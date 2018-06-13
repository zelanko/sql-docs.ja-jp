---
title: Insight ウィジェットを使用して、サーバーと SQL Operations Studio (プレビュー) でデータベースを監視する |Microsoft ドキュメント
description: SQL Operations Studio (プレビュー) で洞察ウィジェットについて説明します。
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql
ms.reviewer: alayu; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: article"
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 77f34ceebb4f02c829b2df3efcae5e64c2eaa1bf
ms.sourcegitcommit: 6fd8a193728abc0a00075f3e4766a7e2e2859139
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34235931"
---
# <a name="manage-servers-and-databases-with-insight-widgets-in-includename-sosincludesname-sos-shortmd"></a>サーバーとの洞察ウィジェットを持つデータベースを管理します。 [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Insight ウィジェットがサーバーとデータベースの監視に使用する TRANSACT-SQL (T-SQL) クエリを実行し、洞察の視覚エフェクトに変えます。 

洞察は、カスタマイズ可能なグラフおよびサーバーとデータベースの監視ダッシュ ボードに追加するグラフです。 サーバーおよびデータベースの概要の洞察を表示し、詳細については、ドリルを定義する管理操作を起動します。 

優れたサーバーおよびデータベース管理ダッシュ ボードに次の例と同様にビルドするには。

![データベース ダッシュ ボード](media/insight-widgets/database-dashboard.png)


操作を開始し、洞察のウィジェットのさまざまな種類の作成を開始には、次のチュートリアルを確認します。

- [カスタム インサイト ウィジェットをビルドします。](tutorial-build-custom-insight-sql-server.md)
- *組み込みの洞察ウィジェットを有効にします。*
   - [パフォーマンス監視のインサイトを有効にします。](tutorial-qds-sql-server.md)
   - [テーブル領域使用状況情報を得ることを有効にします。](tutorial-table-space-sql-server.md)


## <a name="sql-queries"></a>SQL クエリ 

[!INCLUDE[name-sos](../includes/name-sos-short.md)] 別の言語または高負荷のユーザー インターフェイスの JSON の最小構成でできるだけ多く T-SQL を使用するようにまだを行わずに済みますしようとしています。 T-SQL で洞察ウィジェットを構成するには、洞察に富んだウィジェットに変換できる便利なの T-SQL クエリの既存のソースの膨大な数は活用します。

Insight ウィジェットは、1 つまたは 2 つの T-SQL クエリから構成されます。
* *Insight ウィジェットのクエリ*必須であり、ウィジェットで表示されるデータを返すクエリです。
* *情報の詳細クエリ*はインサイトの詳細 ページを作成するかどうかにのみ必要です。

Insight ウィジェットのクエリでは、数、グラフ、またはグラフを表示するデータセットを定義します。 インサイトの詳細のクエリを使用すると、洞察の詳細 パネルで、表形式で関連するインサイトの詳細情報を一覧表示されます。 

[!INCLUDE[name-sos](../includes/name-sos-short.md)] insight ウィジェットのクエリを実行し、グラフのデータセットにクエリの結果セットをマップし、それを表示します。 ユーザー情報の詳細を開くと、insight 詳細クエリが実行され、ダイアログ ボックス内のグリッド ビューで、結果を出力します。

基本的な概念では、T-SQL クエリを記述する方法の数、グラフ、およびグラフ ウィジェットのデータセットとして使用できるようにします。 

## <a name="summary"></a>[概要]

T-SQL クエリされ、結果セットは、洞察ウィジェットの動作を決定します。 グラフの種類のクエリの記述や、既存のクエリの右側のグラフの種類のマッピングは、効果的な洞察ウィジェットを構築する主要な考慮事項です。



## <a name="additional-resources"></a>その他のリソース
- [クエリ エディター](tutorial-sql-editor.md)

