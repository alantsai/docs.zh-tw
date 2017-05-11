---
title: "-checked (C# 編譯器選項) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /checked
dev_langs:
- CSharp
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
caps.latest.revision: 20
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
ms.openlocfilehash: c6cfc54c2dbd3e14d874d7684fdc75a972260cc3
ms.lasthandoff: 03/13/2017

---
# <a name="checked-c-compiler-options"></a>/checked (C# 編譯器選項)
**/checked** 選項會指定產生超出該資料型別範圍之值且不在 [checked](../../../csharp/language-reference/keywords/checked.md) 或 [unchecked](../../../csharp/language-reference/keywords/unchecked.md) 關鍵字範圍內的整數算術陳述式是否導致執行階段例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
/checked[+ | -]  
```  
  
## <a name="remarks"></a>備註  
 在 `checked` 或 `unchecked` 關鍵字範圍內的整數算術陳述式不一定會有 **/checked** 選項的效果。  
  
 如果不在 `checked` 或 `unchecked` 關鍵字範圍內的整數算術陳述式產生超出該資料型別範圍的值，並在編譯時使用 **/checked+** (**/checked**)，則陳述式會在執行階段導致例外狀況。 如果在編譯時使用 **/checked-**，則該陳述式不會在執行階段導致例外狀況。  
  
 這個選項的預設值是 **/checked-**。 使用 **/checked-** 的其中一個案例是建置大型應用程式。 自動化工具有時是用來建置這類應用程式，而且這類工具可能會將 **/checked** 自動設為 +。 您可以指定 **/checked-** 來覆寫工具的全域預設值。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 **[屬性]** 頁面。 如需詳細資訊，請參閱[專案設計工具、建置頁 (C#)](https://docs.microsoft.com/visualstudio/ide/reference/build-page-project-designer-csharp)。  
  
2.  按一下 **[建置]** 屬性頁面。  
  
3.  按一下 **[進階]** 按鈕。  
  
4.  修改 **[檢查算術溢位/反向溢位]** 屬性。  
  
 若要以程式設計方式存取這個編譯器選項，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>。  
  
## <a name="example"></a>範例  
 下列命令會編譯 `t2.cs`。 在命令中使用 `/checked` 會指定檔案中不在 `checked` 或 `unchecked` 關鍵字範圍內且產生超出該資料型別範圍之值的任何整數算術陳述式，都會在執行階段導致例外狀況。  
  
```  
csc t2.cs /checked  
```  
  
## <a name="see-also"></a>另請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB 如何：修改專案屬性和組態設定](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)
