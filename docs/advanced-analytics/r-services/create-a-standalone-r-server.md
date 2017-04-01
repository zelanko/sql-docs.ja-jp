---
title: "スタンドアロン R Server の作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 408e2503-5c7d-4ec4-9d3d-bba5a8c7661d
caps.latest.revision: 35
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 27
---
# スタンドアロン R Server の作成
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップには、**Microsoft R Server (スタンドアロン)** をインストールするためのオプションが含まれています。 このオプションでは、任意のデータベースまたはデータ ソースに接続しながら Windows 上でパフォーマンスの高い R ソリューションを開発することができます。 Microsoft R Server は Enterprise Edition でのみ使用できます。  
  
 Microsoft R Server をインストールすると、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] で提供されているのと同じ強化された R パッケージおよび接続ツールを取得できますが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスは必要なく、また R スクリプトはデータベースではなく、スタンドアロン コンピューターで実行されます。  
  
> [!NOTE]  
>  Microsoft R Server はまた、[モダン ライフサイクル](https://support.microsoft.com/help/447912) ポリシーのインスタンスが登録される簡素化されたセットアップを介して利用できるようになりました。 このサポート サービスにより、常に最新バージョンの R を使用できるようになります。簡素化されたセットアップの使用方法の詳細については、[「Run Microsoft R Server for Windows」](https://msdnstage.redmond.corp.microsoft.com/microsoft-r/rserver-install-windows?branch=r-server-nov16-dev) (Microsoft R Server for Windows を実行する) を参照してください。
>  
> 簡略化されたセットアップを使用して Microsoft R Server をインストールする場合は、新しいサポート ポリシーを使用して R コンポーネントの更新プログラムをより頻繁に取得できるように、R Services の任意の指定インスタンスを変換することもできます。詳細については、[「Use sqlBindR.exe to upgrade an instance of R Services」](http://www.bing.com) (sqlBindR.exe を使用して R Services のインスタンスをアップグレードする) を参照してください。   
  
##  <a name="a-namebkmkinstallrservicesindatabasea-install-microsoft-r-server-standalone"></a><a name="bkmk_installRServicesInDatabase"></a>Microsoft R Server (スタンドアロン) のインストール  
  
1.  Microsoft R Server の以前のバージョンがインストールされている場合は、最初にアンインストールする必要があります。  [「Microsoft R Server の以前のバージョンからのアップグレード」](#bkmk_Uninstall) を参照してください。 

2. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを実行します。  
  
2.  **[インストール]** タブで、 **[New R Server (Standalone) installation]** (新しい R Server (スタンドアロン) のインストール) をクリックします。  
  
     ![Setup option for R Server Standalone](../../advanced-analytics/r-services/media/rsql-rstandalonesetup.png "Setup option for R Server Standalone")  
  
3.  **[機能の選択]** ページで、次のオプションが既に選択されています。  
  
    -   **R Server (スタンドアロン)**  
  
         このオプションを選択すると、オープン ソースの R ツールと基本パッケージを含む共有機能と、Microsoft R によって提供される強化された R パッケージおよび接続ツールがインストールされます。  
  
     その他のすべてのオプションは無視できます。  
  
4.  Microsoft R Open のダウンロードとインストールに関するライセンス条項に同意します。 [**同意する**] ボタンが使用できない状態になっている場合は、[**次へ**] をクリックします。 これらのコンポーネント (および、そのコンポーネントに必要なすべての前提条件) のインストールには時間がかかる場合があります。   
  
5.  [**インストールの準備完了**] ページで、選択内容を確認し、[**インストール**] をクリックします。  
  
> [!TIP]
> 自動またはオフラインでのインストールの詳細については、[「コマンドラインから Microsoft R Server をインストールする」](../../advanced-analytics/r-services/install-microsoft-r-server-from-the-command-line.md) を参照してください。

  
## <a name="what-is-installed-and-where-to-find-r-packages"></a>インストールされる内容と R パッケージの置かれる場所  
 Microsoft R Server には、基本的な R パッケージおよび一連の強化された R パッケージが含まれ、並列処理、パフォーマンスの向上、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] や Hadoop などのデータ ソースへの接続がサポートされます。  
  
-   **R パッケージ**  
  
     R ライブラリは、Microsoft SQL Server 2016 でインストールされるその他のツールやユーティリティと一緒にインストールされます。 例:  
  
     `C:\Program Files\Microsoft SQL Server\130\R_SERVER`  
  
     さらに、このフォルダーには、基本的な R パッケージに関するドキュメント、サンプル データ、R ツールとランタイムに関するドキュメントもあります。  
  
    > [!NOTE]  
    >  SQL Server のインスタンスと R Services (データベース内) を同じコンピューターにインストールしている場合、R ライブラリおよびツールは別のフォルダーにインストールされます。`C:\Program Files\Microsoft SQL Server\<instance_name>\R_SERVICES`  
    >   
    >  [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インスタンスに関連付けられた R パッケージまたはユーティリティは使用しないでください。 必ず R_SERVER フォルダー内の R ツールおよびパッケージを使用してください。  
  
-   **R ツール**  
  
     R の開発 IDE は、セットアップの段階でインストールされません。 RStudio や [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] など任意の開発環境をインストールできます。  
  
     また、追加のツールは必要ありません。 `C:\Program Files\Microsoft SQL Server\130\R_SERVER\bin` には、標準的な基本 R ツールがすべて含まれています。  
  
     詳細については、[「Setup or Configure R Tools」](../../advanced-analytics/r-services/setup-or-configure-r-tools.md) (R ツールのセットアップまたは構成) を参照してください。  


 
## <a name="troubleshooting"></a>トラブルシューティング  

### <a name="incompatible-version-of-r-client-and-r-server"></a>R Client および R Server の互換性のないバージョン

インストールした最新バージョンの Microsoft R Client を使用し、SQL Server でリモート コンピューティング コンテキストを用いて R を実行すると、以下のようなエラーが発生する場合があります。

*Microsoft R Server バージョン 8.0.3 と互換性のない、バージョン 9.0.0 の Microsoft R Client をコンピューター上で実行しています。互換性のあるバージョンをダウンロードしてインストールしてください。*

通常、サービス リリースの公開時に、SQL Server R Services と共にインストールされる R のバージョンが更新されます。 常に最新バージョンの R コンポーネントを使用するためには、サービス パックをすべてインストールします。 Microsoft R Client 9.0.0 との互換性を維持するには、この[サポート記事](https://support.microsoft.com/kb/3210262)で説明されている更新プログラムをインストールする必要があります。 


### <a name="installing-microsoft-r-server-on-an-instance-of-sql-server-installed-on-windows-core"></a>Windows Core にインストールされた SQL Server のインスタンスへの Microsoft R Server のインストール
SQL Server 2016 のリリース バージョンでは、Windows Server Core エディションのインスタンスに Microsoft R Server を追加するときに問題が発生することがわかっていました。 この問題は修正されています。 

この問題が発生する場合は、[KB3164398](https://support.microsoft.com/kb/3164398) に記載の修正プログラムを適用して、Windows Server Core の既存のインスタンスに R 機能を追加してください。   詳細については、[「Can't install Microsoft R Server Standalone on a Windows Server Core operating system」](https://support.microsoft.com/kb/3168691) (Windows Server Core オペレーティング システムに Microsoft R Server (スタンドアロン) をインストールすることはできません) を参照してください。


###  <a name="a-namebkmkuninstalla-upgrading-from-an-older-version-of-microsoft-r-server"></a><a name="bkmk_Uninstall"></a>Microsoft R Server の以前のバージョンからのアップグレード  
 Microsoft R Server のプレリリース版がインストールされている場合は、それをアンインストールしてから新しいバージョンにアップグレードする必要があります。  
  
**R Server (スタンドアロン) をアンインストールするには**  
  
1.  [**コントロール パネル**] を開き、[**プログラムの追加と削除**] をクリックし、`Microsoft SQL Server 2016 <version number>` を選択します。  
  
2.  コンポーネントに対する [**追加**]、[**修復**]、または [**削除**] オプションを含むダイアログ ボックスが表示されたら、[**削除**] を選択します。  
  
3.  [**機能の選択**] ページの [**共有機能**] で [**R Server (スタンドアロン)**] を選択します。 [**次へ**] をクリックし、[**完了**] をクリックして、選択したコンポーネントのみをアンインストールします。  
   
### <a name="installation-fails-with-error-only-one-revolution-enterprise-product-can-be-installed-at-a-time"></a>インストールに失敗し "Revolution Enterprise 製品は一度に 1 つしかインストールできません" というエラーが表示される  
このエラーは、以前の Revolution Analytics 製品またはプレリリース版の SQL Server R Services がインストールされている場合に発生する可能性があります。 以前のバージョンが存在する場合は、そのアンインストールを行ってから、Microsoft R Server の新しいバージョンをインストールしてください。 他のバージョンの Revolution Enterprise ツールとのサイド バイ サイド インストールはサポートされていません。  

ただし、サイド バイ サイド インストールは、R Server (スタンドアロン) を次の環境とともに使用する場合はサポートされます: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] および 
  
### <a name="unable-to-uninstall-older-components"></a>以前のコンポーネントをアンインストールできない   
  
以前のバージョンの削除時に問題が発生する場合は、レジストリを編集して関連するキーを削除することが必要な場合があります。  

> [!IMPORTANT]
> この問題は、プレリリース版の Microsoft R Server または CTP バージョンの SQL Server 2016 R Services がインストールされている場合にのみ発生します。
  
1. Windows レジストリを開き、`HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall` キーを見つけます。  
2. 次のエントリのいずれかが存在し、キーに値 `sEstimatedSize2` のみが含まれる場合は、該当するエントリを削除します。  
  
    -   E0B2C29E-B8FC-490B-A043-2CAE75634972        (8.0.2 の場合)  
  
    -   46695879-954E-4072-9D32-1CC84D4158F4        (8.0.1 の場合)  
  
    -   2DF16DF8-A2DB-4EC6-808B-CB5A302DA91B        (8.0.0 の場合)  
  
    -   5A2A1571-B8CD-4AAF-9303-8DF463DABE5A        (7.5.0 の場合)  
  
## <a name="see-also"></a>参照  
 [Microsoft R Server](../../advanced-analytics/r-services/r-server-standalone.md)  
  
  