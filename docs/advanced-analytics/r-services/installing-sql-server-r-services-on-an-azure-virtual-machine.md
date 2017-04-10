---
title: "Azure の仮想マシンに SQL Server R サービスをインストールします。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/07/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c3c223b8-75c4-412e-a319-d57ecf6533af
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 8
---
# Azure の仮想マシンに SQL Server R サービスをインストールします。
 
含む Azure の仮想マシンを展開する場合 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], 、VM が作成されるときに、インスタンスに追加する機能として R サービスを選択するようになりました。 



+ [新しい VM を作成する SQL Server 2016 と R サービス](#new)
+ [R のサービスを SQL Server 2016 で既存のバーチャル マシンに追加します。](#existing)

## <a name="a-namenewacreate-a-new-sql-server-2016-enterprise-virtual-machine-with-r-services-enabled"></a><a name="new"></a>R サービスを有効にすることで新しい SQL Server 2016 エンタープライズ仮想マシンを作成します。

1. Azure ポータルで仮想マシンをクリックし、[新規] をクリックします。
2. SQL Server 2016 Enterprise Edition を選択します。
3. サーバー名とアカウントのアクセス許可を構成し、料金プランを選択します。
4. セットアップ ウィザード、[VM の手順 4 で **SQL Server の設定**, 、検索 **R サービス (高度な分析機能)** ] をクリック **を有効にする**です。
5. 検証をクリックして表示される概要を確認 **OK**します。
6. 仮想マシンの準備ができたらに接続してがプレインストールされている SQL Server Management Studio を開きます。 R のサービスを実行する準備ができました。 
7. これを確認するには、新しいクエリ ウィンドウを開くし、R を使用して、1 から 10 に数値のシーケンスを生成する、次のような単純なステートメントを実行します。
   ```
    execute sp_execute_external_script
    @language = N'R'
    , @script = N' OutputDataSet <- as.data.frame(seq(1, 10, ));'
    , @input_data_1 = N'   ;'
    WITH RESULT SETS (([Sequence] int NOT NULL));
   ```
6. リモート データ サイエンスのクライアントからのインスタンスに接続されますが場合、は、完了 [追加の手順](#additional-steps) に応じて。


## <a name="additional-steps"></a>その他の手順  

R サービスを使用してリモートの SQL Server のコンピューティングのコンテキストとしてサーバーにアクセスするリモート クライアントが予想される場合に必要な追加の手順です。

### <a name="a-namefirewallaunblock-the-firewall"></a><a name="firewall"></a>ファイアウォールのブロックを解除します。  
  
アクセスできるようにする仮想マシン上のファイアウォール規則を変更する必要があります、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リモート データ サイエンスのクライアントからのインスタンス。  それ以外の場合、計算を必要とするコンテキストをバーチャル マシンのワークスペースの使用をできません。 

既定では、Azure の仮想マシン上のファイアウォールには、ネットワークのローカルの R ユーザー アカウントのアクセスをブロックするルールが含まれています。  
  
リモート データ サイエンスのクライアントから R サービスへのアクセスを有効にします。
1. 仮想マシンでは、セキュリティが強化された Windows ファイアウォールを開きます。
2. 選択 **送信の規則**
3. 次のルールを無効にします。  
  
     `Block network access for R local user accounts in SQL Server instance MSSQLSERVER`  
  
### <a name="enable-odbc-callbacks-for-remote-clients"></a>リモート クライアントの ODBC のコールバックを有効にします。

サーバーを呼び出す R クライアントは、R ソリューションの一部として ODBC クエリを発行する必要があることを期待する場合は、スタート パッドがリモート クライアントの代理として ODBC 呼び出しを行うことがあることを確認する必要があります。 これを行うには、インスタンスにログインするスタート パッドで使用される SQL ワーカー アカウントを許可する必要があります。
詳細については、次を参照してください。 [SQL Server R サービス設定](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)します。 

### <a name="a-namenetworkaadd-network-protocols"></a><a name="network"></a>ネットワーク プロトコルを追加します。  
  
+ 名前付きパイプを有効にします。
  
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] クライアントとサーバーのコンピューター間の接続、およびいくつかの内部接続は、名前付きパイプ プロトコルを使用します。 名前付きパイプが有効でない場合は、インストールして有効にして、サーバーに接続するすべてのデータ サイエンス クライアント両方の Azure の仮想マシンに必要があります。  
  
+ TCP/IP を有効にします。

  TCP/IP は、SQL Server の R のサービスへのループバック接続に必要です。 次のエラーが発生した場合、DBNETLIB; のインスタンスがサポートされるバーチャル マシンで TCP/IP を有効にします。SQL Server が存在しないか、アクセスが拒否されました。

## <a name="how-to-disable-r-services-on-an-instance"></a>インスタンス上の R のサービスを無効にする方法

有効にしたり、既存のバーチャル マシンでこの機能をいつでも無効にできます。 

1. 仮想マシンのブレードを開きます
2. クリックして **設定**, を選択し、 **SQL Server の構成**します。


## <a name="a-nameexistingaadd-sql-server-r-services-to-an-existing-sql-server-2016-enterprise-virtual-machine"></a><a name="existing"></a>既存の SQL Server 2016 Enterprise バーチャル マシンに SQL Server の R のサービスを追加します。

R のサービスが含まれていませんが、SQL Server 2016 で Azure VM を作成する場合は、次の手順に従って、機能を追加できます。

1. 再実行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップし、の機能を追加、 **サーバー構成** ウィザードのページです。
2. 外部スクリプトの実行を有効化し、再起動、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス。 詳細については、次を参照してください。 を参照してください [SQL Server R サービス設定](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)します。
3. (省略可能)リモート スクリプトの実行に必要な場合は、R 作業者のアカウントのデータベースへのアクセスを構成します。
   詳細については、次を参照してください。 [SQL Server R サービス設定](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)します。 
3. (省略可能)リモート データ サイエンスのクライアントから R スクリプトの実行を許可する場合は、Azure の仮想マシン上のファイアウォール規則を変更します。 詳細については、次を参照してください。 [ファイアウォールのブロックを解除](#firewall)します。
4. インストールまたは必要なネットワーク ライブラリを有効にします。 詳細については、次を参照してください。 [ネットワーク プロトコルを追加して](#network)します。

## <a name="see-also"></a>参照
[Sql Server R サービスをセットアップします。](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)