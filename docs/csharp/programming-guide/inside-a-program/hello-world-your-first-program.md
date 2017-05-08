---
title: "Hello World -- 您的第一個程式 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: get-started-article
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
dev_langs:
- CSharp
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
caps.latest.revision: 39
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7ca42afd69e814ce448bfea97c2dbf480830a74a
ms.lasthandoff: 03/13/2017

---
# <a name="hello-world----your-first-program-c-programming-guide"></a>Hello World -- 您的第一個程式 (C# 程式設計手冊)
下列程序會建立 C# 版本的傳統 "Hello World!" 程式。 此程式會顯示字串 `Hello World!`  
  
 如需更多的介紹性概念範例，請參閱 [Visual C# 和 Visual Basic 使用者入門](https://docs.microsoft.com/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)。  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-create-and-run-a-console-application"></a>建立並執行主控台應用程式  
  
1.  啟動 Visual Studio。  
  
2.  在功能表列上，選擇 **[檔案]**、**[新增]**、**[專案]**。  
  
     **[新增專案]** 對話方塊隨即開啟。  
  
3.  依序展開 **[已安裝]**、**[範本]** 和 **[Visual C#]**，然後選擇 **[主控台應用程式]**。  
  
4.  在 **[名稱]** 文字方塊中指定專案名稱，然後選擇 **[確定]** 按鈕。  
  
     新的專案隨即會出現在**方案總管**中。  
  
5.  如果 **[程式碼編輯器]** 中未開啟 Program.cs，請在**方案總管**中開啟 **Program.cs** 的捷徑功能表，然後選擇 **[檢視程式碼]**。  
  
6.  以下列程式碼取代 Program.cs 的內容。  
  
     [!code-cs[csProgGuide#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_1.cs)]  
  
7.  選擇 F5 鍵執行執行專案。 包含 `Hello World!` 一行的命令提示字元視窗隨即出現  
  
 接下來，會檢查此程式的重要部分。  
  
## <a name="comments"></a>註解  
 第一行包含註解。 字元 `//` 會將該行的其餘部分轉換成註解。  
  
 [!code-cs[csProgGuide#32](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_2.cs)]  
  
 您也可以用 `/*` 和 `*/` 字元括住它，註解文字區塊。 這在下列範例中顯示。  
  
 [!code-cs[csProgGuide#33](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_3.cs)]  
  
## <a name="main-method"></a>Main 方法  
 C# 主控台應用程式必須包含 `Main` 方法，控制項在此開始和結束。 `Main` 方法是您建立物件和執行其他方法的所在。  
  
 `Main` 方法是位於類別或結構內的[靜態](../../../csharp/language-reference/keywords/static.md)方法。 在上一個 "Hello World!" 範例中，它位於名為 `Hello` 的類別中。 您可以下列方式之一宣告 `Main` 方法：  
  
-   它會傳回 `void`。  
  
     [!code-cs[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_4.cs)]  
  
-   它也可以傳回整數。  
  
     [!code-cs[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_5.cs)]  
  
-   使用任一傳回型別，它可以接受引數。  
  
     [!code-cs[csProgGuideMain#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_6.cs)]  
  
     -或-  
  
     [!code-cs[csProgGuideMain#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_7.cs)]  
  
 `Main` 方法的參數 `args`，是包含用來叫用程式的命令列引數的 `string` 陣列。 不像在 C++ 中，陣列不包含可執行檔 (exe) 的檔案名稱。  
  
 如需如何使用命令列引數的詳細資訊，請參閱 [Main() 和命令列引數](../../../csharp/programming-guide/main-and-command-args/index.md)以及[如何：使用命令列建立和使用組件](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)。  
  
 按下 F5 在 `Main` 方法的結尾呼叫 <xref:System.Console.ReadKey%2A>，當您在偵錯模式中執行程式時，可防止主控台視窗在您有機會讀取輸出之前關閉。  
  
## <a name="input-and-output"></a>輸入和輸出  
 C# 程式通常會使用 .NET Framework 執行階段程式庫所提供的輸入/輸出服務。 陳述式 `System.Console.WriteLine("Hello World!");` 使用 <xref:System.Console.WriteLine%2A> 方法。 這是執行階段程式庫中 <xref:System.Console> 類別的其中一個輸出方法。 它會在標準輸出資料流中顯示其字串參數，後面接著新行。 其他 <xref:System.Console> 方法可供不同的輸入和輸出作業使用。 如果您在程式開始處包含 `using System;` 指示詞，就可以直接使用 <xref:System> 類別和方法，而不必完整限定它們。 例如，您可以呼叫 `Console.WriteLine` 而不用呼叫 `System.Console.WriteLine`：  
  
 [!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_8.cs)]  
  
 [!code-cs[csProgGuide#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_9.cs)]  
  
 如需輸入/輸出方法的詳細資訊，請參閱 <xref:System.IO>。  
  
## <a name="command-line-compilation-and-execution"></a>命令列編譯和執行  
 您可以編譯 "Hello World!" 程式，使用命令列而不是使用 Visual Studio 整合式開發環境 (IDE)。  
  
#### <a name="to-compile-and-run-from-a-command-prompt"></a>從命令提示字元編譯與執行  
  
1.  將前面程序的程式碼貼入任何文字編輯器，再將檔案儲存為文字檔案。 將檔案命名為 `Hello.cs`。 C# 原始程式碼檔使用延伸模組 `.cs`。  
  
2.  執行下列步驟之一來開啟命令提示字元視窗︰  
  
    -   在 Windows 8 的 **[開始]** 畫面中搜尋 `Developer Command Prompt`，然後點選或選擇 **[適用於 VS2012 的開發人員命令提示字元]**。  
  
         [開發人員命令提示字元] 視窗隨即出現。  
  
    -   開啟 Windows 7 的 **[開始]** 功能表，展開最新版 Visual Studio 的資料夾，開啟 **Visual Studio Tools** 的捷徑功能表，然後選擇 **[適用於 VS2012 的開發人員命令提示字元]**。  
  
         [開發人員命令提示字元] 視窗隨即出現。  
  
    -   從標準的命令提示字元視窗啟用命令列組建。  
  
         請參閱[如何：為 Visual Studio 命令列設定環境變數](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)。  
  
3.  在命令提示字元視窗中，巡覽至包含 `Hello.cs` 檔案的資料夾。  
  
4.  輸入下列命令以編譯 `Hello.cs`。  
  
     `csc Hello.cs`  
  
     如果您的程式沒有任何編譯錯誤，則會建立名為 `Hello.exe` 的可執行檔。  
  
5.  在命令提示字元視窗中輸入下列命令，執行程式：  
  
     `Hello`  
  
 如需 C# 編譯器及其選項的詳細資訊，請參閱[C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)。  
  
## <a name="featured-book-chapter"></a>精選書籍章節  
 [初探 Visual C# 2010](http://go.microsoft.com/fwlink/?LinkId=221214) 中的[撰寫 C# 程式](http://go.microsoft.com/fwlink/?LinkId=221227)  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 程式內部](../../../csharp/programming-guide/inside-a-program/index.md)   
 [字串](../../../csharp/programming-guide/strings/index.md)   
 [\<paveover>C# 範例應用程式](http://msdn.microsoft.com/en-us/9a9d7aaa-51d3-4224-b564-95409b0f3e15)   
 [C# 參考](../../../csharp/language-reference/index.md)   
 [Main() 和命令列引數](../../../csharp/programming-guide/main-and-command-args/index.md)   
 [Visual C# 和 Visual Basic 使用者入門](https://docs.microsoft.com/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
