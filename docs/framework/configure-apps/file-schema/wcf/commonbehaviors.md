---
title: "&lt;commonBehaviors&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;commonBehaviors&gt;
`commonBehaviors` 區段只能定義在 machine.config 檔中。  它會定義兩個名為 `endpointBehaviors` 和 `serviceBehaviors` 的子集合。  每個集合會分別定義由所有 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 端點和電腦上服務所使用的行為項目。  在 `endpointBehaviors` 中定義的行為只會套用至用戶端，在 `serviceBehaviors` 中定義的行為只會套用至服務。  如果 `commonBehaviors` 和 `behaviors` 區段中都有定義某個行為，則會優先使用 `behaviors` 區段中的行為。