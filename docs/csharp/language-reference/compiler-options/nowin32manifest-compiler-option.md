---
title: "-nowin32manifest (C# 編譯器選項) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /nowin32manifest
dev_langs:
- CSharp
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
caps.latest.revision: 15
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
ms.openlocfilehash: ce96938ee00df7bfae742369673f75f8d39abd12
ms.lasthandoff: 03/13/2017

---
# <a name="nowin32manifest-c-compiler-options"></a>/nowin32manifest (C# 編譯器選項)
使用 **[/nowin32manifest]** 選項指示編譯器不要將任何應用程式資訊清單內嵌在可執行檔中。  
  
## <a name="syntax"></a>語法  
  
```  
/nowin32manifest  
```  
  
## <a name="remarks"></a>備註  
 使用此選項時，應用程式在 Windows Vista 上會虛擬化，除非您在 Win32 資源檔案中或於更新版本組建步驟期間提供應用程式資訊清單。  
  
 在 Visual Studio 中，選取 **[資訊清單]** 下拉式清單的 **[建立無資訊清單應用程式]** 選項，在 **[Application Property] (應用程式屬性)** 頁面中設定這個選項。 如需詳細資訊，請參閱[專案設計工具、應用程式頁 (C#)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-csharp)。  
  
 如需建立資訊清單的詳細資訊，請參閱[/win32manifest (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md)。  
  
## <a name="see-also"></a>另請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB 如何：修改專案屬性和組態設定](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
