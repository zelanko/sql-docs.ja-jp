---
title: アプリケーションのデプロイとは何ですか。
titleSuffix: SQL Server 2019 big data clusters
description: この記事では、SQL Server 2019 ビッグ データ クラスター (プレビュー) でアプリケーションの展開について説明します。
author: jterh
ms.author: jroth
manager: jroth
ms.date: 03/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 1a6ba9caed2b01abc50e16e34d1a13413af2d0ba
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66801859"
---
# <a name="what-is-application-deployment-on-a-sql-server-2019-big-data-cluster"></a>アプリケーションの展開は、SQL Server 2019 ビッグ データ クラスター上で何ですか。

アプリケーションの展開では、作成、管理、およびアプリケーションを実行するインターフェイスを提供することでビッグ データ クラスター上でアプリケーションの展開を有効します。 ビッグ データ クラスターにデプロイされたアプリケーションは、クラスターの計算能力を活用し、クラスターで利用可能なデータにアクセスできます。 これは、スケーラビリティとデータが存在するアプリケーションを管理しながら、アプリケーションのパフォーマンスが向上します。
次のセクションでは、アーキテクチャとアプリケーションの展開の機能について説明します。

## <a name="application-deployment-architecture"></a>アプリケーション展開のアーキテクチャ

アプリケーションの展開は、コント ローラーとアプリのランタイムのハンドラーで構成されます。 アプリケーションは、仕様ファイルを作成するときに (`spec.yaml`) 提供されます。 これは、`spec.yaml`ファイルには、アプリケーションを正常に展開するために、コント ローラーが必要なすべてが含まれています。 次に、サンプルの内容の`spec.yaml`:

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

コント ローラーを検査、`runtime`で指定されている、`spec.yaml`ファイルを開き、対応するランタイムのハンドラーを呼び出します。 ランタイムのハンドラーは、アプリケーションを作成します。 最初に、展開するアプリケーションを含む 1 つまたは複数のポッドを含む Kubernetes ReplicaSet が作成されます。 ポッドの数がによって定義されている、`replicas`でパラメーターを設定、`spec.yaml`アプリケーション用のファイル。 1 つ以上のプールの各ポッドことができます。 プールの数がによって定義されている、`poolsize`でパラメーターを設定、`spec.yaml`ファイル。

これらの設定は、デプロイが並列で処理できる要求の量に影響を与えます。 1 つの特定の時点での要求の最大数は等しい`replicas`回`poolsize`します。 5 つのレプリカと 2 つのプールあたりのレプリカがある場合、展開は、並列で 10 件の要求を処理できます。 グラフィカル表現は、以下のイメージを参照してください`replicas`と`poolsize`:。

![Poolsize とレプリカ](media/big-data-cluster-create-apps/poolsize-vs-replicas.png)

Cron ジョブを作成する場合、ReplicaSet が作成され、ポッドを開始して後、`schedule`で設定された、`spec.yaml`ファイル。 最後に、Kubernetes サービスが作成されます (下記参照)、アプリケーションの実行の管理に使用できます。

アプリケーションを実行すると、アプリケーション プロキシをレプリカ、結果を返す要求の Kubernetes サービス。

## <a name="how-to-work-with-application-deployment"></a>アプリケーションの展開を操作する方法

アプリケーションの展開の 2 つのメイン インターフェイスは次のとおりです。 
- [コマンド ライン インターフェイス `mssqlctl`](big-data-cluster-create-apps.md)
- [Visual Studio Code と Azure Data Studio の拡張機能](app-deployment-extension.md)

アプリケーションが RESTful web サービスを使用して実行することもできます。 詳細については、次を参照してください。[ビッグ データ クラスター上でアプリケーションを消費する](big-data-cluster-consume-apps.md)します。

## <a name="next-steps"></a>次のステップ

作成し、ビッグ データの SQL Server クラスターでアプリケーションを実行する方法の詳細については、次を参照してください。

- [mssqlctl を使用してアプリケーションを展開する](big-data-cluster-create-apps.md)
- [アプリのデプロイの拡張機能を使用してアプリケーションをデプロイします。](app-deployment-extension.md)
- [ビッグ データ クラスター上のアプリケーションを使用します。](big-data-cluster-consume-apps.md)

SQL Server のビッグ データ クラスターに関する詳細については、次の概要を参照してください。

- [SQL Server 2019 ビッグ データ クラスターとは](big-data-cluster-overview.md)
