---
title: コント ローラーとは何ですか。
titleSuffix: SQL Server big data clusters
description: この記事では、SQL Server 2019 ビッグ データ クラスター (プレビュー) のコント ローラーについて説明します。
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: jroth
manager: jroth
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 115809307b430a9e5079de4db71180cca4766dac
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66783171"
---
# <a name="what-is-the-controller-on-a-sql-server-big-data-cluster"></a>SQL Server のビッグ データ クラスター上のコント ローラーとは何ですか。

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

コント ローラーは、展開、およびビッグ データ クラスターを管理するためのコア ロジックをホストします。 Kubernetes では、クラスターおよび Spark、HDFS などの他のコンポーネントの一部である SQL Server インスタンスのすべての通信が処理されます。

コント ローラー サービスは、次のコア機能を提供します。

- クラスターのライフ サイクル管理: 構成を更新、削除 (&)、クラスターのブートス トラップ
- Master の SQL Server インスタンスを管理します。
- コンピューティング、データ、および記憶域プールを管理します。
- クラスターの状態を監視する監視ツールを公開します。
- トラブルシューティング ツールを検出し、予期しない問題の修復の公開します。
- クラスターのセキュリティを管理するには。
  - セキュリティで保護されたクラスター エンドポイントを確認します。
  - ユーザーとロールを管理します。
  - クラスター内通信の資格情報を構成します。

## <a name="deploying-the-controller-service"></a>コント ローラー サービスのデプロイ

コント ローラーが展開され、ビッグ データ クラスターを構築するためのユーザーが同じの Kubernetes 名前空間でホストされています。 クラスターを使用してブートス トラップ中に、Kubernetes の管理者がこのサービスがインストールされている、 **mssqlctl**コマンド ライン ユーティリティです。 詳細については、次を参照してください。[ビッグ データの SQL Server クラスターの概要](deploy-get-started.md)します。

年間のワークフローは Kubernetes の上にレイアウトで説明されているすべてのコンポーネントを含む完全に機能の SQL Server ビッグ データ クラスター、[概要](big-data-cluster-overview.md)記事。 ブートス トラップのワークフローが最初に、コント ローラー サービスを作成し、コント ローラー サービスでのインストールとマスター、コンピューティング、データ、および記憶域プールのサービスの一部の残りの部分の構成を調整はこれが配置されるとします。

## <a name="managing-the-cluster-through-the-controller-service"></a>コント ローラー サービスを使用してクラスターを管理します。

いずれかを使用してコント ローラー サービスを使用するだけで、クラスターを管理する`mssqlctl`Api や、クラスター内でホストされているクラスターの管理ポータル。 同じ名前空間にポッドのような追加の Kubernetes オブジェクトを展開する場合管理またはコント ローラー サービスの監視対象ができません。

コント ローラーとビッグ データ クラスター用に作成された、Kubernetes のオブジェクト (ステートフルのセット、ポッド、シークレットなど) は、専用の Kubernetes 名前空間に存在します。 コント ローラー サービスをその名前空間内のすべてのリソースを管理する Kubernetes クラスターの管理者によってアクセス権付与されます。  このシナリオでは、RBAC ポリシーが展開を使用して初期クラスターの一部として自動的に構成されている`mssqlctl`します。 

### <a name="mssqlctl"></a>mssqlctl

`mssqlctl` コマンド ライン ユーティリティは、クラスター管理者は、ブートス トラップし、コント ローラー サービスによって公開される REST Api を使用してビッグ データ クラスターを管理できるようにする Python で記述されます。

### <a name="cluster-administration-portal"></a>クラスターの管理ポータル

コント ローラー サービスが稼働するいると、クラスター アドミニストレーターを使用できます、[クラスター管理ポータル](cluster-admin-portal.md)デプロイの進行状況を監視するには、検出、およびクラスター内のサービスに関する問題のトラブルシューティングします。

## <a name="controller-service-security"></a>コント ローラー サービスのセキュリティ

コント ローラー サービスへのすべての通信は、HTTPS 経由で REST API 経由で行われます。 自己署名証明書は、するので自動的にブートス トラップ時に生成されます。 

コント ローラーのサービス エンドポイントへの認証は、ユーザー名とパスワードに基づきます。 これらの資格情報は、環境変数の入力を使用して、クラスターのブートス トラップ時にプロビジョニングされて`CONTROLLER_USERNAME`と`CONTROLLER_PASSWORD`します。

> [!NOTE]
> 準拠しているパスワードを指定する必要があります[SQL Server パスワードの複雑さの要件](https://docs.microsoft.com/sql/relational-databases/security/password-policy?view=sql-server-2017)します。

## <a name="next-steps"></a>次のステップ

SQL Server のビッグ データ クラスターに関する詳細については、次のリソースを参照してください。

- [SQL Server 2019 ビッグ データ クラスターとは](big-data-cluster-overview.md)
- [ワーク ショップ:Microsoft SQL Server のビッグ データ クラスターのアーキテクチャ](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
