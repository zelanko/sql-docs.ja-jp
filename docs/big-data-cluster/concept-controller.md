---
title: コントローラーとは何ですか。
titleSuffix: SQL Server big data clusters
description: この記事では、SQL Server 2019 ビッグデータクラスター (プレビュー) のコントローラーについて説明します。
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e984c3dced4bde713ac98d67c22481e54491cd68
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419538"
---
# <a name="what-is-the-controller-on-a-sql-server-big-data-cluster"></a>SQL Server ビッグデータクラスターのコントローラーとは

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

このコントローラーは、ビッグデータクラスターをデプロイおよび管理するためのコアロジックをホストします。 Kubernetes、クラスターの一部である SQL Server インスタンス、および HDFS や Spark などのその他のコンポーネントとのすべてのやり取りを処理します。

コントローラーサービスは、次のコア機能を提供します。

- クラスターのライフサイクルの管理: クラスターブートストラップ & 削除、構成の更新
- Master SQL Server インスタンスの管理
- コンピューティング、データ、および記憶域プールの管理
- 監視ツールを公開してクラスターの状態を観察する
- 予期しない問題を検出して修復するためのトラブルシューティングツールを公開する
- クラスターのセキュリティを管理する:
  - セキュリティで保護されたクラスターエンドポイントを確保する
  - ユーザーとロールの管理
  - クラスター内通信用の資格情報を構成する

## <a name="deploying-the-controller-service"></a>コントローラーサービスのデプロイ

このコントローラーは、お客様がビッグデータクラスターを構築する場合と同じ Kubernetes 名前空間でデプロイおよびホストされます。 このサービスは、クラスターのブートストラップ中に、 **azdata**コマンドラインユーティリティを使用して Kubernetes 管理者によってインストールされます。 詳細については、「 [SQL Server ビッグデータクラスターの概要](deploy-get-started.md)」を参照してください。

ビルドアウトワークフローは、[概要](big-data-cluster-overview.md)に関する記事で説明されているすべてのコンポーネントを含むビッグデータクラスター SQL Server、完全に機能する Kubernetes 上にレイアウトします。 ブートストラップワークフローはまずコントローラーサービスを作成します。これがデプロイされると、コントローラーサービスは、マスター、コンピューティング、データ、および記憶域プールの残りのサービス部分のインストールと構成を調整します。

## <a name="managing-the-cluster-through-the-controller-service"></a>コントローラーサービスを使用したクラスターの管理

**Azdata**コマンドを使用して、コントローラーサービスを介してクラスターを管理できます。 ポッドのような追加の Kubernetes オブジェクトを同じ名前空間にデプロイすると、コントローラーサービスによって管理または監視されません。 **Kubectl**コマンドを使用して、Kubernetes レベルでクラスターを管理することもできます。 詳細については、「 [SQL Server ビッグデータクラスターの監視とトラブルシューティング](cluster-troubleshooting-commands.md)」を参照してください。

ビッグデータクラスター用に作成されたコントローラーと Kubernetes オブジェクト (ステートフルセット、ポッド、シークレットなど) は、専用の Kubernetes 名前空間に存在します。 コントローラーサービスには、その名前空間内のすべてのリソースを管理するために、Kubernetes クラスター管理者によってアクセス許可が付与されます。  このシナリオの RBAC ポリシーは、 **azdata**を使用した初期クラスターデプロイの一部として自動的に構成されます。

### <a name="azdata"></a>azdata

**azdata**は Python で記述されたコマンドラインユーティリティです。これを使用すると、クラスター管理者は、コントローラーサービスによって公開されている REST api を使用して、ビッグデータクラスターをブートストラップして管理することができます。

## <a name="controller-service-security"></a>コントローラーサービスのセキュリティ

コントローラーサービスへのすべての通信は、HTTPS 経由の REST API を介して行われます。 自己署名証明書は、ブートストラップ時に自動的に生成されます。 

コントローラーサービスエンドポイントへの認証は、ユーザー名とパスワードに基づいています。 これらの資格情報は、環境変数`CONTROLLER_USERNAME`および`CONTROLLER_PASSWORD`の入力を使用して、クラスターのブートストラップ時にプロビジョニングされます。

> [!NOTE]
> [SQL Server パスワードの複雑さの要件](https://docs.microsoft.com/sql/relational-databases/security/password-policy?view=sql-server-2017)に準拠しているパスワードを指定する必要があります。

## <a name="next-steps"></a>次の手順

SQL Server ビッグデータクラスターの詳細については、次のリソースを参照してください。

- [SQL Server 2019 ビッグデータクラスターとは何ですか。](big-data-cluster-overview.md)
- [ワークショップビッグデータクラスターのアーキテクチャの Microsoft SQL Server](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
