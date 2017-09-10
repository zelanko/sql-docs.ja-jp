---
title: "スタンドアロン R Server の作成 | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 408e2503-5c7d-4ec4-9d3d-bba5a8c7661d
caps.latest.revision: 35
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4f39a03ecf7b74e0e1305d692a71c28609c80bf0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-a-standalone-r-server"></a>スタンドアロン R Server の作成

SQL Server セットアップには、機械学習の SQL Server の外部で実行しているサーバーをインストールするオプションが含まれています。 

このオプションは、Windows では、パフォーマンスの高い R ソリューションを開発し、その他のプラットフォーム間で、ソリューションを共有する必要がある場合に便利です。 これらの実行には、リモート計算コンテキストがサポートされているは、ソリューションを構築するために環境を設定する、サーバー オプションを使用することもできます。
  
  + R Services を実行する SQL Server のインスタンス
  + Hadoop または Spark クラスターを使用した R Server のインスタンス
  + Teradata データベース内分析
  + Linux で実行している R Server 

このトピックでは、Microsoft R Server と Microsoft Machine Learning のサーバーの SQL Server セットアップのセットアップ手順を説明します。

## <a name="which-should-i-install"></a>インストールする必要がありますか。

**Microsoft R Server**が最初に SQL Server 2016 の一部として提供され、R 言語をサポートします。 Microsoft R Server の最新バージョンでは、9.0.1 はでした。
R Server の名前変更 SQL Server の 2017 **Microsoft Machine Learning Server**と Python のサポートが追加されました。 Microsoft Machine Learning のサーバーの最新バージョンは、9.1.0 です。

Microsoft R Server と Microsoft Machine Learning のサーバーの両方には、Enterprise Edition が必要があります。

+ [SQL Server セットアップを使用して Microsoft R Server (スタンドアロン) をインストールします。](#bkmk_installRServer)
+ [SQL Server セットアップを使用して Microsoft Machine Learning Server (スタンドアロン) をインストールします。](#bkmk_installRServer) 

  セットアップには SQL Server ライセンスが必要で、アップグレードは通常 SQL Server のリリース パターンと一致します。 これにより、開発ツールが SQL Server コンピューティング コンテキストで実行されているバージョンと同期します。

+ [Windows 用の R Server をインストールします。](https://msdn.microsoft.com/microsoft-r/rserver-install-windows)

  このオプションを使用して R Server がインストールされている最新のライフ サイクルのサポート ポリシーを使用します。 SQL Server 2016 のインスタンスをアップグレードするセットアップ後に、このインストーラーを実行することもできます。 現時点では、する_できません_Python のサポートは、このオプションを使用してインストールします。 Python を取得するには、Machine Learning サーバーが SQL Server 2017 セットアップを使用してをインストールする必要があります。

##  <a name="bkmk_installRServer"></a>マイクロソフトの機械学習のサーバー (スタンドアロン) をインストールする方法
  
1. Microsoft R Server の以前のバージョンをインストールした場合は、最初にアンインストールすることをお勧めします。

2. SQL Server 2017 セットアップを実行します。
  
3. クリックして、**インストール**タブをクリックし、選択**Machine Learning Server (スタンドアロン) の新規インストール**です。

4. ルールのチェックが完了したら、SQL Server のライセンス条項に同意し、新規インストールを選択します。

5. **機能の選択**ページで、次のオプションが既に選択してください。
    
    - マイクロソフトの機械学習のサーバー (スタンドアロン)
    
    - R と Python 既定で選択します。
    
    その他のオプションはすべて無視します。

6.  ダウンロードし、機械学習のコンポーネントをインストールするためのライセンス条項に同意します。 別のライセンス契約は、Microsoft R オープンおよび Python の必要があります。 
    
    [ **同意する** ] ボタンが使用できない状態になっている場合は、[ **次へ**] をクリックします。 
    
    これらのコンポーネント (および、そのコンポーネントに必要なすべての前提条件) のインストールには時間がかかる場合があります。 
    
    コンピューターがインターネットにアクセスできる、事前にコンポーネントのインストーラーをダウンロードする必要があります。 詳細については、次を参照してください。[インターネットにアクセスできないインストール ML コンポーネント](./installing-ml-components-without-internet-access.md)です。 
    
7.  [ **インストールの準備完了** ] ページで、選択内容を確認し、[ **インストール**] をクリックします。


自動またはオフラインでのインストールの詳細については、 [「コマンドラインから Microsoft R Server をインストールする」](../../advanced-analytics/r-services/install-microsoft-r-server-from-the-command-line.md)を参照してください。

###  <a name="bkmk_installRServer"></a> Microsoft R Server (スタンドアロン) のインストール  

1. Microsoft R Server の以前のバージョンまたは任意のバージョンの Revolution Analytics ツールをインストールした場合は、最初アンインストールする必要があります。  [「Microsoft R Server の以前のバージョンからのアップグレード」](#bkmk_Uninstall)を参照してください。

2. SQL Server 2016 セットアップを実行します。 Service Pack 1 以降をインストールすることをお勧めします。

3. **[インストール]** タブで、 **[New R Server (Standalone) installation]** (新しい R Server (スタンドアロン) のインストール) をクリックします。
    
     ![R Server のスタンドアロンのセットアップ オプション](media/rsql-rstandalonesetup.png "R Server のスタンドアロンのセットアップ オプション")
    
4.  **[機能の選択]** ページで、次のオプションが既に選択されています。
    
    **R Server (スタンドアロン)**  
    
    その他のすべてのオプションは無視できます。 SQL Server データベース エンジンまたは SQL Server R Services をインストールしません。
    
5.  Microsoft R Open のダウンロードとインストールに関するライセンス条項に同意します。 [ **同意する** ] ボタンが使用できない状態になっている場合は、[ **次へ**] をクリックします。 
    
    これらのコンポーネント (および、そのコンポーネントに必要なすべての前提条件) のインストールには時間がかかる場合があります。
    
6.  [ **インストールの準備完了** ] ページで、選択内容を確認し、[ **インストール**] をクリックします。  


### <a name="upgrade-an-existing-r-server-to-901"></a>既存の R サーバー 9.0.1 をアップグレードします。

Microsoft R Server (スタンドアロン) の以前のバージョンをインストールした場合は、新しいバージョンの R コンポーネントを使用するインスタンスをアップグレードできます。 アップグレードでは、サーバーの最新のライフ サイクルのサポート ポリシーも変更されます。 これにより、SQL Server リリースよりも別のスケジュールでより多くの場合、更新するインスタンス。

1. まだインストールされていない場合は、Microsoft R Server (スタンドアロン) をインストールします。

2. ダウンロードの場所から別の windows インストーラーのとおりです: [Microsoft R Server for Windows に実行](https://msdn.microsoft.com/microsoft-r/rserver-install-windows#howtoinstall)です。

3. インストーラーを実行し、次の[手順](https://msdn.microsoft.com/microsoft-r/rserver-install-windows#download-r-server-installer)です。


### <a name="change-in-default-folder-for-r-packages"></a>R パッケージの既定のフォルダーを変更します。

SQL Server セットアップを使用してをインストールするときに、R ライブラリは、セットアップを使用して SQL Server のバージョンに関連付けられているフォルダーにインストールされます。 このフォルダーには、サンプル データ、基本的な R パッケージに関するドキュメント、R ツールとランタイムに関するドキュメントもあります。

**SQL Server 2016 を使用してセットアップした R Server (スタンドアロン)**

`C:\Program Files\Microsoft SQL Server\130\R_SERVER`

**SQL Server 2017 を使用してセットアップした R Server (スタンドアロン)**

`C:\Program Files\Microsoft SQL Server\140\R_SERVER`

**スタンドアロンの Windows インストーラーを使用した設定します。**

ただし、別の Windows インストーラーを使用してインストールする場合、または別の Windows インストーラーを使用してアップグレードする場合は、R ライブラリは次の R サーバーのフォルダーに移動します。

`C:\Program Files\Microsoft\R Server\R_SERVER`
      
**サービス データベースでの R 備えてまたは Machine LEarning のセットアップ**

R Services (In-database) または Machine Learning Services (In-database)、SQL Server のインスタンスをインストールするいるし、そのインスタンスが同じコンピューターに、R ライブラリおよびツールが既定では、別のフォルダーにインストールします。

`C:\Program Files\Microsoft SQL Server\<instance_name>\R_SERVICES`

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インスタンスに関連付けられた R パッケージまたはユーティリティは直接呼び出さないでください。 R Server と R Services の両方がインストールされている場合、同じコンピューターで RGui またはその他のツールを実行する必要がある場合、R のツールと R_SERVER フォルダーにインストールされているパッケージを使用します。


### <a name="development-tools"></a>開発ツール

開発 IDE はセットアップの一部としてインストールされていません。 その他のツールは必要ありませんに R または Python の分布を使用して指定するようにすべての標準的なツールが含まれます。

試してみることをお勧め、新しいリリースの[!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)]、Visual Studio は、R と、Python と SQL Server と BI の両方のツールをサポートしています。 ただし、RStudio を含む、任意の希望する開発環境を使用することができます。

## <a name="troubleshooting"></a>トラブルシューティング  

### <a name="incompatible-version-of-r-client-and-r-server"></a>R Client および R Server の互換性のないバージョン

インストールした最新バージョンの Microsoft R Client を使用し、SQL Server でリモート コンピューティング コンテキストを用いて R を実行すると、以下のようなエラーが発生する場合があります。

*Microsoft R Server バージョン 8.0.3 と互換性のない、バージョン 9.0.0 の Microsoft R Client をコンピューター上で実行しています。互換性のあるバージョンをダウンロードしてインストールしてください。*

通常、サービス リリースの公開時に、SQL Server R Services と共にインストールされる R のバージョンが更新されます。 常に最新バージョンの R コンポーネントを使用するためには、サービス パックをすべてインストールします。 Microsoft R Client 9.0.0 との互換性を維持するには、この [サポート記事](https://support.microsoft.com/kb/3210262)で説明されている更新プログラムをインストールする必要があります。 


### <a name="installing-microsoft-r-server-on-an-instance-of-sql-server-installed-on-windows-core"></a>Windows Core にインストールされた SQL Server のインスタンスへの Microsoft R Server のインストール

RTM バージョンの SQL Server 2016 でが既知の問題 Microsoft R Server を Windows Server Core エディションでインスタンスに追加するときにします。 この問題は修正されています。

この問題が発生する場合は、 [KB3164398](https://support.microsoft.com/kb/3164398) に記載の修正プログラムを適用して、Windows Server Core の既存のインスタンスに R 機能を追加してください。   詳細については、 [「Can't install Microsoft R Server Standalone on a Windows Server Core operating system」](https://support.microsoft.com/kb/3168691)(Windows Server Core オペレーティング システムに Microsoft R Server (スタンドアロン) をインストールすることはできません) を参照してください。


###  <a name="bkmk_Uninstall"></a> 「Microsoft R Server の以前のバージョンからのアップグレード」

Microsoft R Server のプレリリース版がインストールされている場合は、それをアンインストールしてから新しいバージョンにアップグレードする必要があります。

**R Server (スタンドアロン) をアンインストールするには**

1.  [ **コントロール パネル**] を開き、[ **プログラムの追加と削除**] をクリックし、 `Microsoft SQL Server 2016 <version number>`を選択します。  
  
2.  コンポーネントに対する [ **追加**]、[ **修復**]、または [ **削除** ] オプションを含むダイアログ ボックスが表示されたら、[ **削除**] を選択します。  
  
3.  [ **機能の選択** ] ページの [ **共有機能**] で [ **R Server (スタンドアロン)**] を選択します。 [ **次へ**] をクリックし、[ **完了** ] をクリックして、選択したコンポーネントのみをアンインストールします。  
   
### <a name="installation-fails-with-error-only-one-revolution-enterprise-product-can-be-installed-at-a-time"></a>インストールに失敗し "Revolution Enterprise 製品は一度に 1 つしかインストールできません" というエラーが表示される

このエラーは、以前の Revolution Analytics 製品またはプレリリース版の SQL Server R Services がインストールされている場合に発生する可能性があります。 以前のバージョンが存在する場合は、そのアンインストールを行ってから、Microsoft R Server の新しいバージョンをインストールしてください。 他のバージョンの Revolution Enterprise ツールとのサイド バイ サイド インストールはサポートされていません。

ただし、サイド バイ サイド インストールは、R Server (スタンドアロン) を [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] または SQL Server 2016 と共に使用する場合はサポートされます。

### <a name="unable-to-uninstall-older-components"></a>以前のコンポーネントをアンインストールできない

以前のバージョンの削除時に問題が発生する場合は、レジストリを編集して関連するキーを削除することが必要な場合があります。

> [!IMPORTANT]
> この問題は、プレリリース版の Microsoft R Server または CTP バージョンの SQL Server 2016 R Services がインストールされている場合にのみ発生します。
  
1. Windows レジストリを開き、 `HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall`キーを見つけます。
2. 次のエントリのいずれかが存在し、キーに値 `sEstimatedSize2`のみが含まれる場合は、該当するエントリを削除します。
  
    -   E0B2C29E-B8FC-490B-A043-2CAE75634972        (8.0.2 の場合)
  
    -   46695879-954E-4072-9D32-1CC84D4158F4        (8.0.1 の場合)
  
    -   2DF16DF8-A2DB-4EC6-808B-CB5A302DA91B        (8.0.0 の場合)
  
    -   5A2A1571-B8CD-4AAF-9303-8DF463DABE5A        (7.5.0 の場合)
  
## <a name="see-also"></a>参照

[Microsoft R Server](../../advanced-analytics/r-services/r-server-standalone.md)


