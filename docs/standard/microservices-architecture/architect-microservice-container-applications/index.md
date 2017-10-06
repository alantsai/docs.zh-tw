---
title: "架構容器和微服務應用程式"
description: "容器化 .NET 應用程式的 .NET 微服務架構 | 架構容器和微服務應用程式"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.translationtype: HT
ms.sourcegitcommit: 9bb64ea7199f5699ff166d1affb7f8126dcc6612
ms.openlocfilehash: 360b4745e768a751154f3f1445ffb0bf5b62c825
ms.contentlocale: zh-tw
ms.lasthandoff: 09/05/2017

---
# <a name="architecting-container--and-microservice-based-applications"></a>架構容器和微服務應用程式

*Microservices 提供極大的好處，但也會引發龐大的新挑戰。當建立微服務應用程式時，會以微服務架構模式為基礎。*

稍早在本指南中，您了解有關容器和 Docker 的基本概念。 這是您開始使用容器所需的基本資訊。 雖然容器是啟用程式且非常適合微服務，但對微服務架構而言絕非必要，而且本架構章節中的許多架構概念在沒有容器的情況下也適用。 不過，由於已介紹過容器的重要性，因此本指南會將重點放在這兩者的交集。

企業應用程式可能很複雜，而且通常是由多個服務而不是單一服務應用程式所組成。 針對這些案例，您必須了解其他架構方法，例如微服務和特定領域驅動設計 (Domain-Driven Design，DDD) 模式，以及容器協調流程概念。 請注意，本章不只描述容器上的微服務，也描述任何容器化應用程式。

## <a name="container-design-principles"></a>容器設計原則

在容器模型中，容器映像執行個體代表單一處理序。 藉由將容器映像定義為處理序邊界，您可以建立基本類型，以便用來調整處理序或對它進行批次處理。

當您設計容器映像時，您會在 Dockerfile 中看到 [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/) 定義。 這會定義處理序，其存留期間可控制容器的存留期。 當處理序完成時，容器生命週期即告結束。 容器可能代表長時間執行的處理序 (例如網頁伺服器)，但也可能代表短期處理序 (例如之前可能已實作為 Azure [WebJobs](https://docs.microsoft.com/azure/app-service-web/websites-webjobs-resources) 的批次工作)。

如果處理序失敗，容器會結束並由 Orchestrator 接管。 如果 Orchestrator 已設定為保留五個執行中的執行個體，且其中一個失敗，Orchestrator 將會建立另一個容器執行個體，來取代失敗的處理序。 在批次工作中，處理序是透過參數來啟動。 當處理序完成時，工作即告完成。

您可能發現有時需要在單一容器中執行多個處理序。 在此情況下，由於每個容器只能有一個進入點，因此您可以在容器中執行指令碼來視需要啟動許多程式。 例如，您可以使用 [Supervisor](http://supervisord.org/) 或類似工具，在單一容器中啟動多個處理序。 不過，即使您可能發現在每個容器中保留多個處理序的架構，但該方法並不常見。


>[!div class="step-by-step"]
[上一個] (../net-core-net-framework-containers/official-net-docker-images.md) [下一個] (containerize-monolithic-applications.md)
