---
title: "SQL Server の Machine Learning のアップグレードとインストールに関する FAQ |Microsoft ドキュメント"
ms.date: 03/15/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.workload: On Demand
ms.openlocfilehash: 3cbb94081b2d056128fb4beda413c82cd4a20964
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2018
---
# <a name="upgrade-and-installation-faq-for-sql-server-machine-learning-or-r-server"></a>SQL Server の Machine Learning の R Server のアップグレードとインストールに関する FAQ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このトピックでは、機械学習の SQL Server 機能のインストールに関してよく寄せられる質問に対する回答を示します。 アップグレードに関する一般的な質問についても説明します。

+ いくつかの問題は、プレリリース版からアップグレードでのみ発生します。 したがって、するを識別するバージョンおよびエディション最初にこれらの注意事項を読み取る前にお勧めします。 バージョン情報を取得するには実行`@@VERSION`SQL Server Management Studio からのクエリにします。
+ 最近のリリースで修正された問題を解決するには、最新のリリースまたはできるだけ早くのサービスのリリースにアップグレードします。

**適用されます:** SQL Server 2016 の R Services、SQL Server 2017 機械学習の Services (In-database)

## <a name="requirements-and-restrictions-on-older-versions-of-sql-server-2016"></a>要件と SQL Server 2016 の以前のバージョンの制限 

インストールする SQL Server のビルドによって、次の制限の一部は、次の場合がありますに適用。

- 以前のバージョンの SQL Server 2016 の R Services では、8dot3 表記は、作業ディレクトリを含むドライブに必要でした。 プレリリース版をインストールした場合 SQL Server 2016 Service Pack 1 にアップグレードすると、この問題を解決する必要があります。 SP1 以降後は、この要件はリリースに適用されません。

- R の別のバージョンまたは Revolution Analytics からの他のリリースとサイド バイ サイド インストールはサポートされていません。

- セットアップを開始する前にウイルスを無効にします。 セットアップが完了したら、ことをお勧めウイルス スキャンが使用するフォルダーを中断[!INCLUDE[ssnoversion](../../includes/ssnoversion.md)]です。 可能であれば、全体のスキャンを中断[!INCLUDE[ssnoversion](../../includes/ssnoversion.md)]ツリー。

 - Windows Core にインストールされている SQL Server のインスタンスに Microsoft R Server をインストールします。 RTM バージョンの SQL Server 2016 でが既知の問題 Microsoft R Server を Windows Server Core エディションでインスタンスに追加するときにします。 この問題は修正されています。 この問題が発生した場合は、修正プログラムを適用することができます[プログラム KB3164398](https://support.microsoft.com/kb/3164398)を Windows Server Core 上の既存のインスタンスに R の機能を追加します。 詳細については、 [「Can't install Microsoft R Server Standalone on a Windows Server Core operating system」](https://support.microsoft.com/kb/3168691)(Windows Server Core オペレーティング システムに Microsoft R Server (スタンドアロン) をインストールすることはできません) を参照してください。


## <a name="offline-installation-of-machine-learning-components-for-a-localized-version-of-sql-server-2016"></a>SQL Server 2016 のローカライズされたバージョンの machine learning コンポーネントのオフライン インストール

SQL Server 2016 の初期リリース バージョンは、インターネットに接続せず、オフライン セットアップ時にロケール固有の .cab ファイルをインストールできませんでした。 この問題は、今後のリリースで修正されましたが、インストーラーには、適切な言語をインストールできないことを示すメッセージが返された場合は、セットアップを続行を許可するファイル名を編集できます。

+ 適切な言語がインストールされていることを確認するインストーラー ファイルを手動で編集します。 たとえば、日本語バージョンの SQL Server をインストールするには変更するファイルの名前 SRS_8.0.3.0_ から**1033**SRS_8.0.3.0_ に .cab**1041**.cab です。
+ 機械学習のコンポーネントに使用される言語識別子には、SQL Server セットアップの言語と同じである必要がありますか、セットアップを完了することはできません。

## <a name="pre-release-versions-support-policies-upgrade-and-known-issues"></a>プレリリース版: ポリシー、アップグレード、および既知の問題のサポート

プレリリース バージョンの新規インストール[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]は現在サポートされていません。 リリース前のバージョンを使用している場合はできるだけ早くアップグレードします。

このセクションには、特定のアップグレード シナリオの詳細な手順が含まれています。

### <a name="how-to-upgrade-sql-server"></a>SQL Server をアップグレードする方法

SQL Server のバージョンをアップグレードするには、セットアップ ウィザードを再実行します。

+ [SQL Server のアップグレード](../../database-engine/install-windows/upgrade-sql-server.md)
+ [インストール ウィザードを使用して SQL Server をアップグレードします。](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)

バインディングと呼ばれるプロセスを使用してコンポーネントを学習、マシンだけをアップグレードすることができます。 
+ [Machine learning のコンポーネントをアップグレードする SqlBindR を使用します。](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)

### <a name="end-of-support-for-in-place-upgrades-from-prerelease-versions"></a>プレリリース バージョンからのインプレース アップグレードのサポートの終了

SQL Server 2016 のプレリリース バージョンからのアップグレードがサポートされていません。 これには、SQL Server 2016 CTP3、CTP3.1、CTP3.2、RC0、または RC1 が含まれます。

次のバージョンは、SQL Server 2016 のプレリリース バージョンと共にインストールされました。

| バージョン | ビルド         |
|---------|---------------|
| CTP 3.0 | 13.0.xxx      |
| CTP 3.1 | 13.0.801.12   |
| CTP 3.2 | 13.0.900.73   |
| CTP 3.3 | 13.0.1000.281 |
| RC1     | 13.0.1200.242 |
| RC2     | 13.0.1300.275 |
| RC3     | 13.0.1400.361 |

バージョンを使用している疑いがある場合は、実行`@@VERSION`SQL Server Management Studio からのクエリにします。

一般に、アップグレードのプロセスのとおりです。

1. スクリプトとデータをバックアップします。
2. プレリリース版をアンインストールします。
3. リリース バージョンをインストールします。

SQL Server のプレリリース版をアンインストールするマシン ラーニング コンポーネントは複雑になることができ、特別なスクリプトを実行する必要があります。 についてのテクニカル サポートに問い合わせてください。

###  <a name="bkmk_Uninstall"></a> Microsoft R Server の以前のバージョンからアップグレードする前にアンインストールします。

Microsoft R Server のプレリリース版がインストールされている場合は、それをアンインストールしてから新しいバージョンにアップグレードする必要があります。

1.  **[コントロール パネル]** を開き、**[プログラムの追加と削除]** をクリックし、 `Microsoft SQL Server 2016 <version number>`を選択します。

2.  コンポーネントに対する **[追加]**、**[修復]**、または **[削除]** オプションを含むダイアログ ボックスが表示されたら、**[削除]** を選択します。
  
3.  **[機能の選択]** ページの **[共有機能]** で **[R Server (スタンドアロン)]** を選択します。 **[次へ]** をクリックし、**[完了]** をクリックして、選択したコンポーネントのみをアンインストールします。

## <a name="r-services-and-r-server-standalone-side-by-side-errors"></a>R Services と R Server (スタンドアロン) のサイド バイ サイドのエラー 

SQL Server 2016 の以前のバージョンでも同時に R Server (スタンドアロン) と R Services (In-database) の両方をインストールすると、「アクセス拒否」メッセージで失敗するセットアップが発生します。 この問題は、SQL Server 2016 の Service Pack 1 で修正されました。

このエラーが発生しました、これらの機能をアップグレードする必要がある場合は、SQL Server 2016 sp1 のスリップ ストリーム インストールを実行します。 アンインストールと再インストールを必要とする、問題を解決するのには 2 つの方法ができます。

1. R Services (In-database) をアンインストールし、SQLRUserGroup のユーザー アカウントが削除されたかどうかを確認します。

2. サーバーを再起動し、R Server (スタンドアロン) を再インストールします。

3. 実行の SQL Server セットアップの詳細を 1 回、この時間を選択**を既存の SQL Server の機能の追加**です。

4. インスタンスを選択してから、 **R Services (In-database)**を追加するオプションです。

この手順は、問題を解決するのには失敗すると、次の回避策を試してください。

1. 同時に、R Services (In-database) と R Server (スタンドアロン) をアンインストールします。

2. ローカル ユーザー アカウント (SQLRUserGroup) を削除します。

3. サーバーを再起動します。

4. SQL Server セットアップを実行し、R Services (In-database) の機能のみを追加します。 選択しない**R Server (スタンドアロン)**です。

一般に、同じコンピューターに R Services (In-database) と R Server (スタンドアロン) の両方をインストールしないようにお勧めします。 ただし、サーバーを持っていれば、十分な容量、あります R Server のスタンドアロンの開発ツールとして役立ちます可能性。 もう 1 つの可能なシナリオに、R サーバーの操作運用の機能を使用するものデータ移動なしの SQL Server データにアクセスする必要があります。

## <a name="incompatible-version-of-r-client-and-r-server"></a>R Client および R Server の互換性のないバージョン

Microsoft R クライアントをインストール、使用して、リモート SQL Server のコンピューティング コンテキストで R を実行する場合は、次のようなエラーが発生した可能性があります。

*Microsoft R Server 8.0.3 のバージョンの互換性がないコンピューターに 9.0.0 のバージョンの Microsoft R クライアントを実行しています。互換性のあるバージョンをダウンロードしてインストールしてください。*

SQL Server 2016 が必要な SQL Server R Services で実行されていた R のバージョンが Microsoft R クライアントでのライブラリと同じであること。 以降のバージョンで、その要件が削除されました。 ただし、常に、機械学習のコンポーネントの最新バージョンを取得してインストールするすべてのサービス パックお勧めします。 

Microsoft R Server の以前のバージョンをした Microsoft R クライアント 9.0.0 との互換性を確保する必要がある場合は、この説明されている更新プログラムをインストール[サポートの記事](https://support.microsoft.com/kb/3210262)です。


## <a name="installation-fails-with-error-only-one-revolution-enterprise-product-can-be-installed-at-a-time"></a>インストールに失敗し "Revolution Enterprise 製品は一度に 1 つしかインストールできません" というエラーが表示される

このエラーは、以前の Revolution Analytics 製品またはプレリリース版の SQL Server R Services がインストールされている場合に発生する可能性があります。 以前のバージョンが存在する場合は、そのアンインストールを行ってから、Microsoft R Server の新しいバージョンをインストールしてください。 他のバージョンの Revolution Enterprise ツールとのサイド バイ サイド インストールはサポートされていません。

ただし、サイド バイ サイド インストールは、R Server (スタンドアロン) を [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] または SQL Server 2016 と共に使用する場合はサポートされます。

## <a name="registry-cleanup-to-uninstall-older-components"></a>古いコンポーネントをアンインストールするレジストリのクリーンアップ

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

 [SQL Server コンピューターのサービス (In-database) を学習](../r/sql-server-r-services.md)

 [SQL Server コンピューターがサーバー (スタンドアロン) を学習](../r/r-server-standalone.md)
