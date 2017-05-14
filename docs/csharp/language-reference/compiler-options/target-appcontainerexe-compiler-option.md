---
title: "-target:appcontainerexe (C# 編譯器選項) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 168771506692308bc9b031df5c059e58e8d190b1
ms.lasthandoff: 03/13/2017

---
# <a name="targetappcontainerexe-c-compiler-options"></a>/target:appcontainerexe (C# 編譯器選項)
如果您使用 **/target:appcontainerexe** 編譯器選項，編譯器會建立一個必須在應用程式容器中執行的 Windows 可執行檔 (.exe)。 這個選項相當於 [/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)，但是專為 [!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)] 應用程式所設計。  
  
## <a name="syntax"></a>語法  
  
```  
/target:appcontainerexe  
```  
  
## <a name="remarks"></a>備註  
 這個選項會在 [Portable Executable](http://go.microsoft.com/fwlink/p/?LinkId=236960) (可攜式執行檔) (PE) 中設定一個位元，以要求應用程式在應用程式容器中執行。 當這個位元設定時，如果 CreateProcess 方法嘗試在應用程式容器之外啟動可執行檔，則會發生錯誤。  
  
 除非您使用 [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) 選項指定輸出檔名稱，否則輸出檔名稱會採用包含 [Main](../../../csharp/programming-guide/main-and-command-args/index.md) 方法的輸入檔名稱。  
  
 如果您在命令提示字元指定這個選項，下一個 **/out** 或 **/target** 選項之前的所有檔案都是用來建立可執行檔。  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a>若要在 IDE 中設定這個編譯器選項  
  
1.  在**方案總管**中，開啟專案的捷徑功能表，然後選擇 **[屬性]**。  
  
2.  在 **[應用程式]** 索引標籤上，選擇 **[輸出類型]** 清單中的 **[Windows 市集應用程式]**。  
  
     這個選項只適用於 [!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)]應用程式範本。  
  
 如需如何以程式設計方式設定此編譯器選項的資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。  
  
## <a name="example"></a>範例  
 下列命令會將 `filename.cs` 編譯至一個只能在應用程式容器中執行的 Windows 可執行檔。  
  
```  
csc /target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a>另請參閱  
 [/target (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [/target:winexe (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)   
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)
