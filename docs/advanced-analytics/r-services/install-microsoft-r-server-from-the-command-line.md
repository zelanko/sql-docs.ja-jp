---
title: "コマンドラインから Microsoft R Server をインストールする | Microsoft Docs"
ms.custom: ""
ms.date: "01/19/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb4446ba-e9ce-4b93-9854-5e8a58507da0
caps.latest.revision: 4
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 3
---
# コマンドラインから Microsoft R Server をインストールする
    
SQL Server のセットアップで提供されるスクリプト機能を使用すると、コマンドラインから Microsoft R Server をインストールできます。 

- **無人**インストールでは、セットアップ ユーティリティの場所を指定し、インストールする機能を示す引数を使用する必要があります。 
- **Quiet** インストールの場合、同じ引数を渡し、**/q** スイッチを追加します。 プロンプトは表示されず、操作の必要もありません。 ただし、必要な引数が省略されている場合、セットアップは失敗します。

詳細については、「 [コマンド プロンプトからの SQL Server 2016 のインストール](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)」を参照してください。

## <a name="perform-a-commandline-install-of-microsoft-r-server-standalone"></a>Microsoft R Server (スタンドアロン) のコマンドライン インストールの実行

 次の例では、SQL Server のセットアップを使用して、コマンドラインから Microsoft R Server をインストールする場合に使用する引数を示します。


### <a name="example-of-unattended-installation-of-r-server-standalone"></a>スタンドアロンの R Server の無人インストールの例

管理者特権で次のコマンドをコマンド プロンプトより実行し、Microsoft R Server (スタンドアロン) とその前提条件のみをインストールします。 

```  
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR /IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS 
```  

進行状況とプロンプトを表示するには、/q 引数を削除します。

次のすべての引数が必要なことに注意してください。
  - **FEATURES = SQL_SHARED_MR** では、Microsoft R Open とすべての前提条件を含む Microsoft R Server のコンポーネントのみが取得されます。
  - **IACCEPTROPENLICENSETERMS** は、オープン ソースの R コンポーネントを使用するライセンス条項を承諾したことを意味します。
  - **IACCEPTSQLSERVERLICENSETERMS** はセットアップ ウィザードの実行に必要です。


### <a name="offline-installation"></a>オフライン インストール

インターネット アクセスがないコンピューターから Microsoft R Server (スタンドアロン) をインストールする場合、事前に必要な R のコンポーネントをダウンロードして、ローカル フォルダーにコピーしておく必要があります。 ダウンロード場所については、「[インターネットへのアクセスなしで R コンポーネントをインストールする](../../advanced-analytics/r-services/installing-r-components-without-internet-access.md)」を参照してください。   


## <a name="advanced-installation-tips"></a>インストールに関する詳細なヒント

セットアップが完了したら、SQL Server のセットアップで作成された構成ファイルを、セットアップ処理の概要と共に確認できます。

既定で、SQL Server と関連機能のすべてのセットアップ ログと概要は、`C:\Program Files\Microsoft SQL Server\140\Setup Bootstrap\Log` に作成されます。

インストールされる機能ごとに個別にサブフォルダーが作成されます。 Microsoft R Server では、次を探してください。 
- `RSetup.log`
- `Settings.xml`
- `Summmary<instance_GUID>.txt`

同じパラメーターをして Microsoft R Server のインスタンスをもう 1 つセットアップする場合、インストール時に作成された構成ファイルを再利用できます。 詳細については、「[構成ファイルを使用した SQL Server 2016 のインストール](https://msdn.microsoft.com/library/dd239405.aspx)」を参照してください。



### <a name="customizing-your-r-environment"></a>R 環境のカスタマイズ

インストール後、さらに R パッケージをインストールできます。 詳細については、「[Installing and Managing R Packages](../../advanced-analytics/r-services/installing-and-managing-r-packages.md)」 (R パッケージのインストールおよび管理) を参照してください。

> [!IMPORTANT]
> SQL Server 上で R コードを実行する場合、Microsoft R Server を実行するクライアント コンピューターと R サービスを実行する SQL Server インスタンスの両方に同じパッケージを必ずインストールするようにしてください。 



## <a name="see-also"></a>参照  

[Microsoft R Server](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)
  