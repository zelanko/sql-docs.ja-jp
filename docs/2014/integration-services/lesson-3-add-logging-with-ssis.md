---
title: 'レッスン 3: ログ記録の追加 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 64cd24cc-ba8e-4bd7-b10b-6b80d8b04af6
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e716b808d5d9ada8aeaf50d92006cc6453c6e47d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67046764"
---
# <a name="lesson-3-adding-logging"></a>レッスン 3 : ログ機能の追加
  [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]には、タスクとコンテナーイベントのトレースを提供することによって、パッケージの実行をトラブルシューティングおよび監視するためのログ機能が含まれています。 柔軟性に優れたこのログ機能では、パッケージごと、またはパッケージ内のタスクやコンテナーごとにログ記録を使用することができます。 ログを記録するイベントを複数選択すると、1 つのパッケージに対して複数のログが作成されます。  
  
 ログ記録は、ログ プロバイダーにより供給されます。 ログ プロバイダーごとに、異なる書式、および異なるファイル形式でログ情報を書き分けることができます。 
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] では、次のログ プロバイダーを使用できます。  
  
-   テキスト ファイル  
  
-   [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]  
  
-   Windows イベント ログ  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   XML ファイル  
  
 このレッスンでは、 [「レッスン 2: ループの追加](lesson-2-adding-looping-with-ssis.md)」で作成したパッケージのコピーを作成します。 この新しいパッケージを操作しながら、パッケージの実行中に特定のイベントを監視するログ記録を追加し、構成します。 前のレッスンで完了していないものがある場合は、チュートリアルに含まれている、レッスン 2 を完了した状態のパッケージをコピーすることもできます。  
  
> [!IMPORTANT]  
>  このチュートリアルには、 **AdventureWorksDW2012** サンプル データベースが必要です。 **AdventureWorksDW2012**をインストールしてデプロイする方法の詳細については、 [GitHub で Reporting Services 製品サンプル](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)を参照してください。  
  
## <a name="lesson-tasks"></a>このレッスンの作業  
 このレッスンの内容は次のとおりです。  
  
-   [手順 1: レッスン 2 のパッケージのコピー](lesson-3-1-copying-the-lesson-2-package.md)  
  
-   [手順 2:ログ機能の追加と設定](lesson-3-2-adding-and-configuring-logging.md)  
  
-   [手順 3: レッスン 3 のチュートリアル パッケージのテスト](../integration-services/lesson-3-3-testing-the-lesson-3-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>レッスンの開始  
 [手順 1: レッスン 2 のパッケージのコピー](lesson-3-1-copying-the-lesson-2-package.md)  
  
  
