---
title: セキュリティの概念
titleSuffix: SQL Server big data clusters
description: この記事では、SQL Server 2019 ビッグ データ クラスター (プレビュー) のセキュリティの概念について説明します。 これには、クラスター エンドポイントとクラスター認証の説明が含まれます。
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 54ae86785590eb26fb8ac402f3ae8ab6c7f29a98
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "67958664"
---
# <a name="security-concepts-for-sql-server-big-data-clusters"></a>SQL Server ビッグ データ クラスターのセキュリティの概念

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

セキュリティで保護されたビッグ データ クラスターとは、SQL Server と HDFS/Spark の両方にまたがる、認証と承認のシナリオに対する一貫性のあるわかりやすいサポートを意味します。 認証とは、ユーザーまたはサービスの身元を確認し、ユーザーまたはサービスが本物であることを確認するプロセスです。 承認とは、要求元のユーザーの ID に基づいて、特定のリソースへのアクセスを許可または拒否することを意味します。 この手順は、ユーザーが認証によって識別された後に実行されます。

通常、ビッグ データのコンテキストにおける承認は、ユーザー ID と特定のアクセス許可を関連付けるアクセス制御リスト (ACL) を使用して実行されます。 HDFS は、サービス API、HDFS ファイル、およびジョブ実行に対するアクセスを制限することで、承認をサポートするものです。

この記事では、ビッグ データ クラスターのセキュリティに関する重要な概念について説明します。

## <a name="cluster-endpoints"></a>クラスター エンドポイント

ビッグ データ クラスターには 3 つのエントリ ポイントがあります。

* HDFS/Spark (Knox) ゲートウェイ - これは HTTPS ベースのエンドポイントです。 その他のエンドポイントは、これを通じてプロキシ処理されます。 HDFS/Spark ゲートウェイは、webHDFS や Livy などのサービスにアクセスするために使用されます。 Knox への参照が表示されている場合は、エンドポイントです。

* コントローラー エンドポイント - クラスターを管理するための REST API を公開しているビッグ データ クラスター管理サービスです。 一部のツールは、このエンドポイントからもアクセスできます。

* マスター インスタンス - クラスター内の SQL Server マスター インスタンスに接続するためのデータベース ツールとアプリケーションの TDS エンドポイント。

![クラスター エンドポイント](media/concept-security/cluster_endpoints.png)

現時点では、外部からクラスターにアクセスするための追加のポートを開くオプションはありません。

### <a name="how-endpoints-are-secured"></a>エンドポイントをセキュリティで保護する方法

ビッグ データ クラスター内のエンドポイントのセキュリティ保護は、パスワードを使用して行います。パスワードは、環境変数または CLI コマンドを使用して設定/更新できます。 すべてのクラスター内部パスワードは、Kubernetes シークレットとして格納されます。  

## <a name="authentication"></a>[認証]

クラスターをプロビジョニングすると、複数のログインが作成されます。

これらのログインの中には、サービスの相互通信用のものや、エンドユーザーがクラスターにアクセスするためのものがあります。

### <a name="end-user-authentication"></a>エンドユーザー認証
クラスターをプロビジョニングするとき、環境変数を使用して、複数のエンドユーザー パスワードを設定する必要があります。 これらは、SQL 管理者およびクラスター管理者がサービスにアクセスするために使用するパスワードです。

コントローラーのユーザー名:
 + CONTROLLER_USERNAME=<controller_username>

コントローラーのパスワード:  
 + CONTROLLER_PASSWORD=<controller_password>

SQL マスター SA のパスワード: 
 + MSSQL_SA_PASSWORD=<controller_sa_password>

HDFS/Spark エンドポイントにアクセスするためのパスワード:
 + KNOX_PASSWORD=<knox_password>

### <a name="intra-cluster-authentication"></a>クラスター内認証

クラスターを展開すると、複数の SQL ログインが作成されます。

* システムで管理されるコントローラー SQL インスタンス内に、sysadmin ロールを持つ特別な SQL ログインが作成されます。 このログインのパスワードは、K8s シークレットとしてキャプチャされます。

* sysadmin ログインは、コントローラーによって所有および管理される、クラスター内のすべての SQL インスタンスに作成されます。 これらのインスタンスに対して、HA のセットアップやアップグレードなどの管理タスクがコントローラーによって実行される必要があります。 これらのログインは、データ プールと通信する SQL マスター インスタンスなど、SQL インスタンス間のクラスター内通信にも使用されます。

> [!NOTE]
> 現在のリリースでは、基本認証のみがサポートされています。 HDFS オブジェクトおよび SQL ビッグ データ クラスターのコンピューティングとデータ プールに対するきめ細かいアクセス制御はまだ使用できません。

## <a name="intra-cluster-communication"></a>クラスター内通信

ビッグ データ クラスター内の SQL 以外のサービスとの通信 (Livy から Spark へ、または Spark から記憶域プールへの通信など) は、証明書を使用して保護されます。 SQL Server と SQL Server との通信はすべて、SQL ログインを使用して保護されます。

## <a name="next-steps"></a>次の手順

SQL Server ビッグ データ クラスターの詳細については、次のリソースを参照してください。

- [SQL Server 2019 ビッグ データ クラスターとは](big-data-cluster-overview.md)
- [ワークショップ: Microsoft SQL Server ビッグ データ クラスターのアーキテクチャ](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
