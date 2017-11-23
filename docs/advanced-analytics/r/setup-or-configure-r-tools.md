---
title: "SQL Server セットアップに含まれている R ツール |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/31/2017
ms.prod:
- sql-server-2016
- sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c04ae30-d391-4369-9742-d2b275e14c0d
caps.latest.revision: "9"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 37910463066855d8929d554cb7f850c410dac4a0
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="r-tools-included-with-sql-server-setup"></a>SQL Server セットアップに含まれている R のツール

いずれかでインストールされているのと同じ R ツールを取得する SQL Server で R をインストールするときに**基本**RGui、Rterm などの R のインストール。 このため実際があるすべてのツールを開発し、R コードをテストする必要があります。

このトピックでは、インストールに付属のツールを示します。

> [!TIP]
> 
> 通常のデバッグし、専用の開発環境を使用して R コードをテストする簡単です。 テストする場合は、あらかじめ外部ツールでは、詳細なエラー メッセージを読み取るしてソリューションをデバッグできるように、SQL Server で R コードを実行しやすくすることもあります。
> 
> SQL Server で動作するように構成する方法と、R ソリューションを開発に使用できる無料ツールの一覧については、この記事を参照してください:[データ サイエンス クライアントのセットアップ](set-up-a-data-science-client.md)

**適用されます:** SQL Server 2016 R Services (In-database) および Microsoft R Server (スタンドアロン) です。SQL Server 2017 機械学習の Services (In-database) と機械学習のサーバー (スタンドアロン)

## <a name="r-tools-included-with-installation"></a>R ツールのインストールに含まれています。

次の標準的な R ツールが含まれている、*基本インストール*R のし、そのため、既定でインストールされます。

+ **RTerm**: R スクリプトを実行するためのコマンド ライン ターミナル

+ **RGui.exe**:  R のための単純な対話型エディター。コマンドライン引数は RGui.exe と RTerm で同じです。

+ **RScript**: R スクリプトをバッチ モードで実行するためのコマンドライン ツール。

これらのツールを検索するには、SQL Server または機能を学習するスタンドアロンのマシンを設定するときにインストールされた R ライブラリを決定します。 たとえば、既定のインストールでは、R ツールはこれらのフォルダーにあります。

+ SQL Server 2016 R Services:`~\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64`
+ Microsoft R Server のスタンドアロン:`~\Program Files\Microsoft R\R_SERVER\bin\x64`
+ SQL Server 2017 マシン サービスを学習します。`~\Program Files\Microsoft SQL Server\MSSQL14.<instancename>\R_SERVICES\bin\x64`
+ 機械学習のサーバー (スタンドアロン)。`~\Program Files\Microsoft\ML Server\R_SERVER\bin\x64`

R ツールのヘルプを必要がある場合は、開く**RGui**をクリックして**ヘルプ**オプションのいずれかを選択します。

## <a name="introducing-microsoft-r-client"></a>Microsoft R クライアントの概要

Microsoft R クライアントは、開発用に、RevoScaleR パッケージに対するアクセスを提供する無料でダウンロードします。 R のクライアントをインストールするには、SQL Server データベース内の分析、および Hadoop、Spark、または Machine Learning のサーバーを使用して Linux 上の分散 R コンピューティングを含む、すべてのサポートされているコンピューティング コンテキストで実行できる R ソリューションを作成できます。

別の R 開発環境が既にインストールされている場合 RStudio などは、ライブラリおよび Microsoft R クライアントによって提供される実行可能ファイルを使用する環境を再構成します。 により、RevoScaleR パッケージのすべての機能を使用することができますが、パフォーマンスが制限されます。

詳細については、次を参照してください。 [Microsoft R クライアントは何ですか。](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)
