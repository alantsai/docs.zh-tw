---
title: "如何：在 Windows Form 中列印多頁文字檔 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "列印 [Windows Form], 列印多頁"
  - "列印 [Windows Form], 文字"
  - "文字, 列印 Windows Form"
  - "Windows Form, 列印文字"
ms.assetid: 362427f8-03d4-4826-b49f-60ab066ad322
caps.latest.revision: 24
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# 如何：在 Windows Form 中列印多頁文字檔
Windows 應用程式列印文字的情況極為常見。  <xref:System.Drawing.Graphics> 類別提供將物件 \(圖形或文字\) 繪製到螢幕或印表機等裝置的方法。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer> 的 <xref:System.Windows.Forms.TextRenderer.DrawText%2A> 方法不支援列印。  您應該一律使用 <xref:System.Drawing.Graphics> 的 <xref:System.Drawing.Graphics.DrawString%2A> 方法，來繪製要用於列印的文字，如下列程式碼範例所示：  
  
### 列印文字  
  
1.  將一個 <xref:System.Drawing.Printing.PrintDocument> 元件和一個字串加入您的表單。  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2.  如果是在列印文件，請將 <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> 屬性設定為您想要列印的文件，並且開啟文件內容，讀取到您在之前所加入的字串。  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3.  在 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件處理常式中，使用 <xref:System.Drawing.Printing.PrintPageEventArgs> 類別的 <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> 屬性和文件內容來計算行的長度和每頁的行數。  在繪製每一頁之後，請檢查該頁面是否為最後一頁，並且據此設定 <xref:System.Drawing.Printing.PrintPageEventArgs> 的 <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> 屬性。  在 <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> 成為 `false` 之前會持續引發 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件。  此外，請確定 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件與其事件處理方法相關聯。  
  
     在下列程式碼範例中，會使用事件處理常式以表單上所使用的相同字型來列印 "testPage.txt" 檔案的內容。  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4.  呼叫 <xref:System.Drawing.Printing.PrintDocument.Print%2A> 方法以引發 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件。  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## 範例  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   位於磁碟機 C:\\ 根目錄之名為 testPage.txt 的文字檔，其中包含要列印的文字。  編輯這個程式碼可列印不同的檔案。  
  
-   System、System.Windows.Forms、System.Drawing 組件的參考。  
  
-   如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以透過將程式碼貼入新的專案，在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\))。  
  
## 請參閱  
 <xref:System.Drawing.Graphics>   
 <xref:System.Drawing.Brush>   
 [Windows Form 列印支援](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)