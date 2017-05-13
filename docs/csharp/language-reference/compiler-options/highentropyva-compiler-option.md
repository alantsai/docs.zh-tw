---
title: "-highentropyva (C# 編譯器選項) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /highentropyva
dev_langs:
- CSharp
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
caps.latest.revision: 8
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
ms.openlocfilehash: c1b49faa2fb388b330c24bdff28d00872828b110
ms.lasthandoff: 03/13/2017

---
# <a name="highentropyva-c-compiler-options"></a>/highentropyva (C# 編譯器選項)
**[/highentropyva]** 編譯器選項會通知 Windows 核心某一特定可執行檔是否支援高熵位址空間配置隨機載入 (ASLR)。  
  
## <a name="syntax"></a>語法  
  
```  
/highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>引數  
 `+` &#124; `-`  
 此選項會指定，64 位元可執行檔或 [/platform:anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) 編譯器選項所標記的可執行檔支援高熵虛擬位址空間。 此選項預設為停用。 使用 **[/highentropyva+]** 或 **[/highentropyva]** 予以啟用。  
  
## <a name="remarks"></a>備註  
 當隨機化處理序的位址空間配置作為 ASLR 一部分時，**[/highentropyva]** 選項可讓相容的 Windows 核心版本使用較高程度的高熵。 使用較高程度的高熵表示可將大量位址配置到記憶體區域，例如堆疊和堆積， 因此更難猜測特定記憶體區域的位置。  
  
 指定 **[/highentropyva]** 編譯器選項時，目標可執行檔以及作為其依據的任何模組在作為 64 位元處理序執行時，都必須能夠處理大於 4 GB 的指標值。
