---
title: "SQL Server マシン ラーニング Services のエディションで利用可能な機能 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2018
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
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: 4322211bcc3a5466976368b9562ed3e95ad7e331
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2018
---
# <a name="feature-availability-across-editions-of-sql-server-machine-learning-services"></a>エディションの SQL Server マシン ラーニング Services 全体で利用可能な機能
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
 
 SQL Server 2016 および SQL Server 2017 マシン学習機能を利用します。 この記事は、機能を提供するエディションを一覧表示、特定のエディションに適用される制限事項について説明し、特定のエディションでのみ使用できる機能の一覧します。


## <a name="sql-server-2017-machine-learning-features"></a>SQL Server 2017 機械学習機能

Enterprise および Developer エディションでは、エンタープライズ インストール用のソリューションをビルドするには同じコストをかけずにできるように、同じ機能カバレッジがあります。 エディションは、機能的 equivlanet、Developer Edition の使用は運用環境でサポートされていません。

基本と高度な統合の違いは、小数点以下桁数です。 高度な統合は、コンピューターに対応できるサイズを問わず、データ セットの並列処理のすべての使用可能なコアを使用できます。 基本的な統合は、2 コアとメモリに収まるデータ セットに制限されています。 

基本と高度な統合は、(In-database) のインスタンスに適用されます。 スタンドアロン サーバーでは、データベース エンジン インスタンス機能ではなく、開発者および Enterprise エディションでのみのインストール オプションとして提供しています。

|機能|Enterprise|Standard|Web|Express with Advanced Services|Express 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|基本的な R 統合|はい|[ユーザー アカウント制御]|[ユーザー アカウント制御]|[ユーザー アカウント制御]|いいえ|   
|高度な R 統合|はい|いいえ|いいえ|いいえ|いいえ| 
|基本的な Python 統合|はい|[ユーザー アカウント制御]|[ユーザー アカウント制御]|[ユーザー アカウント制御]|いいえ|
|高度な Python 統合|はい|いいえ|いいえ|いいえ|いいえ| 
|Machine Learning Server (スタンドアロン)|はい|いいえ|いいえ|いいえ|いいえ|   

 > [!NOTE]
 > (スタンドアロン) サーバーのみを提供、[操作運用](https://docs.microsoft.com/machine-learning-server/what-is-operationalization)Microsoft (SQL-製以外) R サーバーまたは Machine Learning のサーバーのインストールに含まれている機能です。 操作運用には、web サービスの配置とホスティング機能が含まれています。
>
> (In-database) インストールでは、ソリューションの運用に同等のアプローチが機能を利用するデータベース エンジンのストアド プロシージャで実行できる関数にコードを変換する場合。


## <a name="sql-server-2016-r-features"></a>SQL Server 2016 の R の機能

SQL Server 2016 には、R 統合のみが含まれています。 SQL Server 2016 では、基本と高度な R 統合は、SQL Server 2017 と同じです。

## <a name="r-feature-availability-in-azure-sql-database"></a>Azure SQL データベースで使用できる R 機能
  
初期テストのリリースでは、後に R Services は、保留中のさらなる開発 Azure SQL データベースから削除されました。 

## <a name="performance-expectations-for-enterprise-edition"></a>Enterprise Edition 用のパフォーマンスの予測

Machine learning ソリューションでのパフォーマンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]一般に従来の R を使用して、同じハードウェアを指定された実装を超えると予想されます。 SQL Server で R ソリューション実行できるサーバーのリソースを使用するためと、場合がありますを使用して複数のプロセスに配布する、 **RevoScaleR**関数。 

Vs の Enterprise Edition で実行された場合は、ソリューションを学習、同じコンピューターのパフォーマンスとスケーラビリティに大きな差異を表示することができますも期待します。Standard エディションです。 原因としては、これにより、RevoScaleR 関数をメモリに収まりきらない場合より多くのデータを処理を並列処理、機械学習に使用できる増加したスレッドおよびストリーミング (またはチャンキング) のサポートにあります。 

ただし、R、または Python コードの外部の多くの要因によって同じハードウェア上であってもパフォーマンスに影響することができます。 これらの要因には、サーバーのリソースに対する競合する要求により、作成されるクエリ プランの種類、スキーマの変更、統計を更新または新しいクエリ プラン、断片化、およびその詳細を作成する必要があります。 R、または Python コードを含む可能性があります (秒)、1 つの作業負荷で実行しますが、かかるストアド プロシージャは分場合に可能であれば他のサービスが実行されています。  そのため、マシン学習のパフォーマンスを測定するときに、リモート計算コンテキストでネットワークをなど、サーバー パフォーマンスのさまざまな側面を監視することをお勧めします。

構成することをお勧め[リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md) (Enterprise Edition で使用可能) 外部スクリプトのジョブは優先順位を付ける内またはサーバーに高い負荷を処理する方法をカスタマイズします。 外部スクリプトのジョブのソースを指定し、特定のワークロードの優先順位を設定、SQL クエリで使用されるメモリの量を制限する分類子関数を定義し、ワークロードごとに使用される並列処理の数を制御できます。

## <a name="see-also"></a>参照

+ [SQL Server 2016 のエディションとコンポーネント](../../sql-server/editions-and-components-of-sql-server-2016.md)
+ [SQL Server 2017 のエディションとコンポーネント](../../sql-server/editions-and-components-of-sql-server-2017.md)
+ [R (Machine Learning サーバー) で、big data コンピューティングに関するヒント](https://docs.microsoft.com/machine-learning-server/r/tutorial-large-data-tips)
