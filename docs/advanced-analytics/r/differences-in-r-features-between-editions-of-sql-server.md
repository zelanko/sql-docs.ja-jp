---
title: "SQL Server マシン ラーニング Services のエディションで利用可能な機能 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 16ca6c44b15c9fb7c1983d5a04175ebbade57895
ms.sourcegitcommit: 6b1618aa3b24bf6759b00a820e09c52c4996ca10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2018
---
# <a name="feature-availability-across-editions-of-sql-server-machine-learning-services"></a>エディションの SQL Server マシン ラーニング Services 全体で利用可能な機能
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
 
 SQL Server 2016 および SQL Server 2017 マシン学習機能を利用します。 この記事は、機能を提供するエディションを一覧表示、特定のエディションに適用される制限事項について説明し、特定のエディションでのみ使用できる機能の一覧します。

 > [!NOTE]
 > 一般に、SQL Server の Machine Learning (In-database) は含まれません、[操作運用](https://docs.microsoft.com/machine-learning-server/what-is-operationalization)スタンドアロン R サーバーまたは Machine Learning のサーバーのインストールに含まれている機能です。 操作運用では、web サービスの展開と、ホストが含まれていて、したがってその他の SQL Server 操作と同じリソースに対して競合します。
 > 
 > このため、web サービスとして予測モデルの展開をサポートするために別の物理サーバー上の SQL Server 2016 R Server (スタンドアロン) または SQL Server 2017 Machine Learning サーバー (スタンドアロン) のインストールをお勧めします。 

## <a name="sql-server-2017-machine-learning-services-in-database-and-standalone"></a>SQL Server 2017 マシン ラーニング Services (In-database) および (スタンドアロン)

Developer Edition では、Enterprise Edition のと同等のパフォーマンスを提供します。 運用環境には、Developer Edition の使用はサポートされていません。

|機能|Enterprise|Standard|Web|Express with Advanced Services|Express| 
|-------|----------|--------|---|------------------------------|-------|
| R インタープリター & 独自のパッケージ | はい | [ユーザー アカウント制御] | いいえ | いいえ | いいえ | 
| Python インタープリター & クライアント ライブラリ | はい | [ユーザー アカウント制御] | いいえ | いいえ | いいえ | 
| データのチャンキング <br/>(大量の新機能には、メモリ内に収まる範囲を超えるのデータを処理) | はい | いいえ | いいえ | いいえ | いいえ |
| スケール アップの処理 <br/>(2 つ以上のプロセッサ) | はい | いいえ | いいえ | いいえ | いいえ |
| 操作運用 | はい | いいえ | いいえ | いいえ | いいえ |
| [予測](../../t-sql/queries/predict-transact-sql.md)関数 <br/>(実行[ネイティブ スコアリング](../sql-native-scoring.md)事前トレーニング済みモデルは、必要なバイナリ形式で保存する前に) | はい | [ユーザー アカウント制御] | [ユーザー アカウント制御] | [ユーザー アカウント制御] | はい |
| R のクライアントの互換性 | はい | [ユーザー アカウント制御] | いいえ | いいえ | いいえ | 
| Microsoft R Open | はい | [ユーザー アカウント制御] | いいえ | いいえ | いいえ | 
| Anaconda Python 3.5 | はい | [ユーザー アカウント制御] | いいえ | いいえ | いいえ | 

## <a name="sql-server-2016-r-services-in-database-and-r-server-standalone"></a>SQL Server 2016 R Services (In-database) と R Server (スタンドアロン)

使用可能な機能では、まず 2016年のリリースの含まれていない Python サポート マイナス、2017年と同じです。

## <a name="r-feature-availability-in-azure-sql-database"></a>Azure SQL データベースで使用できる R 機能
  
初期テストのリリースでは、後に R Services は現在**いない**保留中の開発ではさらに、Azure SQL データベースで使用できます。 

## <a name="performance-expectations-for-enterprise-edition"></a>Enterprise Edition 用のパフォーマンスの予測

Machine learning ソリューションでのパフォーマンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]一般に従来の R を使用して、同じハードウェアを指定された実装を超えると予想されます。 SQL Server で R ソリューション実行できるサーバーのリソースを使用するためと、場合がありますを使用して複数のプロセスに配布する、 **RevoScaleR**関数。 

パフォーマンスが Python ソリューションでは、評価されていない機能は、開発中は、適用する同じ利点の一部が必要とします。

Vs の Enterprise Edition で実行された場合は、ソリューションを学習、同じコンピューターのパフォーマンスとスケーラビリティに大きな差異を表示することができますも期待します。Standard エディションです。 原因としては、これにより、RevoScaleR 関数をメモリに収まりきらない場合より多くのデータを処理を並列処理、機械学習に使用できる増加したスレッドおよびストリーミング (またはチャンキング) のサポートにあります。 

ただし、R、または Python コードの外部の多くの要因によって同じハードウェア上であってもパフォーマンスに影響することができます。 これらの要因には、サーバーのリソースに対する競合する要求により、作成されるクエリ プランの種類、スキーマの変更、統計を更新または新しいクエリ プラン、断片化、およびその詳細を作成する必要があります。 R、または Python コードを含む可能性があります (秒)、1 つの作業負荷で実行しますが、かかるストアド プロシージャは分場合に可能であれば他のサービスが実行されています。  そのため、マシン学習のパフォーマンスを測定するときに、リモート計算コンテキストでネットワークをなど、サーバー パフォーマンスのさまざまな側面を監視することをお勧めします。

構成することをお勧め[リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md) (Enterprise Edition で使用可能) 外部スクリプトのジョブは優先順位を付ける内またはサーバーに高い負荷を処理する方法をカスタマイズします。 外部スクリプトのジョブのソースを指定し、特定のワークロードの優先順位を設定、SQL クエリで使用されるメモリの量を制限する分類子関数を定義し、ワークロードごとに使用される並列処理の数を制御できます。

## <a name="see-also"></a>参照

+ [SQL Server 2016 のエディションとコンポーネント](../../sql-server/editions-and-components-of-sql-server-2016.md)
+ [SQL Server 2017 のエディションとコンポーネント](../../sql-server/editions-and-components-of-sql-server-2017.md)
+ [R (Machine Learning サーバー) で、big data コンピューティングに関するヒント](https://docs.microsoft.com/machine-learning-server/r/tutorial-large-data-tips)
