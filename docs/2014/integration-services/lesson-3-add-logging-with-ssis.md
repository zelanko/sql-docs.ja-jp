---
title: 'レッスン 3: ログ機能の追加 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 64cd24cc-ba8e-4bd7-b10b-6b80d8b04af6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7dc2b824ef3fb3b1809bf685b3b5b8409ca1f805
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48196922"
---
# <a name="lesson-3-adding-logging"></a>レッスン 3 : ログ機能の追加
  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] には、パッケージの実行を監視し、問題を解決するためのログ機能があります。このログを使用して、タスクやコンテナー イベントを追跡できます。 柔軟性に優れたこのログ機能では、パッケージごと、またはパッケージ内のタスクやコンテナーごとにログ記録を使用することができます。 ログを記録するイベントを複数選択すると、1 つのパッケージに対して複数のログが作成されます。  
  
 ログ記録は、ログ プロバイダーにより供給されます。 ログ プロバイダーごとに、異なる書式、および異なるファイル形式でログ情報を書き分けることができます。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] では、次のログ プロバイダーを使用できます。  
  
-   テキスト ファイル  
  
-   [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]  
  
-   Windows イベント ログ  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   XML ファイル  
  
 このレッスンで作成したパッケージのコピーを作成します[レッスン 2: ループを追加する](lesson-2-adding-looping-with-ssis.md)します。 この新しいパッケージを操作しながら、パッケージの実行中に特定のイベントを監視するログ記録を追加し、構成します。 前のレッスンで完了していないものがある場合は、チュートリアルに含まれている、レッスン 2 を完了した状態のパッケージをコピーすることもできます。  
  
> [!IMPORTANT]  
>  このチュートリアルには、 **AdventureWorksDW2012** サンプル データベースが必要です。 インストールおよび展開方法の詳細について**AdventureWorksDW2012**、 [CodePlex の Reporting Services Product Samples](http://go.microsoft.com/fwlink/p/?LinkID=52691)します。  
  
## <a name="lesson-tasks"></a>このレッスンの作業  
 このレッスンの内容は次のとおりです。  
  
-   [手順 1: レッスン 2 のパッケージのコピー](lesson-3-1-copying-the-lesson-2-package.md)  
  
-   [手順 2: ログ機能の追加と設定](lesson-3-2-adding-and-configuring-logging.md)  
  
-   [手順 3: レッスン 3 のチュートリアル パッケージのテスト](../integration-services/lesson-3-3-testing-the-lesson-3-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>レッスンの開始  
 [手順 1: レッスン 2 のパッケージのコピー](lesson-3-1-copying-the-lesson-2-package.md)  
  
  
