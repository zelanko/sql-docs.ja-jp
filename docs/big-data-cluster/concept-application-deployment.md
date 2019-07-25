---
title: アプリケーションの展開とは
titleSuffix: SQL Server 2019 big data clusters
description: この記事では、SQL Server 2019 ビッグデータクラスター (プレビュー) でのアプリケーションのデプロイについて説明します。
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d8cc44862af21c54bdbd0e4adbb35db912c3f7c9
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419406"
---
# <a name="what-is-application-deployment-on-a-sql-server-2019-big-data-cluster"></a>SQL Server 2019 ビッグデータクラスターでのアプリケーションの展開とは

アプリケーションの展開では、アプリケーションを作成、管理、および実行するためのインターフェイスを提供することにより、ビッグデータクラスターでアプリケーションを展開できます。 ビッグデータクラスターに展開されたアプリケーションは、クラスターの計算機能を利用し、クラスターで使用可能なデータにアクセスできます。 これにより、データが存在するアプリケーションを管理しながら、アプリケーションのスケーラビリティとパフォーマンスが向上します。
次のセクションでは、アプリケーションの展開のアーキテクチャと機能について説明します。

## <a name="application-deployment-architecture"></a>アプリケーションの展開アーキテクチャ

アプリケーションの配置は、コントローラーとアプリのランタイムハンドラーで構成されます。 アプリケーションを作成するときに、仕様ファイル`spec.yaml`() が提供されます。 この`spec.yaml`ファイルには、アプリケーションを正常に展開するためにコントローラーが認識する必要があるすべてのものが含まれています。 の`spec.yaml`内容の例を次に示します。

```yaml
#spec.yaml
name: add-app #name of your python script
version: v1  #version of the app
runtime: Python #the language this app uses (R or Python)
src: ./add.py #full path to the location of the app
entrypoint: add #the function that will be called upon execution
replicas: 1  #number of replicas needed
poolsize: 1  #the pool size that you need your app to scale
inputs:  #input parameters that the app expects and the type
  x: int
  y: int
output: #output parameter the app expects and the type
  result: int
```

コントローラーは、 `spec.yaml`ファイル`runtime`内の指定されたを検査し、対応するランタイムハンドラーを呼び出します。 ランタイムハンドラーによってアプリケーションが作成されます。 まず、1つまたは複数のポッドを含む Kubernetes ReplicaSet が作成されます。それぞれに、デプロイするアプリケーションが含まれています。 ポッドの数は、アプリケーションの`replicas` `spec.yaml`ファイルで設定されたパラメーターによって定義されます。 各ポッドには、プールをさらに1つ含めることができます。 プールの数は、 `poolsize` `spec.yaml`ファイルのパラメーターセットによって定義されます。

これらの設定は、展開が並列で処理できる要求の量に影響を与えます。 指定された時間内の要求の最大数は`replicas` 、 `poolsize`回と同じになります。 レプリカあたり5つのレプリカと2つのプールがある場合、デプロイは10個の要求を並行して処理できます。 `replicas` と`poolsize`のグラフィック表示については、次の図を参照してください。

![Poolsize とレプリカ](media/big-data-cluster-create-apps/poolsize-vs-replicas.png)

Replicaset が作成され、ポッドが開始されると、 `schedule` `spec.yaml`ファイルでが設定されている場合、cron ジョブが作成されます。 最後に、アプリケーションの管理と実行に使用できる Kubernetes サービスが作成されます (以下を参照)。

アプリケーションを実行すると、アプリケーションの Kubernetes サービスによって、レプリカに対する要求がプロキシされ、結果が返されます。

## <a name="how-to-work-with-application-deployment"></a>アプリケーションの展開を使用する方法

アプリケーションの展開には、次の2つの主要なインターフェイスがあります。 
- [コマンドラインインターフェイス`azdata`](big-data-cluster-create-apps.md)
- [Visual Studio Code と Azure Data Studio 拡張機能](app-deployment-extension.md)

また、RESTful web サービスを使用してアプリケーションを実行することもできます。 詳細については、「[ビッグデータクラスターでのアプリケーションの使用](big-data-cluster-consume-apps.md)」を参照してください。

## <a name="next-steps"></a>次のステップ

SQL Server ビッグデータクラスターでアプリケーションを作成して実行する方法の詳細については、次を参照してください。

- [Azdata を使用してアプリケーションをデプロイする](big-data-cluster-create-apps.md)
- [アプリのデプロイ拡張機能を使用してアプリケーションをデプロイする](app-deployment-extension.md)
- [ビッグデータクラスターでのアプリケーションの使用](big-data-cluster-consume-apps.md)

SQL Server ビッグデータクラスターの詳細については、次の概要を参照してください。

- [SQL Server 2019 ビッグデータクラスターとは何ですか。](big-data-cluster-overview.md)
