---
title: "Azure の仮想マシンに SQL Server マシン学習機能をインストールする |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/31/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3c223b8-75c4-412e-a319-d57ecf6533af
caps.latest.revision: "11"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 0c4b8ef73f4afbc54d2fc1841e281afd0342cedf
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="installing-sql-server-machine-learning-features-on-an-azure-virtual-machine"></a>Azure の仮想マシンの機能を学習する SQL Server マシンにインストール
 
含む Azure の仮想マシンを展開する場合[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]VM が作成されるときに、インスタンスに追加する機能として機械学習に選択できます。

+ [SQL Server 2016 と R Services を含む新しい仮想マシンを作成します。](#new)
+ [SQL Server 2016 の既存のバーチャル マシンに machine learning の機能を追加します。](#existing)

> [!NOTE]
> 仮想マシンでは、SQL Server 2017 に使用できるようになりました。 参照してください[このお知らせ](https://azure.microsoft.com/blog/announcing-new-azure-vm-images-sql-server-2017-on-linux-and-windows/)詳細についてはします。
> 
> R も Azure SQL Database のプレビュー機能として利用できます。 詳細については、次を参照してください。 [Azure SQL database を使用して R](../r/using-r-in-azure-sql-database.md)です。

## <a name="create-a-new-sql-server-2017-virtual-machine"></a>新しい SQL Server 2017 仮想マシンを作成します。

SQL Server 2017 の R と Python を使用してする Windows ベースのバーチャル マシンを取得することを確認します。 [!INCLUDE[sscurrentlong-md](../../includes/sscurrentlong-md.md)]linux をサポートしている高速[ネイティブ スコアリング](../sql-native-scoring.md)T-SQL で予測関数しますが、他のマシン機能の学習を使用して利用できないこのエディションでまだです。

SQL Server VM の内容の一覧は、この記事を参照してください:[概要 SQL Server の Azure Virtual Machines (Windows) で](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-iaas-overview)です。

### <a name="new"></a>機械学習で新しい SQL Server Enterprise VM を作成します。

1. Azure ポータルで、仮想マシンをクリックし、[新規] をクリックします。
2. SQL Server 2017 年 1 Enterprise Edition を選択します。
3. サーバー名とアカウントのアクセス許可を構成し、料金プランを選択します。
4. **SQL Server の設定**(VM のセットアップ ウィザードの手順 4) 検索**Machine Learning サービス (Advanced Analytics)**  をクリック**を有効にする**です。
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
2. 外部スクリプトの実行を有効化し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを再起動します。 詳細については、次を参照してください。 [SQL Server R Services セットアップ](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)です。
3. (省略可能) R ワーカー アカウントのデータベースへのアクセスを構成します (リモート スクリプトの実行に必要な場合)。
   詳細については、「 [SQL Server R Services (In-Database) をセットアップする](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)」を参照してください。
3. (省略可能) Azure 仮想マシンでファイアウォール規則を変更します (リモートのデータ サイエンス クライアントから R スクリプトを実行できるようにする場合)。 詳しくは、「[ファイアウォールのブロックを解除する](#firewall)」をご覧ください。
4. 必要なネットワーク ライブラリをインストールまたは有効化します。 詳しくは、「[ネットワーク プロトコルを追加する](#network)」をご覧ください。

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
詳細については、「 [SQL Server R Services (In-Database) をセットアップする](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)」を参照してください。

### <a name="network"></a>ネットワーク プロトコルを追加する

+ 名前付きパイプを有効にする
  
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] では、クライアントとサーバー コンピューター間の接続 (および一部の内部接続) に、名前付きパイプ プロトコルが使用されます。 名前付きパイプが有効になっていない場合は、Azure 仮想マシンと、サーバーに接続するデータ サイエンス クライアントの両方に名前付きパイプをインストールし、有効化する必要があります。
  
+ TCP/IP を有効にする

  TCP/IP は、ループバック接続に必要です。 次のエラーが発生した場合は、インスタンスをサポートする仮想マシンで TCP/IP を有効にします。

  "DBNETLIB です。SQL Server が存在しないかアクセスが拒否されました"

## <a name="related-resources"></a>関連リソース

[Azure SQL データベースでの R の使用](../r/using-r-in-azure-sql-database.md)