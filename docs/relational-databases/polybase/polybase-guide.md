---
title: PolyBase ガイド | Microsoft Docs
ms.date: 05/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: polybase
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: database
ms.tgt_pltfrm: ''
ms.topic: get-started-article
f1_keywords:
- PolyBase
- PolyBase, guide
helpviewer_keywords:
- PolyBase
- PolyBase, overview
- Hadoop import ×
- Hadoop export
- Hadoop export, PolyBase overview
- Hadoop import, PolyBase overview
caps.latest.revision: 26
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 24ddcaa7ea682b0afb5f76f6d45ca89b9bbd1896
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="polybase-guide"></a>PolyBase ガイド
[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]
  PolyBase は、t-sql 言語を使ってデータベースの外部にあるデータにアクセスするテクノロジです。  SQL Server 2016 では、Hadoop で外部データに対してクエリを実行したり、Azure Blob Storage のデータをインポート/エクスポートしたりできます。 クエリは Hadoop に計算をプッシュするように最適化されます。 Azure SQL データ ウェアハウスでは、Azure Blob Storage と Azure Data Lake Store からデータをインポート/エクスポートできます。
  
  
 PolyBase を使用するには、「 [PolyBase の概要](../../relational-databases/polybase/get-started-with-polybase.md)」を参照してください。  
  
 ![PolyBase 論理](../../relational-databases/polybase/media/polybase-logical.png "PolyBase 論理")  
  
## <a name="why-use-polybase"></a>PolyBase を使用する理由  
的確な意思決定を行うには、リレーショナル データとテーブルとして構造化されていない他のデータ (特に Hadoop) の両方を分析します。 これは、種類の異なるデータ ストア間でデータを転送する手段がない限り、実行するのは困難です。 PolyBase は、SQL Server にとって外部のデータに対する操作により、このようなギャップを埋めます。  
  
単純にしておくために、PolyBase を使用するうえで Hadoop 環境に追加のソフトウェアをインストールする必要はありません。 外部データの照会では、データベース テーブルの照会と同じ構文が使用されます。 これはすべてに透過的に行われます。 PolyBase は詳細をすべてバックグラウンドで処理するので、エンド ユーザーは Hadoop の知識がなくても外部テーブルに対するクエリを実行できます。 
  
 PolyBase には、以下の機能があります。  
  
-   **SQL Server または PDW から Hadoop に格納されたデータのクエリを実行する。** ユーザーは、たとえば Hadoop など、コスト効果の高いスケーラブルな分散システムにデータを格納しています。 PolyBase を使用すると、T-SQL で簡単にデータを照会できます。  
  
-   **Azure Blob Storage に格納されたデータのクエリを実行する。** Azure BLOB ストレージは、Azure サービスによって使用されるデータを格納するのに便利な場所です。  PolyBase を使用すると、T-SQL で簡単にデータにアクセスできます。  
  
-   **Hadoop、Azure Blob Storage、Azure Data Lake Store からデータをインポートする。** Hadoop、Azure BLOB ストレージ、Azure Data Lake Store のデータをリレーショナル テーブルにインポートすることで、Microsoft SQL の列ストア テクノロジと分析機能の速度を活用できます。 ETL ツールやインポート ツールを個別に用意する必要はありません。  

-   **Hadoop、Azure BLOB ストレージ、Azure Data Lake Store にデータをエクスポートする。** データを Hadoop、Azure BLOB ストレージ、Azure Data Lake Store にアーカイブすることで、コスト効果の高いストレージを実現し、アクセスしやすいようにそのストレージをオンライン状態にしておくことができます。  
  
-   **BI ツールと統合される。** PolyBase を Microsoft のビジネス インテリジェンスや分析スタックと一緒に使用したり、SQL Server と互換性のあるサード パーティ ツールを使用したりすることができます。  
  
## <a name="performance"></a>[パフォーマンス]  
  
-   **計算を Hadoop にプッシュする。**クエリ オプティマイザーは、クエリ パフォーマンスが向上するのであれば、Hadoop に計算をプッシュすることをコストに基づいて決定します。  コスト ベースの決定には、外部テーブルの統計が使用されます。 計算のプッシュでは、MapReduce ジョブが作成され、Hadoop の分散コンピューティング リソースが活用されます。  
  
-   **コンピューティング リソースをスケーリングする。** クエリのパフォーマンスを向上させるために、SQL Server [PolyBase スケールアウト グループ](../../relational-databases/polybase/polybase-scale-out-groups.md)を使用できます。 これにより、SQL Server インスタンスと Hadoop ノードの間の並列データ転送が可能になります。また、外部データに対する操作のためのコンピューティング リソースが追加されます。  
  
## <a name="polybase-guide-topics"></a>PolyBase ガイドに関するトピック  
 このガイドには、効率的かつ効果的に PolyBase を使用するためのトピックが含まれています。  
  
|||  
|-|-|  
|**トピック**|**[説明]**|  
|[PolyBase の概要](../../relational-databases/polybase/get-started-with-polybase.md)|PolyBase をインストールして構成するための基本的な手順。 Hadoop または Azure BLOB ストレージ内のデータを指す外部オブジェクトを作成する方法と、クエリの例を示しています。|  
|[PolyBase のバージョン管理機能の概要](../../relational-databases/polybase/polybase-versioned-feature-summary.md)|SQL Server、SQL Database、および SQL Data Warehouse でサポートされる PolyBase の機能について説明しています。|  
|[PolyBase スケールアウト グループ](../../relational-databases/polybase/polybase-scale-out-groups.md)|SQL Server スケールアウト グループを使用した SQL Server と Hadoop の間のスケールアウト並列処理。|  
|[PolyBase のインストール](../../relational-databases/polybase/polybase-installation.md)|インストール ウィザードまたはコマンド ライン ツールを使用して PolyBase をインストールするためのリファレンスおよび手順。|  
|[PolyBase の構成](../../relational-databases/polybase/polybase-configuration.md)|SQL Server の設定を PolyBase 対応に構成します。  たとえば、計算プッシュ ダウンや Kerberos セキュリティを構成します。|  
|[PolyBase T-SQL オブジェクト](../../relational-databases/polybase/polybase-t-sql-objects.md)|外部データを定義してそれにアクセスするために PolyBase が使用する T-SQL オブジェクトを作成します。|  
|[PolyBase Queries](../../relational-databases/polybase/polybase-queries.md)|T-SQL ステートメントを使用して、外部データを照会、インポート、またはエクスポートします。|  
|[PolyBase のトラブルシューティング](../../relational-databases/polybase/polybase-troubleshooting.md)|PolyBase クエリを管理するための手法。 動的管理ビュー (DMV) を使用して PolyBase クエリを監視できます。また、PolyBase クエリ プランを読み解いてパフォーマンス上のボトルネックを見つける方法を説明しています。|  
  
  
