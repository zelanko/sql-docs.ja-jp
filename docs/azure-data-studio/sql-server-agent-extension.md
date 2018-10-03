---
title: Azure データ Studio の SQL Server Agent 拡張機能 |Microsoft Docs
description: Azure Data Studio 用 SQL Server エージェント拡張機能 (プレビュー)
ms.custom: tools|sos
ms.date: 09/24/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.prod_service: sql-tools
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 5804aa146ddf79f6c3c4ccba48edd86d297c5c72
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "48039204"
---
# <a name="sql-server-agent-extension-preview"></a>SQL Server エージェントの拡張機能 (プレビュー)

SQL Server エージェントの拡張機能 (プレビュー) では、管理およびトラブルシューティングの SQL エージェント ジョブと構成の拡張機能です。 この拡張機能は現在プレビュー段階です。

主なアクションは次のとおりです。
- リスト SQL Server エージェント ジョブの SQL Server で構成されています。
- ジョブの実行結果とジョブ履歴の表示
- 開始およびジョブを停止する基本的なジョブ制御

## <a name="install-the-sql-server-agent-extension"></a>SQL Server エージェントの拡張機能をインストールします。

1. 拡張機能マネージャーを開き、使用可能な拡張機能にアクセスするには、拡張機能 アイコンを選択するか、**ビュー**メニューの**拡張**を選択します。
2. 使用可能な拡張機能を選択して詳細を表示します。

   ![エージェントをインストールします。](media/extensions/sql-server-agent-extension/install-sql-agent.png)

1. 必要な拡張機能を選択し、**インストール**します。
2. **再読み込み**を選択して拡張機能を有効にします(初めて拡張機能をインストールするときのみ必要です)。
1. サーバーまたはデータベースを右クリックし、**管理**を選択して管理ダッシュ ボードに移動します。
2. インストールされた拡張機能は、管理ダッシュ ボードのタブとして表示されます。

   ![エージェントのビュー](media/extensions/sql-server-agent-extension/view-sql-agent.png)

## <a name="view-jobs"></a>ジョブの表示

SQL Server エージェントの拡張機能に接続するときに、最初に表示はすべてのエージェント ジョブの一覧を示します。

   ![ジョブの表示](media/extensions/sql-server-agent-extension/job-view.png)

## <a name="next-steps"></a>次の手順

詳細については、SQL Server エージェントは[ドキュメントを確認します。](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent?view=sql-server-2017)


