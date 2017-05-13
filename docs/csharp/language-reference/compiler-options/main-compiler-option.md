---
title: "-main (C# 編譯器選項) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /main
dev_langs:
- CSharp
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
caps.latest.revision: 14
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
ms.openlocfilehash: fa8c02a6521b65e2cc4f7c8d779c1091ce399fba
ms.lasthandoff: 03/13/2017

---
# <a name="main-c-compiler-options"></a>/main (C# 編譯器選項)
如果有多個類別包含 **Main** 方法，這個選項會指定含有程式進入點的類別。  
  
## <a name="syntax"></a>語法  
  
```  
/main:class  
```  
  
## <a name="arguments"></a>引數  
 `class`  
 含有 **Main** 方法的類型。  
  
## <a name="remarks"></a>備註  
 如果編譯的 [Main](../../../csharp/programming-guide/main-and-command-args/index.md) 方法中包含一個以上的型別，您可以指定哪個型別含有要作為程式進入點的 **Main** 方法。  
  
 在編譯 .exe 檔案時，即可使用此選項。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 **[屬性]** 頁面。  
  
2.  按一下 **[應用程式]** 屬性頁。  
  
3.  修改 **[啟始物件]** 屬性。  
  
     若要以程式設計方式設定此編譯器選項，請參閱 <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>。  
  
## <a name="example"></a>範例  
 編譯 `t2.cs` 和 `t3.cs`，將 **Main** 方法的位置指定在 `Test2` 中：  
  
```  
csc t2.cs t3.cs /main:Test2  
```  
  
## <a name="see-also"></a>另請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB 如何：修改專案屬性和組態設定](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
