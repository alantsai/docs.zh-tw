---
title: "由於內部錯誤，無法取得記憶體資訊 | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrDiagnosticInfo_Memory"
ms.assetid: 1ba8f774-5858-438e-914e-99fddc9e5e7e
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# 由於內部錯誤，無法取得記憶體資訊
呼叫 `My.Computer.Info` 物件的其中一個記憶體資訊屬性失敗。  
  
### 更正這個錯誤  
  
-   在 `My.Computer.Info` 物件之記憶體資訊屬性的呼叫周圍加入 `Try...Catch` 區塊。  
  
## 請參閱  
 [My.Computer.Info Object](../../visual-basic/language-reference/objects/my-computer-info-object.md)   
 [Visual Basic 中的例外狀況和錯誤處理](http://msdn.microsoft.com/zh-tw/3e351e73-cf23-40ab-8b60-05794160529e)   
 [Try...Catch...Finally Statement](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)