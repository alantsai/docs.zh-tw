---
title: The .NET Portability Analyzer | .NET
description: "了解如何使用.NET Portability Analyzer 工具來評估程式碼移植到不同.NET 平台之間的可行性。"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 01/23/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
translationtype: Human Translation
ms.sourcegitcommit: 2dcfc9e725a9776e810f23a505e2c6fb157161c4
ms.openlocfilehash: dd14dc23b14e45569f0fdb9a37954b34c4e654d1
ms.lasthandoff: 02/21/2017

---

# <a name="the-net-portability-analyzer"></a>.NET Portability Analyzer

要將您的程式庫變成多平台？ 想要查看花費多少功夫才能讓您的應用程式與其他 .NET 平台相容嗎？ [.NET Portability Analyzer](http://go.microsoft.com/fwlink/?LinkID=507467) 是一項工具，其藉由分析組件來提供您有關程式在跨 .NET 平台上之彈性的詳細報表。 Portability Analyzer 會以 Visual Studio 2015 延伸模組和主控台應用程式的形式提供給您。

## <a name="new-targets"></a>新目標

*   [.NET core](https://www.dotnetfoundation.org/netcore)︰具有模組化的設計，採用並存，並且適合在跨平台的情況下使用。 並存可讓您採用新的 .NET Core 版本，而不會中斷其他應用程式。
*   [ASP.NET Core](https://www.dotnetfoundation.org/aspnet-core)︰是建置於 .NET Core 上的現代 Web 架構，因此提供開發人員相同的優點。
*   [.NET Native](https://blogs.msdn.microsoft.com/dotnet/2014/04/24/net-native-performance)︰改善某些 Windows 市集應用程式的效能，這些應用程式在 x64 和 ARM 電腦上使用 .NET Native 的靜態編譯來執行。

## <a name="how-to-use-portability-analyzer"></a>如何使用 Portability Analyzer

若要開始使用.NET Portability Analyzer，必須從 [Visual Studio 組件庫](http://go.microsoft.com/fwlink/?LinkID=507467) 下載及安裝此延伸模組。 您可以在 Visual Studio 中，使用 [分析] > [Portability Analyzer Settings] (Portability Analyzer 設定) 設定此工具，然後選取您的目標平台。

![可攜性螢幕擷取畫面](./media/portability-analyzer/portability-screenshot.png)

若要分析整個專案，在方案總管中以滑鼠右鍵按一下您的專案，然後選取 [Analyze Assembly Portability] (分析組件可攜性)。 否則，請移至 [分析] 功能表，然後選取 [Analyze Assembly Portability] (分析組件可攜性)。 從這裡選取專案的可執行檔或 DLL。

![可攜性方案總管](./media/portability-analyzer/portability-solution-explorer.png)

執行分析之後，您會看到 .NET Portability 的報表。 僅有目標平台不支援的類型才會顯示在清單中，您可以在 [錯誤清單] 的 [訊息] 索引標籤中檢閱建議。 您也可以直接從 [訊息] 索引標籤跳到有問題的地方。

![可攜性報表](./media/portability-analyzer/portability-report.png)

不想使用 Visual Studio？ 您也可以從命令提示字元使用 Portability Analyzer。 下載 [API Portability Analyzer](http://www.microsoft.com/download/details.aspx?id=42678)。

*   輸入下列命令分析目前的目錄︰`\...\ApiPort.exe analyze -f .`
*   若要分析特定的 .dll 檔案清單，請輸入下列命令︰`\...\ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`

您的 .NET Portability 報表會以 Excel (*.xlsx*) 檔案格式儲存在您目前目錄中。 Excel 活頁簿中的 [詳細資料] 索引標籤會包含更多的資訊。

如需 .NET Portability Analyzer 的詳細資訊，請瀏覽 [GitHub 文件](https://github.com/Microsoft/dotnet-apiport#documentation)和 Channel 9 影片 [Brief Look at the .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) (.NET Portability Analyzer 簡介)。
