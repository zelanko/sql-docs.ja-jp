---
title: セキュリティの概念
titleSuffix: SQL Server 2019 big data clusters
description: この記事では、SQL Server 2019 ビッグ データ クラスター (プレビュー) のセキュリティの概念について説明します。 これには、クラスター エンドポイントとクラスターの認証の説明が含まれます。
author: nelgson
ms.author: negust
manager: craigg
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 5e440a3502e5062013ac5e3b716036f107a13c6a
ms.sourcegitcommit: 715683b5fc7a8e28a86be8949a194226b72ac915
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2019
ms.locfileid: "58477987"
---
# <a name="security-concepts-for-sql-server-big-data-clusters"></a>ビッグ データの SQL Server クラスターのセキュリティの概念

ビッグ データをセキュリティで保護されたクラスターでは、SQL Server と HDFS/Spark の両方で認証と承認のシナリオを首尾一貫したサポートを意味します。 認証は、ユーザーまたはサービスの id を確認し、それらがあると主張するユーザーはことを確認するプロセスです。 承認は、許可または要求しているユーザーの id に基づいて特定のリソースへのアクセスを拒否するを参照します。 ユーザーが認証によって特定した後は、この手順を実行します。

ビッグ データのコンテキストでの承認は通常、特定のアクセス許可を持つユーザーの id を関連付けるアクセス制御リスト (Acl) を実行します。 HDFS では、サービスの Api、HDFS のファイルとジョブの実行へのアクセスを制限することで承認をサポートしています。

この記事では、ビッグ データ クラスター内のキーのセキュリティに関連する概念を説明します。

## <a name="cluster-endpoints"></a>クラスター エンドポイント

ビッグ データ クラスターに 3 つのエントリ ポイントがあります。

* HDFS/Spark (Knox) ゲートウェイ - これは、HTTPS ベースのエンドポイント。 その他のエンドポイントは、この経由でプロキシ処理です。 HDFS/Spark ゲートウェイは、webHDFS Livy などのサービスにアクセスするために使用されます。 Knox への参照を表示すると、任意の場所は、エンドポイントです。

* コント ローラー エンドポイント - クラスターを管理するための REST Api を公開するビッグ データ クラスターの管理サービスです。 管理ポータルなどのいくつかのツールは、このエンドポイントからもアクセスされます。

* マスター インスタンスのデータベース ツールと、クラスター内の SQL Server マスター インスタンスに接続するアプリケーションの TDS エンドポイント。

![クラスター エンドポイント](media/concept-security/cluster_endpoints.png)

現時点では、外部からクラスターへのアクセスの追加のポートを開くためのオプションはありません。

### <a name="how-endpoints-are-secured"></a>エンドポイントを保護する方法

ビッグ データ クラスター内のエンドポイントをセキュリティで保護することができるパスワードを使用してセット/更新するか環境変数または CLI コマンドを使用します。 すべてのクラスター内部のパスワードは、Kubernetes シークレットとして格納されます。  

## <a name="authentication"></a>認証

クラスターをプロビジョニングすると、ログインの数が作成されます。

これらのログインの一部は、互いと通信するサービスと他のユーザーは、クラスターにアクセスするエンドユーザー。

### <a name="end-user-authentication"></a>エンドユーザー認証
クラスターをプロビジョニングするには、上のエンドユーザーのパスワードの数は環境変数を使用して設定する必要があります。 これらは、SQL 管理者とクラスターの管理者サービスへのアクセスに使用するパスワードです。

コント ローラーのユーザー名:
 + CONTROLLER_USERNAME=<controller_username>

コント ローラーのパスワード:  
 + CONTROLLER_PASSWORD=<controller_password>

SQL マスター SA パスワード: 
 + MSSQL_SA_PASSWORD=<controller_sa_password>

HDFS/Spark エンドポイントへのアクセスのパスワード:
 + KNOX_PASSWORD = < knox_password >

### <a name="intra-cluster-authentication"></a>クラスター内の認証

クラスターの展開時に、さまざまな SQL ログインが作成されます。

* 特別な SQL ログインは sysadmin ロールで、管理されているシステムであるコント ローラーの SQL インスタンスに作成されます。 このログインのパスワードは、K8s シークレットとしてキャプチャされます。

* コント ローラーが所有して管理すると、クラスター内のすべての SQL インスタンスで sysadmin ログインが作成されます。 これらのインスタンスで HA のセットアップやアップグレードなどの管理タスクを実行するコント ローラーに必要になります。 これらのログインは、SQL のマスター インスタンス データ プールとの通信などの SQL インスタンスの間で、クラスター間の通信にも使用されます。

> [!NOTE]
> 現在のリリースでは、基本的な認証のみがサポートされます。 HDFS オブジェクト、およびビッグ データ クラスター コンピューティングとデータ プール、SQL へのきめ細かいアクセス制御は、まだ使用できません。

## <a name="intra-cluster-communication"></a>クラスター内通

証明書を使用して、Livy Spark には記憶域プールでは、Spark など、ビッグ データ クラスター内の非 SQL サービスとの通信が保護されます。 すべての SQL Server と SQL Server 間の通信は、SQL ログインを使用して保護されます。

## <a name="next-steps"></a>次のステップ

SQL Server のビッグ データ クラスターに関する詳細については、次のリソースを参照してください。

- [SQL Server 2019 ビッグ データ クラスターとは](big-data-cluster-overview.md)
- [ワーク ショップ:Microsoft SQL Server のビッグ データ クラスターのアーキテクチャ](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
