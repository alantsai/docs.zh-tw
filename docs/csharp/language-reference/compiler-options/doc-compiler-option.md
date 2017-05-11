---
title: "-doc (C# 編譯器選項) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- FileProperties.BuildAction
- /doc
dev_langs:
- CSharp
helpviewer_keywords:
- comments, C# code
- XML documentation [C#], comments in source files
- doc compiler option [C#]
- Visual C#, XML documentation for
- -doc compiler option [C#]
- /doc compiler option [C#]
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
caps.latest.revision: 19
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
ms.openlocfilehash: 8addbbfe1e854feee560192292b713da4fc67e6c
ms.lasthandoff: 03/13/2017

---
# <a name="doc-c-compiler-options"></a>/doc (C# 編譯器選項)
**/doc** 選項可讓您在 XML 檔案中放入文件註解。  
  
## <a name="syntax"></a>語法  
  
```  
/doc:file  
```  
  
## <a name="arguments"></a>引數  
 `file`  
 XML 的輸出檔，填入編譯原始程式碼檔案中的註解。  
  
## <a name="remarks"></a>備註  
 在原始程式碼檔案中，位在下列內容前面的文件註解，可以處理並新增至 XML 檔案︰  
  
-   這類使用者定義型別，如[類別](../../../csharp/language-reference/keywords/class.md)、[委派](../../../csharp/language-reference/keywords/delegate.md)或[介面](../../../csharp/language-reference/keywords/interface.md)。  
  
-   這類成員如欄位、[事件](../../../csharp/language-reference/keywords/event.md)、[屬性](../../../csharp/programming-guide/classes-and-structs/using-properties.md)或方法。  
  
 包含主要的原始程式碼檔案會先輸出為 XML。  
  
 若要以產生的 .xml 檔案搭配 [IntelliSense](https://docs.microsoft.com/visualstudio/ide/using-intellisense) 功能使用，.xml 檔案的檔案名稱要和您想支援的組件同名，然後確定 .xml 檔案和組件位於相同的目錄。 如此，在 Visual Studio 專案中參考組件時，也會找到 .xml 檔案。 如需詳細資訊，請參閱[提供程式碼註解](https://docs.microsoft.com/visualstudio/ide/supplying-xml-code-comments)。  
  
 除非您使用 [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) 編譯，否則 `file` 會包含 \<assembly>\</assembly> 標記，以便指定包含編譯輸出檔之組建資訊清單的檔案名稱。  
  
> [!NOTE]
>  /doc 選項適用於所有的輸入檔案，或若設定在專案設定中，適用專案的所有檔案。 若要停用與特定檔案或程式碼區段文件註解相關的警告，請使用[#pragma 警告](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)。  
  
 如需從程式碼中的註解產生文件的方式，請參閱[建議使用的文件註解標籤](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 **[屬性]** 頁面。  
  
2.  按一下 **[建置]** 索引標籤。  
  
3.  修改 **XML 文件檔案**屬性。  
  
 如需如何以程式設計方式設定此編譯器選項的資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB 如何：修改專案屬性和組態設定](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
