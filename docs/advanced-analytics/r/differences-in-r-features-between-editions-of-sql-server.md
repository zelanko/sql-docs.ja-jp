---
title: "SQL Server のエディション間の machine learning の機能の相違 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/16/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b33a3e2-04d3-4bad-9335-9568ae09db0b
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: f4fd73dd213b004916fb99dcb95146221116da8e
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2018
---
# <a name="differences-in-machine-learning-features-between-editions-of-sql-server"></a>SQL Server のエディション間の machine learning の機能の相違
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
 
 機械学習のサポートは、SQL Server 2016 および SQL Server 2017 で使用できます。 この記事は、機能をサポートするエディションを一覧表示、特定のエディションに適用される追加の制限事項について説明し、特定のエディションでのみ利用可能な機能を示します。

 > [!NOTE]
 > 一般に、SQL Server の機械学習は含まれません、[操作運用](https://docs.microsoft.com/machine-learning-server/what-is-operationalization)Microsoft R Server または Machine Learning のサーバーに含まれている機能です。
 > 
 > これらの機能を必要がある場合インストールできます Microsoft R Server または Machine Learning のサーバーとは別に、web サービスとして予測モデルの展開をサポートします。 

## <a name="summary-of-differences"></a>相違点の概要

-   **Enterprise Edition**
    
     SQL Server 2017 には、Machine Learning サービス (データベースが含まれています。 SQL Server 2016 には、R Services が含まれています。 この機能は、SQL Server のコンピューティング コンテキストとして使用するなど、SQL Server でのデータベース内分析をサポートします。
     
     SQL Server 2017 には、Microsoft Machine Learning Server (スタンドアロン) が含まれています。 SQL Server 2016 には、Microsoft R Server (スタンドアロン) が含まれています。 この機能は、機械学習が不要でコンピューティング コンテキストとして使用する SQL Server の使用をサポートします。

     並列処理とストリーミングによって最適化されたパフォーマンスとスケーラビリティを提供する Enterprise Edition でこれらの機能に制限はありません。 また、このエディションには、ストリーミング、および並列実行のためのプラットフォームのサポートの使用が最大化します。 Standard Edition とは異なり、データを入力することを意味は、メモリに適合する必要はありませんが、ストリーミングすることができます。
     
     SQL Server を使用してデータベースの分析では、サーバー リソース使用率をカスタマイズする外部のスクリプトのリソース管理をサポートします。
     
     Microsoft R Server と Machine Learning のサーバーの新しいエディションには、迅速なセキュリティで保護された展開をサポートする操作運用のエンジンのバージョンおよび R ソリューションの共有が含まれます。 詳細については、次を参照してください。 [Machine Learning のサーバーで分析を使用できるように](https://docs.microsoft.com/machine-learning-server/what-is-operationalization)です。

-   **Developer Edition**

     Enterprise Edition と同じ機能があります。ただし、Developer Edition は運用環境では使用できません。  
  
-   **Standard Edition**

     データベース内の分析のすべての機能に含まれている Enterprise Edition、リソース統制を除く。 パフォーマンスとスケール制限されます。 処理可能なデータがサーバーのメモリに収まる必要があると、使用する場合でも、処理は、1 つのコンピューティングのスレッドに制限されます、 **RevoScaleR**関数。
  
-   **Express および Web エディション**
  
     のみ Express Edition with Advanced Services では、機械学習機能が含まれます。 パフォーマンスの制限は、Standard Edition に似ています。 
     
     Web Edition は、機械学習モデルを作成するなどのタスクのものではありません。 ただし、予測関数を使用すると、トレーニング済みモデルを別の場所を使用してスコア付けを実行します。

-   **Azure SQL データベース**
  
     初期テストのリリースでは、後に R Services は現在**いない**保留中の開発ではさらに、Azure SQL データベースで使用できます。 

### <a name="external-script-languages-supported"></a>サポートされている外部のスクリプト言語

すべてのエディションは、次の machine learning 言語がサポートされています。

+ SQL Server 2017: R と Python
+ SQL Server 2016: R のみ

Microsoft R Open は、すべてのエディションに含まれます。

Microsoft R Client は、すべてのエディションで動作できます。

## <a name="machine-learning-in-enterprise-edition"></a>機械学習の Enterprise Edition で

Machine learning ソリューションでのパフォーマンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]一般に従来の R を使用して、同じハードウェアを指定された実装を超えると予想されます。 SQL Server で R ソリューション実行できるサーバーのリソースを使用するためと、場合がありますを使用して複数のプロセスに配布する、 **RevoScaleR**関数。 

パフォーマンスが Python ソリューションでは、評価されていない機能は、開発中は、適用する同じ利点の一部が必要とします。

Vs の Enterprise Edition で実行された場合は、ソリューションを学習、同じコンピューターのパフォーマンスとスケーラビリティに大きな差異を表示することができますも期待します。Standard エディションです。 原因としては、これにより、RevoScaleR 関数をメモリに収まりきらない場合より多くのデータを処理を並列処理、機械学習に使用できる増加したスレッドおよびストリーミング (またはチャンキング) のサポートにあります。 

ただし、R、または Python コードの外部の多くの要因によって同じハードウェア上であってもパフォーマンスに影響することができます。 これらの要因には、サーバーのリソースに対する競合する要求により、作成されるクエリ プランの種類、スキーマの変更、統計を更新または新しいクエリ プラン、断片化、およびその詳細を作成する必要があります。 R、または Python コードを含む可能性があります (秒)、1 つの作業負荷で実行しますが、かかるストアド プロシージャは分場合に可能であれば他のサービスが実行されています。  そのため、マシン学習のパフォーマンスを測定するときに、リモート計算コンテキストでネットワークをなど、サーバー パフォーマンスのさまざまな側面を監視することをお勧めします。

構成することをお勧め[リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md) (Enterprise Edition で使用可能) 外部スクリプトのジョブは優先順位を付ける内またはサーバーに高い負荷を処理する方法をカスタマイズします。 外部スクリプトのジョブのソースを指定し、特定のワークロードの優先順位を設定、SQL クエリで使用されるメモリの量を制限する分類子関数を定義し、ワークロードごとに使用される並列処理の数を制御できます。

## <a name="machine-learning-in-developer-edition"></a>機械学習の Developer Edition で

Developer Edition では、Enterprise Edition のと同等のパフォーマンスを提供します。

運用環境には、Developer Edition の使用はサポートされていません。

## <a name="machine-learning-in-standard-edition"></a>機械学習の Standard edition

同じハードウェア構成であれば、Standard Edition にも、標準的な R パッケージに比べて、パフォーマンス上のメリットがあります。

Standard Edition は、リソース ガバナーをサポートしていません。 Standard Edition には、パフォーマンスの制限と Enterprise edition と Developer edition と比較するとスケーラビリティも用意されています。

すべての**RevoScaleR**関数とパッケージは、Standard Edition に含まれてが起動し、R スクリプトを管理するサービスは、使用できるプロセスの数に制限されます。 さらに、スクリプトで処理されるデータは、メモリに収まる必要があります。

使用するソリューションに同じ制限が適用**revoscalepy**です。

## <a name="machine-learning-in-express-edition-with-advanced-services"></a>機械学習の Express Edition with Advanced Services で

Express Edition には、Standard Edition と同じ制限が適用されます。

## <a name="machine-learning-in-web-edition"></a>機械学習で Web Edition

Web edition は、R、または Python スクリプトの実行をサポートしません。 ただし、使用することができます、 [PREDICT](../../t-sql/queries/predict-transact-sql.md)を実行する関数[ネイティブ スコアリング](../sql-native-scoring.md)別の SQL Server または R Server のインスタンスでトレーニングおよび、必要なバイナリ形式で保存されているモデルにします。

## <a name="next-steps"></a>次の手順

詳細については、以下をご覧ください。

+ [SQL Server 2016 のエディションとコンポーネント](../../sql-server/editions-and-components-of-sql-server-2016.md)
+ [SQL Server 2017 のエディションとコンポーネント](../../sql-server/editions-and-components-of-sql-server-2017.md)

SQL Server の他の機能の詳細についてを参照してください。

+ [エディションと SQL Server 2016 のサポートされる機能](../../sql-server/editions-and-components-of-sql-server-2016.md) 

大きなデータ セット用のソリューションを最適化する方法の詳細については、次を参照してください。 [R での big data コンピューティングに関するヒント](https://docs.microsoft.com/machine-learning-server/r/tutorial-large-data-tips)ドキュメント。
