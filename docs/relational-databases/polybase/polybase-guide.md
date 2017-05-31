---
title: "PolyBase ガイド | Microsoft Docs"
ms.date: 12/08/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-polybase
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- PolyBase
- PolyBase, guide
helpviewer_keywords:
- PolyBase
- PolyBase, overview
- "Hadoop import ×"
- Hadoop export
- Hadoop export, PolyBase overview
- Hadoop import, PolyBase overview
ms.assetid: b42b7d48-328a-4046-abe9-f73fd83212dc
caps.latest.revision: 26
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 627fdce2e1c294343680b119e9b0c36fc3d8665d
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="polybase-guide"></a>PolyBase ガイド
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  PolyBase は、非リレーショナル データとリレーショナル データの両方にすべて SQL Server 内からアクセスし、それらを結合するためのテクノロジです。  SQL Server 2016 では、Hadoop または Azure BLOB ストレージ内の外部データに対してクエリを実行できます。 クエリは Hadoop に計算をプッシュするように最適化されます。 Azure SQL データ ウェアハウスでは、Azure BLOB ストレージと Azure Data Lake Store からデータをインポートできます。
  
Transact-SQL (T-SQL) ステートメントを使用し、SQL Server 内のリレーショナル テーブルと Hadoop または Azure BLOB ストレージに格納されている非リレーショナル データとの間でデータをインポートしたり、エクスポートしたりできます。 T-SQL クエリ内から外部データを照会して、それをリレーショナル データと結合することもできます。  
  
 PolyBase を使用するには、「 [PolyBase の概要](../../relational-databases/polybase/get-started-with-polybase.md)」を参照してください。  
  
 ![PolyBase 論理](../../relational-databases/polybase/media/polybase-logical.png "PolyBase 論理")  
  
## <a name="why-use-polybase"></a>PolyBase を使用する理由  
的確な意思決定を行うには、リレーショナル データとテーブルとして構造化されていない他のデータ (特に Hadoop) の両方を分析します。 これは、種類の異なるデータ ストア間でデータを転送する手段がない限り、実行するのは困難です。 PolyBase は、SQL Server にとって外部のデータに対する操作により、このようなギャップを埋めます。  
  
単純にしておくために、PolyBase を使用するうえで Hadoop 環境や Azure 環境に追加のソフトウェアをインストールする必要はありません。 外部データの照会では、データベース テーブルの照会と同じ構文が使用されます。 これはすべてに透過的に行われます。 PolyBase は詳細をすべてバックグラウンドで処理するので、PolyBase を正しく使用するうえで Hadoop や Azure に関する知識は不要です。 
  
 PolyBase には、以下の機能があります。  
  
-   **Hadoop に格納されたデータを照会する。** ユーザーは、たとえば Hadoop など、コスト効果の高いスケーラブルな分散システムにデータを格納しています。 PolyBase を使用すると、T-SQL で簡単にデータを照会できます。  
  
-   **Azure BLOB ストレージに格納されたデータを照会する。** Azure BLOB ストレージは、Azure サービスによって使用されるデータを格納するのに便利な場所です。  PolyBase を使用すると、T-SQL で簡単にデータにアクセスできます。  
  
-   **Hadoop、Azure BLOB ストレージ、Azure Data Lake Store からデータをインポートする。** Hadoop、Azure BLOB ストレージ、Azure Data Lake Store のデータをリレーショナル テーブルにインポートすることで、Microsoft SQL の列ストア テクノロジと分析機能の速度を活用できます。 ETL ツールやインポート ツールを個別に用意する必要はありません。  

  
-   **Hadoop、Azure BLOB ストレージ、Azure Data Lake Store にデータをエクスポートする。** データを Hadoop、Azure BLOB ストレージ、Azure Data Lake Store にアーカイブすることで、コスト効果の高いストレージを実現し、アクセスしやすいようにそのストレージをオンライン状態にしておくことができます。  
  
-   **BI ツールと統合される。** PolyBase を Microsoft のビジネス インテリジェンスや分析スタックと一緒に使用したり、SQL Server と互換性のあるサード パーティ ツールを使用したりすることができます。  
  
## <a name="performance"></a>パフォーマンス  
  
-   **計算を Hadoop にプッシュする。**クエリ オプティマイザーは、クエリ パフォーマンスが向上するのであれば、Hadoop に計算をプッシュすることをコストに基づいて決定します。  コスト ベースの決定には、外部テーブルの統計が使用されます。   計算のプッシュでは、MapReduce ジョブが作成され、Hadoop の分散コンピューティング リソースが活用されます。  
  
-   **コンピューティング リソースをスケーリングする。** クエリのパフォーマンスを向上させるために、SQL Server [PolyBase スケールアウト グループ](../../relational-databases/polybase/polybase-scale-out-groups.md)を使用できます。 これにより、SQL Server インスタンスと Hadoop ノードの間の並列データ転送が可能になります。また、外部データに対する操作のためのコンピューティング リソースが追加されます。  
  
## <a name="polybase-guide-topics"></a>PolyBase ガイドに関するトピック  
 このガイドには、効率的かつ効果的に PolyBase を使用するためのトピックが含まれています。  
  
|||  
|-|-|  
|**トピック**|**説明**|  
|[PolyBase の概要](../../relational-databases/polybase/get-started-with-polybase.md)|PolyBase をインストールして構成するための基本的な手順。 Hadoop または Azure BLOB ストレージ内のデータを指す外部オブジェクトを作成する方法と、クエリの例を示しています。|  
|[PolyBase のバージョン管理機能の概要](../../relational-databases/polybase/polybase-versioned-feature-summary.md)|SQL Server、SQL Database、および SQL Data Warehouse でサポートされる PolyBase の機能について説明しています。|  
|[PolyBase スケールアウト グループ](../../relational-databases/polybase/polybase-scale-out-groups.md)|SQL Server スケールアウト グループを使用した SQL Server と Hadoop の間のスケールアウト並列処理。|  
|[PolyBase のインストール](../../relational-databases/polybase/polybase-installation.md)|インストール ウィザードまたはコマンド ライン ツールを使用して PolyBase をインストールするためのリファレンスおよび手順。|  
|[PolyBase の構成](../../relational-databases/polybase/polybase-configuration.md)|SQL Server の設定を PolyBase 対応に構成します。  たとえば、計算プッシュ ダウンや Kerberos セキュリティを構成します。|  
|[PolyBase T-SQL オブジェクト](../../relational-databases/polybase/polybase-t-sql-objects.md)|外部データを定義してそれにアクセスするために PolyBase が使用する T-SQL オブジェクトを作成します。|  
|[PolyBase Queries](../../relational-databases/polybase/polybase-queries.md)|T-SQL ステートメントを使用して、外部データを照会、インポート、またはエクスポートします。|  
|[PolyBase のトラブルシューティング](../../relational-databases/polybase/polybase-troubleshooting.md)|PolyBase クエリを管理するための手法。 動的管理ビュー (DMV) を使用して PolyBase クエリを監視できます。また、PolyBase クエリ プランを読み解いてパフォーマンス上のボトルネックを見つける方法を説明しています。|  
  
  

