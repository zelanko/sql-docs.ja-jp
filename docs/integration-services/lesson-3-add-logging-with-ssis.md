---
title: "レッスン 3: SSIS を使用してログ記録を追加する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 64cd24cc-ba8e-4bd7-b10b-6b80d8b04af6
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0bfc02e0c5930fca3dec339274167cbad5716461
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="lesson-3-add-logging-with-ssis"></a>レッスン 3: SSIS でのログ記録の追加
[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] には、パッケージの実行を監視し、問題を解決するためのログ機能があります。このログを使用して、タスクやコンテナー イベントを追跡できます。 柔軟性に優れたこのログ機能では、パッケージごと、またはパッケージ内のタスクやコンテナーごとにログ記録を使用することができます。 ログを記録するイベントを複数選択すると、1 つのパッケージに対して複数のログが作成されます。  
  
ログ記録は、ログ プロバイダーにより供給されます。 ログ プロバイダーごとに、異なる書式、および異なるファイル形式でログ情報を書き分けることができます。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] では、次のログ プロバイダーを使用できます。  
  
-   テキスト ファイル  
  
-   [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]  
  
-   Windows イベント ログ  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   XML ファイル  
  
このレッスンでは、「 [レッスン 2: SSIS でループを追加する](../integration-services/lesson-2-adding-looping-with-ssis.md)」で作成したパッケージのコピーを作成します。 この新しいパッケージを操作しながら、パッケージの実行中に特定のイベントを監視するログ記録を追加し、構成します。 前のレッスンで完了していないものがある場合は、チュートリアルに含まれている、レッスン 2 を完了した状態のパッケージをコピーすることもできます。  
  
> [!IMPORTANT]  
> このチュートリアルには、 **AdventureWorksDW2012** サンプル データベースが必要です。 **AdventureWorksDW2012**, [Reporting Services Product Samples on CodePlex (CodePlex の Reporting Services 製品サンプル)](http://go.microsoft.com/fwlink/p/?LinkID=526910)」を参照してください。  
  
## <a name="lesson-tasks"></a>このレッスンの作業  
このレッスンの内容は次のとおりです。  
  
-   [手順 1: レッスン 2 パッケージのコピー](../integration-services/lesson-3-1-copying-the-lesson-2-package.md)  
  
-   [手順 2: を追加して、ログの構成](../integration-services/lesson-3-2-adding-and-configuring-logging.md)  
  
-   [手順 3: レッスン 3 のチュートリアル パッケージのテスト](../integration-services/lesson-3-3-testing-the-lesson-3-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>レッスンの開始  
[手順 1: レッスン 2 パッケージのコピー](../integration-services/lesson-3-1-copying-the-lesson-2-package.md)  
  
  
  

