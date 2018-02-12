---
title: "R と SQL Server のエンド ツー エンドのデータ サイエンスのチュートリアル |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/22/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.assetid: edd76ae9-4125-45a8-bf42-47a85b9d9a32
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: eee99c95b17438fa810501b653a83538e658b205
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2018
---
# <a name="end-to-end-data-science-walkthrough-for-r-and-sql-server"></a>R と SQL Server のエンド ツー エンドのデータ サイエンスのチュートリアル
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このチュートリアルでは、SQL Server 2016 または SQL Server 2017 Microsoft R に基づいた予測モデリングのエンド ツー エンド ソリューションを開発します。

このチュートリアルは、よく知られている公開データ セット、ニューヨーク市タクシー データセットに基づいています。 R コードの組み合わせを使用する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ、およびカスタムの SQL 関数をドライバーが可能性があります特定タクシー旅行に関するヒントを取得する確率を示す分類モデルを作成します。 展開することも、R モデルを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サーバー データを使用してモデルに基づいたスコアを生成します。

この例は、販売キャンペーンに顧客の反応を予測することや、支出またはイベントで出席者の予測などの実際の問題のすべての種類を拡張できます。 モデルは、ストアド プロシージャから呼び出すことができます、ためには、アプリケーションで簡単に埋め込むことができます。

このチュートリアルは、開発者は R を導入する設計されているため[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]、可能な限り、R を使用します。 ただし、これはいないという R は、各タスクに最適なツールではありません。 多くの場合、特にデータ集計と機能エンジニアリングについては、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の方が優れたパフォーマンスを示す可能性があります。  このようなタスクでは、特に [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]の新機能 (メモリ最適化列ストア インデックスなど) のメリットが得られます。 その過程で可能な最適化を指摘にしようとします。

> [!NOTE]
> 本来このチュートリアルは、SQL Server 2016 用に作成し、SQL Server 2016 でテストしたものです。 ただし、スクリーン ショットや手順が更新されました、最新の SQL Server 2017 で動作する SQL Server Management Studio を使用します。

## <a name="overview"></a>概要

推定時間は、セットアップを含めないでください。 詳細については、次を参照してください。 [、チュートリアルの前提条件](../tutorials/walkthrough-prerequisites-for-data-science-walkthroughs.md)です。

|トピックの一覧|所要時間|
|-|------------------------------|
|[R のチュートリアルのデータを準備します。](../tutorials/walkthrough-prepare-the-data.md) <br /><br />モデルの構築に使用するデータを取得します。 公開されているデータセットをダウンロードして、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに読み込みます。|30 分|
|[SQL を使用してデータを探索する](../tutorials/walkthrough-view-and-explore-the-data.md) <br /><br />SQL ツールと集計を使用して、データを理解します。|10 分|
|[R を使用したデータの要約](../tutorials/walkthrough-view-and-summarize-data-using-r.md) <br /><br />R を使用して、データを調べ、サマリーを生成します。|10 分|
|[SQL Server で R を使用してプロットを作成します。](../tutorials/walkthrough-create-graphs-and-plots-using-r.md) <br /><br />R と SQL を混在させることで、ローカルおよびリモート計算コンテキストでプロットを作成します。|10 分|
|[R と T-SQL を使用してデータの機能を作成する)](../tutorials/walkthrough-create-data-features.md) <br /><br />R と [!INCLUDE[tsql](../../includes/tsql-md.md)] のカスタム関数を使用して、機能エンジニアリングを実行します。 特性付けタスクにおける R と T-SQL のパフォーマンスを比較します。 |10 分|
|[R モデルを構築し、SQL Server に保存](../tutorials/walkthrough-build-and-save-the-model.md) <br /><br />予測モデルをトレーニングして調整します。 モデルのパフォーマンスを評価します。 このチュートリアルでは、分類モデルを作成します。 また、R を使用してモデルの精度のプロットも作成します。|15 分|
|[SQL Server を使用して、R モデルを配置します。](../tutorials/walkthrough-deploy-and-use-the-model.md) <br /><br />モデルを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに保存することで、モデルを運用環境にデプロイします。 ストアド プロシージャからモデルを呼び出して、予測を生成します。|10 分|

### <a name="intended-audience"></a>想定読者

このチュートリアルは、R または SQL の開発者向けです。 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] を使用してエンタープライズ ワークフローに R を統合する方法の概要について説明します。  データベースとテーブルを作成し、データをインポートして、クエリを実行するなど、データベース操作に慣れておく必要があります。

+ すべての SQL と R スクリプトが含まれます。
+ 環境内で実行するには、スクリプト内の文字列を変更する必要があります。 これを行う任意のコード エディターなど[Visual Studio Code](https://code.visualstudio.com/Download)です。

### <a name="prerequisites"></a>前提条件

+ SQL Server 2016 のインスタンスまたは SQL Server 2017 の評価版へのアクセスが必要です。
+ SQL Server コンピューターの少なくとも 1 つのインスタンスに [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] がインストールされている必要があります。
+ ラップトップなどのリモート コンピューターまたは別のネットワーク コンピューターから R コマンドを実行する場合は、Microsoft R Open のライブラリをインストールする必要があります。 Microsoft R クライアントまたは Microsoft R Server をインストールすることができます。 リモート コンピューターに接続できる必要があります、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。
+ 同じコンピューターにクライアントとサーバーを配置する必要がある場合は、「リモート」のクライアントから R スクリプトを送信する際に使用するための Microsoft R ライブラリの別のセットをインストールすることを確認します。 使わない、R ライブラリがインストールされているが使用するため、SQL Server インスタンスでこの目的のため。

これらのサーバーとクライアントの環境を設定する方法の詳細については、次を参照してください。 [R と SQL Server のデータ サイエンスのチュートリアルの前提条件](../tutorials/walkthrough-prerequisites-for-data-science-walkthroughs.md)です。

## <a name="next-lesson"></a>次のレッスン

[R のチュートリアルのデータを準備します。](../tutorials/walkthrough-prepare-the-data.md)
