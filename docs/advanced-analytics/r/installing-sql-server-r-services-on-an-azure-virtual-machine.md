---
title: "Azure 仮想マシンに SQL Server R Services をインストールする | Microsoft Docs"
ms.custom: 
ms.date: 07/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3c223b8-75c4-412e-a319-d57ecf6533af
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e673268b1f6b56890f22576d293135b2675ed4ab
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="installing-sql-server-r-services-on-an-azure-virtual-machine"></a>Azure 仮想マシンに SQL Server R Services をインストールする
 
含む Azure の仮想マシンを展開する場合[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]VM が作成されるときに、インスタンスに追加する機能として機械学習に選択できます。

+ [ SQL Server 2016 と R Services を含んだ新しい VM を作成する](#new)
+ [SQL Server 2016 を含んだ既存の仮想マシンに R Services を追加する](#existing)

## <a name="new"></a>R Services が有効化された新しい SQL Server 2016 エンタープライズ仮想マシンを作成する

1. Azure ポータルで、仮想マシンをクリックし、[新規] をクリックします。
2. SQL Server 2016 Enterprise Edition を選択します。
3. サーバー名とアカウントのアクセス許可を構成し、料金プランを選択します。
4. VM セットアップ ウィザードの手順 4 (**SQL Server の設定**) で、**[R Services (高度な分析)]** を見つけ、**[有効]** をクリックします。
5. 検証用に表示された概要を確認し、**[OK]** をクリックします。
6. 仮想マシンの準備ができたら、そのマシンに接続し、プレインストールされている SQL Server Management Studio を開きます。 これで、R Services を実行できる状態になります。
7. これを確認するには、新しいクエリ ウィンドウを開き、次のような簡単なステートメントを実行します。このステートメントは、R を使用して 1 から 10 までの数値のシーケンスを生成するものです。
   ```
    execute sp_execute_external_script
    @language = N'R'
    , @script = N' OutputDataSet <- as.data.frame(seq(1, 10, ));'
    , @input_data_1 = N'   ;'
    WITH RESULT SETS (([Sequence] int NOT NULL));
   ```
6. リモートのデータ サイエンス クライアントからインスタンスに接続する場合は、必要に応じて[追加の手順](#additional-steps)を完了してください。


## <a name="additional-steps"></a>追加の手順  

リモート SQL Server のコンピューティング コンテキストとしてサーバーにアクセスするリモート クライアントの場合、追加の手順が必要です。

### <a name="firewall"></a>ファイアウォールのブロックを解除する

既定では、Azure 仮想マシン上のファイアウォールには、ローカルの R ユーザー アカウントのネットワーク アクセスをブロックする規則が含まれています。

アクセスできることを保証するには、このルールを無効にする必要があります、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]リモート データ サイエンス クライアントからのインスタンス。  それ以外の場合、R コードは、他の R コードの問題もなく、SQL Server のコンピューティング コンテキストを使用する場合でも、仮想マシンのワークスペースを使用する計算コンテキストで実行できません。

リモートのデータ サイエンス クライアントから R Services へのアクセスを有効にするには、次の手順に従います。

1. 仮想マシン で、[セキュリティが強化された Windows ファイアウォール] を開きます。
2. **[送信の規則]** を選択します
3. 次の規則を無効にします。
  
     `Block network access for R local user accounts in SQL Server instance MSSQLSERVER`
  
### <a name="enable-odbc-callbacks-for-remote-clients"></a>リモート クライアントの ODBC コールバックを有効にする

サーバーを呼び出す R クライアントから、R ソリューションの一部として ODBC クエリを発行する必要がある場合は、リモート クライアントの代わりにスタート パッドから ODBC 呼び出しを実行できるようにする必要があります。 これを行うには、スタート パッドによって使用される SQL ワーカー アカウントがインスタンスにログインするできるようにする必要があります。
詳細については、「 [SQL Server R Services (In-Database) をセットアップする](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)」を参照してください。

### <a name="network"></a>ネットワーク プロトコルを追加する

+ 名前付きパイプを有効にする
  
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] では、クライアントとサーバー コンピューター間の接続 (および一部の内部接続) に、名前付きパイプ プロトコルが使用されます。 名前付きパイプが有効になっていない場合は、Azure 仮想マシンと、サーバーに接続するデータ サイエンス クライアントの両方に名前付きパイプをインストールし、有効化する必要があります。
  
+ TCP/IP を有効にする

  TCP/IP は、SQL Server R Services へのループバック接続に必要です。 次のエラーが発生した場合は、インスタンスをサポートする仮想マシンで TCP/IP を有効にします。

  "DBNETLIB です。SQL Server が存在しないかアクセスが拒否されました"

## <a name="how-to-disable-r-services-on-an-instance"></a>インスタンス上の R Services を無効にする方法

既存の仮想マシンの機能は、いつでも有効にしたり、無効にすることができます。

1. 仮想マシンのブレードを開きます
2. **[設定]** をクリックし、**[SQL Server の構成]** を選択します。

## <a name="existing"></a>既存の SQL Server 2016 Enterprise バーチャル マシンに SQL Server R Services を追加します。

R Services が含まれていません Azure の仮想マシンを作成した場合は、次の手順で、機能を追加できます。

1. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを再実行し、ウィザードの **[サーバーの構成]** ページで機能を追加します。
2. 外部スクリプトの実行を有効化し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを再起動します。 詳細については、「 [SQL Server R Services (In-Database) をセットアップする](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)」を参照してください。
3. (省略可能) R ワーカー アカウントのデータベースへのアクセスを構成します (リモート スクリプトの実行に必要な場合)。
   詳細については、「 [SQL Server R Services (In-Database) をセットアップする](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)」を参照してください。
3. (省略可能) Azure 仮想マシンでファイアウォール規則を変更します (リモートのデータ サイエンス クライアントから R スクリプトを実行できるようにする場合)。 詳しくは、「[ファイアウォールのブロックを解除する](#firewall)」をご覧ください。
4. 必要なネットワーク ライブラリをインストールまたは有効化します。 詳しくは、「[ネットワーク プロトコルを追加する](#network)」をご覧ください。

## <a name="related-resources"></a>関連リソース

[SQL Server R Services をセットアップする](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)

