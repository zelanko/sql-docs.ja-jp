---
title: マスター インスタンスの SQL Server のビッグ データ クラスターとは何ですか。 | Microsoft Docs
description: この記事では、SQL Server 2019 ビッグ データ クラスター内のマスター インスタンスについて説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 7c58d925e9d52ee4496f8a324eab91bbfa7ccaad
ms.sourcegitcommit: 182d77997133a6e4ee71e7a64b4eed6609da0fba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50051064"
---
# <a name="what-is-the-sql-server-big-data-cluster-master-instance"></a>マスター インスタンスをクラスター、SQL Server のビッグ データとは何ですか。

この記事では、の役割を説明します、 *SQL Server のマスター インスタンス*で SQL Server 2019 ビッグ ata クラスター。 マスター インスタンスが SQL Server のビッグ データ クラスターで実行されている SQL Server インスタンス[コントロール プレーン](big-data-cluster-overview.md#controlplane)します。

SQL Server のマスター インスタンスは、次の機能を提供します。

## <a name="connectivity"></a>接続

SQL Server のマスター インスタンスは、クラスターの外部からアクセスできる TDS エンドポイントを提供します。 アプリケーションまたは Azure Data Studio などの SQL Server ツールに接続することができますか、このエンドポイントと同じように SQL Server Management Studio は、他の SQL Server インスタンス。

## <a name="scale-out-query-management"></a>スケール アウト クエリの管理

SQL Server のマスター インスタンスには内のノード上の SQL Server インスタンス間でクエリを配布するために使用するスケール アウト クエリ エンジンが含まれています、[プールのコンピューティング](concept-compute-pool.md)します。 スケール アウト クエリ エンジンには、TRANSACT-SQL で、追加の構成なしでクラスター内のすべての Hive テーブルへのアクセスも提供します。 (Hive テーブルのサポートは、CTP 2.0 ではありません)

## <a name="metadata-and-user-databases"></a>データベース メタデータとユーザー データベース

標準の SQL Server システム データベースに加えて、SQL のマスター インスタンスも内容は次の。

- HDFS テーブルのメタデータを保持するメタデータ データベース
- データ プレーンのシャード マップ
- クラスターのデータ プレーンへのアクセスを提供する外部テーブルの詳細です。
- PolyBase の外部データ ソースと外部テーブルのユーザー データベースで定義されています。

SQL Server のマスター インスタンスにユーザー データベースを追加することもできます。

## <a name="machine-learning-services"></a>Machine learning サービス

SQL Server machine learning サービスは、SQL Server で Java、R および Python のコードを実行するため、データベース エンジンへのアドオン機能です。 この機能はコア エンジンのプロセスから外部プロセスの分離は、R または Python のステートメントを含む T-SQL スクリプトまたは Java、R ストアド プロシージャとしてのリレーショナル データを完全に統合される SQL Server の機能拡張フレームワークに基づいて、またはT-SQL を格納している Python コードです。

ビッグ データの SQL Server クラスターの一部として、machine learning サービスは既定では SQL Serevr マスター インスタンスで使用可能になります。 つまり外部スクリプトの実行が SQL Server のマスター インスタンスで有効にするとは、Java の sp_execute_external_script を使用して、R と Python のスクリプトの実行を可能にすることができます。

### <a name="advantages-of-machine-learning-services-in-a-big-data-cluster"></a>ビッグ データ クラスターでの machine learning サービスの利点

SQL Server 2019 では、通常、エンタープライズ データベースに格納されているディメンションのデータに参加するビッグ データを簡単にします。 ビッグ データの値は、ときだけで、組織の部分の効力はありませんが、レポート、ダッシュ ボード、およびアプリケーションにも含まれていますが大幅に増加します。 同時に、データ サイエンティストは Spark/HDFS エコシステム ツールを使用し、SQL Server のマスター インスタンスでアクセスできる外部データ ソースでデータをリアルタイムにアクセスがある容易なを続行できます_を通じて_SQL Server マスターインスタンス。

SQL Server 2019 ビッグ データのクラスターで行うことができますの詳細は、エンタープライズ データ レイクにします。 SQL Server の開発者およびアナリストことができます。

* Enterprise data lake からのデータを使用するアプリケーションをビルドします。
* Transact SQL クエリとすべてのデータの上の理由です。
* アクセスして企業データを分析するには、SQL Server ツールおよびアプリケーションの既存のエコシステムを使用します。
* データの仮想化とデータ マートのデータ移動の必要性を軽減します。
* Spark を使用してビッグ データのシナリオを続行します。
* Spark や SQL Server を使用して、データ レイク経由でモデルをトレーニングするインテリジェントなエンタープライズ アプリケーションをビルドします。
* 最適なパフォーマンスの実稼働データベースでのモデルを運用化します。
* リアルタイムの分析のためのエンタープライズ データ マートに直接 Stream データ。
* 視覚的に対話型分析と BI ツールを使用してデータを探索します。

## <a name="next-steps"></a>次の手順

SQL Server のビッグ データ クラスターに関する詳細については、次の概要を参照してください。

- [SQL Server 2019 ビッグ データ クラスターとは](big-data-cluster-overview.md)
