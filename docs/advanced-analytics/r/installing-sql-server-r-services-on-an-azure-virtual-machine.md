---
title: Azure の仮想マシンに SQL Server マシン学習機能をインストールする |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/21/2018
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ''
caps.latest.revision: ''
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: d2f0f38086c7725e14261afa9a40f29b212b748f
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2018
---
# <a name="install-sql-server-machine-learning-features-on-an-azure-virtual-machine"></a>Azure の仮想マシンの機能を学習する SQL Server コンピューターをインストールします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
 
使用することをお勧め、[データ サイエンス仮想マシン](ttps://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/provision-vm)が、SQL Server 2017 Machine Learning Services または SQL Server 2016 R サービスだけを持つ VM を実行する場合に、この記事の内容に従って、手順を実行します。

## <a name="create-a-virtual-machine-on-azure"></a>Azure で仮想マシンを作成します。

1. Azure ポータルの左側の一覧で、[クリックして**仮想マシン**] をクリックし、**追加**です。
2. SQL Server 2017 年 1 Enterprise Edition または SQL Server 2016 Enterprise Edition を検索します。
3. サーバー名とアカウントのアクセス許可を構成し、料金プランを選択します。
4. **SQL Server の設定**(VM のセットアップ ウィザードの手順 4) 検索**Machine Learning サービス (Advanced Analytics)** (または**R Services** for SQL Server 2016) をクリック**有効にする**です。
5. 検証用に表示された概要を確認し、**[OK]** をクリックします。
6. 仮想マシンの準備ができたら、そのマシンに接続し、プレインストールされている SQL Server Management Studio を開きます。 機械学習を実行する準備ができました。
7. これを確認するには、新しいクエリ ウィンドウを開き、次のような簡単なステートメントを実行します。このステートメントは、R を使用して 1 から 10 までの数値のシーケンスを生成するものです。

    ```
    EXEC sp_execute_external_script
    @language = N'R'
    , @script = N' OutputDataSet <- as.data.frame(seq(1, 10, ));'
    , @input_data_1 = N'   ;'
    WITH RESULT SETS (([Sequence] int NOT NULL));
    ```

6. リモート データ サイエンス クライアントからのインスタンスに接続する場合は、完了[追加の手順](#additional-steps)必要に応じて、します。

### <a name="disable-machine-learning-features-on-a-sql-server-vm"></a>SQL Server VM で、マシン学習機能を無効にします。

有効にするも、いつでも既存の SQL Server 仮想マシンでこの機能を無効にすることができます。

1. 仮想マシンのブレードを開きます。
2. **[設定]** をクリックし、**[SQL Server の構成]** を選択します。
3. 機能を変更して適用します。

### <a name="existing"></a>R Services、SQL Server 2016 Enterprise の既存の VM を追加します。

機械学習なしの SQL Server を含む Azure の仮想マシンを作成する場合は、次の手順で機能を追加することができます。

1. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを再実行し、ウィザードの **[サーバーの構成]** ページで機能を追加します。
2. 外部スクリプトの実行を有効化し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを再起動します。 詳細については、次を参照してください。 [SQL Server の 2016 R Services をインストール](../install/sql-r-services-windows-install.md)です。
3. (省略可能) R ワーカー アカウントのデータベースへのアクセスを構成します (リモート スクリプトの実行に必要な場合)。
4. (省略可能) Azure 仮想マシンでファイアウォール規則を変更します (リモートのデータ サイエンス クライアントから R スクリプトを実行できるようにする場合)。 詳しくは、「[ファイアウォールのブロックを解除する](#firewall)」をご覧ください。
5. 必要なネットワーク ライブラリをインストールまたは有効化します。 詳しくは、「[ネットワーク プロトコルを追加する](#network)」をご覧ください。

## <a name="additional-steps"></a>追加の手順

リモート SQL Server のコンピューティング コンテキストとしてサーバーにアクセスするリモート クライアントの場合、追加の手順が必要です。

### <a name="firewall"></a>ファイアウォールのブロックを解除する

既定では、Azure の仮想マシン上のファイアウォールには、ネットワークのローカル ユーザー アカウントのアクセスをブロックするルールが含まれます。

アクセスできることを保証するには、このルールを無効にする必要があります、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]リモート データ サイエンス クライアントからのインスタンス。  それ以外の場合、機械学習のコードは、仮想マシンのワークスペースを使用する計算コンテキストで実行できません。

リモート データ サイエンス クライアントからのアクセスを有効にします。

1. 仮想マシン で、[セキュリティが強化された Windows ファイアウォール] を開きます。
2. **[送信の規則]** を選択します
3. 次の規則を無効にします。
  
     `Block network access for R local user accounts in SQL Server instance MSSQLSERVER`
  
### <a name="enable-odbc-callbacks-for-remote-clients"></a>リモート クライアントの ODBC コールバックを有効にする

サーバーを呼び出すクライアントは、そのマシン学習ソリューションの一部として ODBC クエリを発行する必要があることを予定の場合、スタート パッドがリモート クライアントの代理として ODBC 呼び出しを実行できることを確認する必要があります。 これを行うには、スタート パッドによって使用される SQL ワーカー アカウントがインスタンスにログインするできるようにする必要があります。
詳細については、次を参照してください。 [SQL Server の 2016 R Services をインストール](../install/sql-r-services-windows-install.md)です。

### <a name="network"></a>ネットワーク プロトコルを追加する

+ 名前付きパイプを有効にする
  
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] では、クライアントとサーバー コンピューター間の接続 (および一部の内部接続) に、名前付きパイプ プロトコルが使用されます。 名前付きパイプが有効になっていない場合は、Azure 仮想マシンと、サーバーに接続するデータ サイエンス クライアントの両方に名前付きパイプをインストールし、有効化する必要があります。
  
+ TCP/IP を有効にする

  TCP/IP は、ループバック接続に必要です。 次のエラーが発生した場合は、インスタンスをサポートする仮想マシンで TCP/IP を有効にします。

  "DBNETLIB です。SQL Server が存在しないかアクセスが拒否されました"