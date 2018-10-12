---
title: PolyBase ガイド | Microsoft Docs
ms.date: 05/31/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: polybase
ms.tgt_pltfrm: ''
ms.topic: quickstart
f1_keywords:
- PolyBase
- PolyBase, guide
helpviewer_keywords:
- PolyBase
- PolyBase, overview
- Hadoop import
- Hadoop export
- Hadoop export, PolyBase overview
- Hadoop import, PolyBase overview
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: c31f9538f3429ff4ae1182ee0cd974996cc705a6
ms.sourcegitcommit: 82bb56269faf3fb5dd1420418e32a0a6476780cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2018
ms.locfileid: "43694725"
---
# <a name="polybase-guide"></a>PolyBase ガイド

[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]

PolyBase を使用すると、SQL Server 2016 インスタンスで Hadoop からデータを読み取る Transact-SQL クエリを処理できるようになります。 同じクエリで SQL Server のリレーショナル テーブルにアクセスすることもできます。 また、PolyBase では、同じクエリで Hadoop と SQL Server のデータを結合させることもできます。 SQL Server では、[外部テーブル](../../t-sql/statements/create-external-table-transact-sql.md)または[外部データ ソース](../../t-sql/statements/create-external-data-source-transact-sql.md)によって Hadoop と接続します。

PolyBase では、次の Microsoft の SQL 製品にこれらと同じ機能を提供します。

- SQL Server 2016 以降のバージョン
- Analytics Platform System (旧称 Parallel Data Warehouse)
- Azure SQL Data Warehouse

PolyBase では、クエリ全体を最適化するために計算の一部が Hadoop ノードにプッシュされます。 しかし、PolyBase の外部アクセスは Hadoop だけではありません。 その他の構造化されていない非リレーショナル テーブルもサポートしています (区切られたテキスト ファイルなど)。

#### <a name="data-import-and-export"></a>データのインポートとエクスポート

下層 の PolyBase のサポートにより、T-SQL クエリでは Azure Blob Storage のデータをインポートおよびエクスポートすることもできます。 さらに、PolyBase によって、Azure SQL Data Warehouse で Azure Data Lake Store および Azure Blob Storage のデータをインポートおよびエクスポートできるようになります。

PolyBase の使用については、「[PolyBase の概要](../../relational-databases/polybase/get-started-with-polybase.md)」をご覧ください。
  
![PolyBase 論理](../../relational-databases/polybase/media/polybase-logical.png "PolyBase 論理")

## <a name="why-use-polybase"></a>PolyBase を使用する理由

SQL Server のデータを外部データと結合することは、以前はもっと困難でした。 次の好ましくないオプションのどちらかを選択する必要がありました。

- すべてのデータをどちらか一方の形式に統一するために、片方のデータを転送する。
- 両方のデータのソースに対してクエリを実行した後、クライアント レベルでデータを結合および統合するためにカスタムのクエリ ロジックを記述する。

PolyBase では T-SQL を使用してデータを結合するので、これらの好ましくないオプションは不要になります。

シンプルさを保つため、Hadoop 環境に追加のソフトウェアをインストールしなくても PolyBase を使用することができます。 外部データを照会するには、データベース テーブルの照会に使用したのと同じ T-SQL 構文を使用します。 PolyBase が実装する補助的なアクションは、すべて透過的に実行されます。 クエリの作成者に Hadoop の知識は必要ありません。

PolyBase には、以下の機能があります。

- **SQL Server または PDW から Hadoop に格納されたデータのクエリを実行する。** ユーザーは、たとえば Hadoop など、コスト効果の高いスケーラブルな分散システムにデータを格納しています。 PolyBase を使用すると、T-SQL で簡単にデータを照会できます。

- **Azure Blob Storage に格納されたデータのクエリを実行する。** Azure BLOB ストレージは、Azure サービスによって使用されるデータを格納するのに便利な場所です。  PolyBase を使用すると、T-SQL で簡単にデータにアクセスできます。

- **Hadoop、Azure Blob Storage、Azure Data Lake Store からデータをインポートする。** Hadoop、Azure Blob Storage、または Azure Data Lake Store からリレーショナル テーブルにデータをインポートすることで、Microsoft SQL の高速な列ストア テクノロジおよび分析機能を活用できます。 ETL ツールやインポート ツールを個別に用意する必要はありません。

- **Hadoop、Azure BLOB ストレージ、Azure Data Lake Store にデータをエクスポートする。** データを Hadoop、Azure BLOB ストレージ、Azure Data Lake Store にアーカイブすることで、コスト効果の高いストレージを実現し、アクセスしやすいようにそのストレージをオンライン状態にしておくことができます。

- **BI ツールと統合する。** PolyBase を Microsoft のビジネス インテリジェンスや分析スタックと一緒に使用したり、SQL Server と互換性のあるサード パーティ ツールを使用したりすることができます。

## <a name="performance"></a>パフォーマンス

- **Hadoop に計算をプッシュする。** クエリ オプティマイザーはコスト ベースの決定を行い、クエリのパフォーマンスが向上する場合は Hadoop に計算をプッシュします。  コスト ベースの決定には、外部テーブルの統計が使用されます。 計算のプッシュでは、MapReduce ジョブが作成され、Hadoop の分散コンピューティング リソースが活用されます。

- **コンピューティング リソースをスケーリングする。** クエリのパフォーマンスを向上させるために、SQL Server [PolyBase スケールアウト グループ](../../relational-databases/polybase/polybase-scale-out-groups.md)を使用できます。 これにより、SQL Server インスタンスと Hadoop ノードの間の並列データ転送が可能になります。また、外部データに対する操作のためのコンピューティング リソースが追加されます。

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
| &nbsp; | &nbsp; |
  
