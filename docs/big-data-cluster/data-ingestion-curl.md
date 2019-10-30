---
title: curl を使用して HDFS にデータを読み込む |Microsoft Docs
titleSuffix: SQL Server big data clusters
description: Curl を使用して、[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]上の HDFS にデータを読み込みます。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c65ce7fb6752240f0dd23a6dab195539146e7933
ms.sourcegitcommit: 4fb6bc7c81a692a2df706df063d36afad42816af
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "73049877"
---
# <a name="use-curl-to-load-data-into-hdfs-on-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Curl を使用して、[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] 上の HDFS にデータを読み込みます

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、 **curl**を使用して [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (プレビュー) で HDFS にデータを読み込む方法について説明します。

## <a id="prereqs"></a> Prerequisites

- [ビッグ データ クラスターにサンプル データを読み込む](tutorial-load-sample-data.md)

## <a name="obtain-the-service-external-ip"></a>サービスの外部 IP を取得する

WebHDFS は展開が完了すると開始され、そのアクセスは Knox を経由します。 Knox エンドポイントは、**gateway-svc-external** という Kubernetes サービスを介して公開されます。  ファイルをアップロードまたはダウンロードするために必要な WebHDFS URL を作成するには、**gateway-svc-external** サービスの外部 IP アドレスとビッグ データ クラスターの名前が必要です。 次のコマンドを実行して、**gateway-svc-external** サービスの外部 IP アドレスを取得できます。

```bash
kubectl get service gateway-svc-external -n <big data cluster name> -o json | jq -r .status.loadBalancer.ingress[0].ip
```

> [!NOTE]
> `<big data cluster name>` は、ここでは、展開構成ファイル内に指定したクラスターの名前です。 既定の名前は `mssql-cluster` です。

## <a name="construct-the-url-to-access-webhdfs"></a>WebHDFS にアクセスするための URL を作成する

次のように、WebHDFS にアクセスするための URL を作成できます。

`https://<gateway-svc-external service external IP address>:30443/gateway/default/webhdfs/v1/`

例 :

`https://13.66.190.205:30443/gateway/default/webhdfs/v1/`

## <a name="list-a-file"></a>ファイルの一覧表示

**Hdfs:///product_review_data**の下のファイルを一覧表示するには、次の curl コマンドを使用します。

```bash
curl -i -k -u root:root-password -X GET 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/product_review_data/?op=liststatus'
```

## <a name="put-a-local-file-into-hdfs"></a>ローカル ファイルを HDFS に配置する

新しいファイル product_review_data をローカルディレクトリからディレクトリに配置するには、次の curl コマンドを使用**します (** **content-type**パラメーターは必須です)。

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/product_review_data/test.csv?op=create' -H 'Content-Type: application/octet-stream' -T 'test.csv'
```

## <a name="create-a-directory"></a>ディレクトリを作成する

`hdfs:///` の下に **test** というディレクトリを作成するには、次のコマンドを使用します。

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/test?op=MKDIRS'
```

## <a name="next-steps"></a>次のステップ

SQL Server ビッグ データ クラスターの詳細については、「[SQL Server ビッグ データ クラスターとは](big-data-cluster-overview.md)」を参照してください。
