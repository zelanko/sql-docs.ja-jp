---
title: Insight ウィジェットを使用して、サーバーと SQL Operations Studio (プレビュー) でデータベースを監視する |Microsoft ドキュメント
description: SQL Operations Studio (プレビュー) で洞察ウィジェットについて説明します。
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql
ms.technology: ssops
ms.reviewer: alayu; sstein
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 79918d899fa978404dde63bf9257ffb9fc52d185
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39082854"
---
# <a name="manage-servers-and-databases-with-insight-widgets-in-includename-sosincludesname-sos-shortmd"></a>サーバーとの洞察のウィジェットでのデータベースを管理します。 [!INCLUDE[name-sos](../includes/name-sos-short.md)]

洞察のウィジェットは、サーバーとデータベースの監視に使用する TRANSACT-SQL (T-SQL) クエリを実行し、洞察に満ちた視覚エフェクトに変換します。 

インサイトは、カスタマイズ可能なチャートやグラフ サーバーとデータベースの監視ダッシュ ボードに追加するには。 サーバーをデータベースの概要の詳細情報の表示し、詳細については、ドリルダウンを定義する管理アクションを起動します。 

すばらしいサーバーおよびデータベース管理ダッシュ ボード例を次のようなをビルドすることができます。

![データベース ダッシュ ボード](media/insight-widgets/database-dashboard.png)


移動し、洞察のウィジェットのさまざまな種類の作成を開始には、次のチュートリアルをご覧ください。

- [カスタム インサイト ウィジェットをビルドします。](tutorial-build-custom-insight-sql-server.md)
- *組み込みの洞察のウィジェットを有効にします。*
   - [パフォーマンスの洞察の監視を有効にします。](tutorial-qds-sql-server.md)
   - [テーブル領域使用状況の分析情報を有効にします。](tutorial-table-space-sql-server.md)


## <a name="sql-queries"></a>SQL クエリ 

[!INCLUDE[name-sos](../includes/name-sos-short.md)] まだ他の言語や複雑なユーザー インターフェイスの最小限の JSON 構成で可能な限り T-SQL を使用するための概要を回避しようとしています。 T-SQL で洞察のウィジェットを構成するには、洞察に富むウィジェットに変換できる便利な T-SQL クエリの既存のソースの数を数えきれないほどが利用しています。

洞察のウィジェットは、1 つまたは 2 つの T-SQL クエリから構成されます。
* *洞察のウィジェットのクエリ*をウィジェットに表示されるデータを返すクエリでありは必須です。
* *インサイトの詳細のクエリ*がインサイトの詳細ページを作成するかどうかにのみ必要です。

Insight ウィジェットのクエリは、数、グラフ、またはグラフを表示するデータセットを定義します。 インサイトの詳細のクエリは、インサイトの詳細 パネルで表形式で関連する分析情報の詳細情報を一覧表示に使用されます。 

[!INCLUDE[name-sos](../includes/name-sos-short.md)] 洞察のウィジェットのクエリを実行します、グラフのデータセットにクエリの結果セットをマップし、それをレンダリングします。 ユーザー分析情報の詳細を開くと、インサイトの詳細のクエリが実行され、ダイアログ ボックスで、グリッド ビューに結果を出力します。

基本的な考え方では、数、グラフ、およびグラフ ウィジェットのデータセットとして使用できるように、方法で T-SQL クエリを作成します。 

## <a name="summary"></a>[概要]

T-SQL クエリとその結果セットは、洞察のウィジェットの動作を決定します。 グラフの種類のクエリを作成または既存のクエリの右側のグラフの種類のマッピングは、効果的な洞察のウィジェットを構築する重要な考慮事項です。



## <a name="additional-resources"></a>その他のリソース
- [クエリ エディター](tutorial-sql-editor.md)

