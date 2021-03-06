---
title: "FILESTREAM 資料 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# FILESTREAM 資料
FILESTREAM 儲存體屬性適用於儲存在 varbinary\(max\) 資料行中的二進位 \(BLOB\) 資料。  在引進 FILESTREAM 之前，儲存二進位資料需要特殊處理。  文字文件、影像和視訊等非結構化資料通常會儲存在資料庫外部，因而難以管理。  
  
> [!NOTE]
>  您必須安裝 .NET Framework 3.5 SP1 \(或更新版本\) 才能使用 SqlClient 來處理 FILESTREAM 資料。  
  
 針對 varbinary\(max\) 資料行指定 FILESTREAM 屬性會導致 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 將資料儲存在本機 NTFS 檔案系統上，而非資料庫檔案中。  雖然系統會以不同的方式儲存資料，但是您仍可使用支援搭配儲存在資料庫中之 varbinary\(max\) 資料的相同 [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] 陳述式 \(Statement\)。  
  
## FILESTREAM 的 SqlClient 支援  
 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Data Provider for [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] \(<xref:System.Data.SqlClient>\) 支援使用 <xref:System.Data.SqlTypes> 命名空間中定義的 <xref:System.Data.SqlTypes.SqlFileStream> 類別來讀取和寫入 FILESTREAM 資料。  `SqlFileStream` 繼承自 <xref:System.IO.Stream> 類別，可提供讀取和寫入資料流的方法。  讀取資料流會將資料從資料流傳送至資料結構中，例如位元組的陣列。  寫入則會將資料從資料結構傳送至資料流中。  
  
### 建立 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 資料表  
 下列 [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] 陳述式會建立名為 employees 的資料表並插入一個資料列。  一旦您啟用了 FILESTREAM 儲存體之後，就可以使用這份資料表搭配後面的程式碼範例。  《[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 線上叢書》中的資源連結位於本主題的結尾。  
  
```  
CREATE TABLE employees  
(  
  EmployeeId INT  NOT NULL  PRIMARY KEY,  
  Photo VARBINARY(MAX) FILESTREAM  NULL,  
  RowGuid UNIQUEIDENTIFIER  NOT NULL  ROWGUIDCOL  
  UNIQUE DEFAULT NEWID()  
)  
GO  
Insert into employees  
Values(1, 0x00, default)  
GO  
  
```  
  
### 範例：讀取、覆寫和插入 FILESTREAM 資料  
 下列範例將示範如何從 FILESTREAM 中讀取資料。  這段程式碼會取得檔案的邏輯路徑，並將 `FileAccess` 設定為 `Read` 而且將 `FileOptions` 設定為 `SequentialScan`。  然後，程式碼會將位元組從 SqlFileStream 讀入緩衝區中。  接著，這些位元組會寫入主控台視窗。  
  
 範例也會示範如何將資料寫入會覆寫所有現有資料的 FILESTREAM 中。  這段程式碼會取得檔案的邏輯路徑並建立 `SqlFileStream`，並將 `FileAccess` 設定為 `Write` 而且將 `FileOptions` 設定為 `SequentialScan`。  然後，單一位元組會寫入 `SqlFileStream`，並取代檔案中的任何資料。  
  
 範例也會示範如何使用 Seek 方法來附加資料至檔案的結尾，藉以將資料寫入 FILESTREAM。  這段程式碼會取得檔案的邏輯路徑並建立 `SqlFileStream`，並將 `FileAccess` 設定為 `ReadWrite` 而且將 `FileOptions` 設定為 `SequentialScan`。  然後，程式碼會使用 Seek 方法來搜尋至檔案的結尾，並將單一位元組附加至現有的檔案。  
  
```csharp  
using System;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Data;  
using System.IO;  
  
namespace FileStreamTest  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder("server=(local);integrated security=true;database=myDB");  
            ReadFilestream(builder);  
            OverwriteFilestream(builder);  
            InsertFilestream(builder);  
  
            Console.WriteLine("Done");  
        }  
  
        private static void ReadFilestream(SqlConnectionStringBuilder connStringBuilder)  
        {  
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))  
            {  
                connection.Open();  
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);  
  
                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);  
                command.Transaction = tran;  
  
                using (SqlDataReader reader = command.ExecuteReader())  
                {  
                    while (reader.Read())  
                    {  
                        // Get the pointer for the file  
                        string path = reader.GetString(0);  
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
                        // Create the SqlFileStream  
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Read, FileOptions.SequentialScan, allocationSize: 0))  
                        {  
                            // Read the contents as bytes and write them to the console  
                            for (long index = 0; index < fileStream.Length; index++)  
                            {  
                                Console.WriteLine(fileStream.ReadByte());  
                            }  
                        }  
                    }  
                }  
                tran.Commit();  
            }  
        }  
  
        private static void OverwriteFilestream(SqlConnectionStringBuilder connStringBuilder)  
        {  
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))  
            {  
                connection.Open();  
  
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);  
  
                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);  
                command.Transaction = tran;  
  
                using (SqlDataReader reader = command.ExecuteReader())  
                {  
                    while (reader.Read())  
                    {  
                        // Get the pointer for file   
                        string path = reader.GetString(0);  
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
                        // Create the SqlFileStream  
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Write, FileOptions.SequentialScan, allocationSize: 0))  
                        {  
                            // Write a single byte to the file. This will  
                            // replace any data in the file.  
                            fileStream.WriteByte(0x01);  
                        }  
                    }  
                }  
                tran.Commit();  
            }  
        }  
  
        private static void InsertFilestream(SqlConnectionStringBuilder connStringBuilder)  
        {  
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))  
            {  
                connection.Open();  
  
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);  
  
                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);  
                command.Transaction = tran;  
  
                using (SqlDataReader reader = command.ExecuteReader())  
                {  
                    while (reader.Read())  
                    {  
                        // Get the pointer for file  
                        string path = reader.GetString(0);  
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Write, FileOptions.SequentialScan, allocationSize: 0))  
                        {  
                            // Seek to the end of the file  
                            fileStream.Seek(0, SeekOrigin.End);  
  
                            // Append a single byte   
                            fileStream.WriteByte(0x01);  
                        }  
                    }  
                }  
                tran.Commit();  
            }  
  
        }  
    }  
} using (SqlConnection connection = new SqlConnection(  
    connStringBuilder.ToString()))  
{  
    connection.Open();  
  
    SqlCommand command = new SqlCommand("", connection);  
    command.CommandText = "select Top(1) Photo.PathName(), "  
    + "GET_FILESTREAM_TRANSACTION_CONTEXT () from employees";  
  
    SqlTransaction tran = connection.BeginTransaction(  
        System.Data.IsolationLevel.ReadCommitted);  
    command.Transaction = tran;  
  
    using (SqlDataReader reader = command.ExecuteReader())  
    {  
        while (reader.Read())  
        {  
            // Get the pointer for file  
            string path = reader.GetString(0);  
            byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
            FileStream fileStream = new SqlFileStream(path,  
                (byte[])reader.GetValue(1),  
                FileAccess.ReadWrite,  
                FileOptions.SequentialScan, 0);  
  
            // Seek to the end of the file  
            fs.Seek(0, SeekOrigin.End);  
  
            // Append a single byte   
            fileStream.WriteByte(0x01);  
            fileStream.Close();  
        }  
    }  
    tran.Commit();  
}  
```  
  
 如需其他範例，請參閱[如何儲存二進位資料並將其擷取至檔案資料流資料行](http://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str)。  
  
## 《[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 線上叢書》中的資源  
 FILESTREAM 的完整文件位於《[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 線上叢書》中的下列章節。  
  
|主題|描述|  
|--------|--------|  
|[設計和實作 FILESTREAM 儲存體](http://msdn2.microsoft.com/library/bb895234\(SQL.105\).aspx)|提供 FILESTREAM 文件和相關主題的連結。|  
|[FILESTREAM 概觀](http://msdn2.microsoft.com/library/bb933993\(SQL.105\).aspx)|描述使用 FILESTREAM 儲存體的時機，以及它如何整合 SQL Server Database Engine 與 NTFS 檔案系統。|  
|[FILESTREAM 儲存體使用者入門](http://msdn.microsoft.com/library/bb933995\(SQL.105\).aspx)|描述如何在 SQL Server 執行個體 \(Instance\) 上啟用 FILESTREAM、如何建立資料庫和資料表來儲存 FILESTREAM 資料，以及如何管理包含 FILESTREAM 資料的資料列。|  
|[在用戶端應用程式中使用 FILESTREAM 儲存體](http://msdn.microsoft.com/library/bb933877\(SQL.105\).aspx)|描述可用於處理 FILESTREAM 資料的 Win32 API 函式。|  
|[使用 FILESTREAM 搭配其他 SQL Server 功能](http://msdn.microsoft.com/library/bb895334\(SQL.105\).aspx)|針對使用 FILESTREAM 資料搭配其他 SQL Server 功能提供相關的考量、指導方針和限制。|  
  
## 請參閱  
 [SQL Server 資料型別和 ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)   
 [擷取和修改 ADO.NET 中的資料](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [程式碼存取安全性和 ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md)   
 [SQL Server 二進位和大數值資料](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)