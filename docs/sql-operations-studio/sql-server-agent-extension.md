---
title: SQL Operations Studio (プレビュー) の SQL Server Agent 拡張機能 |Microsoft Docs
description: SQL Operations Studio (プレビュー) 用 SQL Server Agent 拡張機能
ms.custom: tools|sos
ms.date: 07/19/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 0da107a9f5dab0a9eb468bc3570788cff816b24a
ms.sourcegitcommit: 4b21840f20195d70f255465666f7b409ba839d18
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39147022"
---
# <a name="sql-server-agent-extension"></a>SQL Server Agent 拡張機能

SQL Server Agent 拡張機能では、管理およびトラブルシューティングの SQL エージェント ジョブと構成の拡張機能です。 この拡張機能は現在プレビュー段階です。

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

## <a name="next-steps"></a>次のステップ

詳細については、SQL Server エージェントは[ドキュメントを確認します。](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent?view=sql-server-2017)


