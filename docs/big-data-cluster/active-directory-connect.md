---
title: Active Directory モードでの接続
titleSuffix: SQL Server Big Data Cluster
description: Active Directory ドメインで SQL Server ビッグ データ クラスターに接続する方法について説明します。
author: cloudmelon
ms.author: melqin
ms.reviewer: mikeray
ms.date: 09/30/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: bd8da3642d0a650ea10c54b7ed8e46a54fba2971
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2020
ms.locfileid: "91898744"
---
# <a name="connect-big-data-clusters-2019-active-directory-mode"></a>[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]SQL Server ビッグ データ クラスターを接続する: Active Directory モード

この記事では、Active Directory モードでデプロイされる SQL Server ビッグ データ クラスターのエンドポイントに接続する方法ついて説明します。 この記事のタスクでは、Active Directory モードでデプロイされる SQL Server ビッグ データ クラスターが必要です。 クラスターがない場合は、「Active Directory モードで [[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]SQL Server ビッグ データ クラスターをデプロイする](active-directory-deploy.md)」を参照してください。

## <a name="overview"></a>概要

AD Auth を使用して SQL Server マスター インスタンスにログインします。

SQL Server インスタンスへの AD 接続を確認するには、`sqlcmd` を使用して SQL マスター インスタンスに接続します。 展開時、指定されたグループに対してログインが自動的に作成されます (`clusterUsers` と `clusterAdmins`)。

Linux を使用している場合、最初に AD ユーザーとして `kinit` を実行し、次に `sqlcmd` を実行します。 Windows を使用している場合、**ドメインに参加しているクライアント コンピューター**から目的のユーザーとしてログインします。

## <a name="connect-to-master-instance-from-linuxmac"></a>Linux/Mac からマスター インスタンスに接続する

```bash
kinit <username>@<domain name>
sqlcmd -S <DNS name for master instance>,31433 -E
```

## <a name="connect-to-master-instance-from-windows"></a>Windows からマスター インスタンスに接続する

```cmd
sqlcmd -S <DNS name for master instance>,31433 -E
```

## <a name="log-in-to-sql-server-master-instance-using-azure-data-studio-or-ssms"></a>Azure Data Studio または SSMS を使用し、SQL Server マスター インスタンスにログインする

ドメインに参加しているクライアントから、SSMS または Azure Data Studio を開き、マスター インスタンスに接続できます。 これは、AD 認証を使用して SQL Server インスタンスに接続する場合と同じです。

SSMS から:

![SSMS での SQL Server への接続に関するダイアログ](./media/deploy-active-directory/image23.png)

Azure Data Studio から:

![Azure Data Studio での SQL Server への接続に関するダイアログ](./media/deploy-active-directory/image24.png)}

## <a name="log-in-to-controller-with-ad-authentication"></a>AD 認証を使用してコントローラーにログインする

### <a name="connect-to-controller-with-ad-authentication-from-linuxmac"></a>Linux/Mac から AD 認証を使用してコントローラーに接続する

`azdata` と AD 認証を使用し、コントローラー エンドポイントに接続するために、2 つのオプションがあります。 *--endpoint/-e* パラメーターを使用できます。

```bash
kinit <username>@<domain name>
azdata login -e https://<controller DNS name>:30080 --auth ad
```

または、 *--namespace/-n* パラメーター (ビッグ データ クラスター名) を使用して接続することもできます。

```bash
kinit <username>@<domain name>
azdata login -n <clusterName> --auth ad
```

### <a name="connect-to-controller-with-ad-authentication-from-windows"></a>Windows から AD 認証を使用してコントローラーに接続する

```cmd
azdata login -e https://<controller DNS name>:30080 --auth ad
```

## <a name="use-ad-authentication-to-knox-gateway-webhdfs"></a>Knox ゲートウェイ (webHDFS) に AD 認証を使用する

Knox ゲートウェイ エンドポイント経由で curl を使用して HDFS コマンドを発行することもできます。 これには Knox の AD 認証が必要です。 次の curl コマンドでは、Knox ゲートウェイを介して webHDFS REST 呼び出しが発行され、`products` という名前のディレクトリが作成されます。

```bash
curl -k -v --negotiate -u : https://<Gateway DNS name>:30443/gateway/default/webhdfs/v1/products?op=MKDIRS -X PUT
```

## <a name="next-steps"></a>次のステップ

[SQL Server ビッグ データ クラスターの Active Directory 統合のトラブルシューティング](troubleshoot-active-directory.md)

[概念: Active Directory モードで [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] をデプロイする](active-directory-deployment-background.md)
