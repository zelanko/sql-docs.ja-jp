---
title: アップグレードとインストールよく寄せられる質問 (FAQ) - SQL Server Machine Learning サービス
ms.custom: sqlseattle
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/15/2018
ms.topic: conceptual
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.openlocfilehash: dd92ba0e080da0dd8ed387ae0a9f3d431232c896
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432855"
---
# <a name="upgrade-and-installation-faq-for-sql-server-machine-learning-or-r-server"></a>SQL Server Machine Learning の R Server のアップグレードとインストールに関する FAQ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このトピックでは、machine learning の SQL Server 機能のインストールに関するよく寄せられる質問に対する回答を提供します。 アップグレードに関する一般的な質問についても説明します。

+ いくつかの問題は、プレリリース版からのアップグレードでのみ発生します。 そのため、ことをバージョンとエディションを識別最初にこれらの注意事項を読む前にお勧めします。 バージョン情報を取得するには実行`@@VERSION`SQL Server Management Studio からのクエリでします。
+ 最新のリリースまたは最近のリリースで修正された問題を解決するのには、できるだけ早くサービス リリースにアップグレードします。

**適用対象:** SQL Server 2016 R Services、SQL Server 2017 Machine Learning サービス (データベース)

## <a name="requirements-and-restrictions-on-older-versions-of-sql-server-2016"></a>要件と SQL Server 2016 の以前のバージョンに関する制限事項 

インストールする SQL Server のビルド、に応じて次の制限事項のいくつかの可能性があります適用されます。

- 以前のバージョンの SQL Server 2016 R Services では、8dot3 表記が作業ディレクトリを含むドライブに必要でした。 リリース前のバージョンをインストールした場合は、SQL Server 2016 Service Pack 1 にアップグレードするとこの問題を解決する必要があります。 SP1 以降後は、この要件はリリースに適用されません。

- 現時点では、インストールすることはできません[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]フェイル オーバー クラスター。 ただし、SQL Server 2019 プレビューは、テスト環境では、この機能を評価したい場合、フェールオーバーのサポートを提供しています。 詳細については、次を参照してください。[新](../what-s-new-in-sql-server-machine-learning-services.md)します。

- Azure VM では、追加の構成が必要にあります。 たとえば、リモート アクセスをサポートするファイアウォール例外を作成する必要があります。

- R の別のバージョンまたは Revolution Analytics から他のリリースのサイド バイ サイドでインストールがサポートされていません。

- セットアップを開始する前にウィルス対策を無効にします。 ウイルス スキャンが使用するフォルダーの中断をお勧めのセットアップが完了すると、[!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]します。 可能であれば、全体のスキャンを中断[!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]ツリー。

 - Windows Core にインストールされている SQL Server のインスタンスには、Microsoft R Server をインストールします。 SQL Server 2016 の RTM バージョンであった既知の問題を Windows Server Core エディションにインスタンスに Microsoft R Server を追加するときにします。 この問題は修正されています。 この問題に遭遇した場合は、記載の修正プログラムを適用できます[KB3164398](https://support.microsoft.com/kb/3164398) Windows Server Core では、既存のインスタンスに R 機能を追加します。 詳細については、 [「Can't install Microsoft R Server Standalone on a Windows Server Core operating system」](https://support.microsoft.com/kb/3168691)(Windows Server Core オペレーティング システムに Microsoft R Server (スタンドアロン) をインストールすることはできません) を参照してください。


## <a name="offline-installation-of-machine-learning-components-for-a-localized-version-of-sql-server-2016"></a>SQL Server 2016 のローカライズされたバージョンで machine learning コンポーネントのオフライン インストール

SQL Server 2016 の初期リリース バージョンは、インターネットに接続せずにオフラインのセットアップ中にロケール固有の .cab ファイルをインストールできませんでした。 この問題は今後のリリースで修正されましたが、インストーラーには、適切な言語をインストールできないことを示すメッセージが返された場合は、セットアップを続行を許可するファイル名を編集できます。

+ 適切な言語がインストールされていることを確認するインストーラー ファイルを手動で編集するには。 たとえば、日本語バージョンの SQL Server をインストールするには変更するファイルの名前 srs_8.0.3.0_**1033**.cab SRS_8.0.3.0_ から**1041**.cab です。
+ Machine learning コンポーネントに使用される言語識別子には、SQL Server セットアップの言語と同じである必要があります。 またはセットアップを完了することはできません。

## <a name="pre-release-versions-support-policies-upgrade-and-known-issues"></a>プレリリース版: ポリシー、アップグレード、および既知の問題のサポート

プレリリース版の新規インストール[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]現在サポートされていません。 リリース前のバージョンを使用している場合、できるだけ早くにアップグレードします。

このセクションには、特定のアップグレード シナリオの詳細な手順が含まれています。

### <a name="how-to-upgrade-sql-server"></a>SQL Server をアップグレードする方法

SQL Server のバージョンをアップグレードするには、セットアップ ウィザードを再実行します。

+ [SQL Server のアップグレード](../../database-engine/install-windows/upgrade-sql-server.md)
+ [インストール ウィザードを使用して SQL Server をアップグレードします。](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)

コンポーネントのバインドと呼ばれるプロセスを使用して学習マシンだけをアップグレードできます。 
+ [SqlBindR を使用して、machine learning コンポーネントをアップグレードするには](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)

### <a name="end-of-support-for-in-place-upgrades-from-prerelease-versions"></a>プレリリース バージョンからのインプレース アップグレードのサポートの終了

SQL Server 2016 のプレリリース バージョンからのアップグレードがサポートされていません。 これは、SQL Server 2016 CTP3、CTP3.1、CTP3.2、RC0、または RC1 に含まれます。

次のバージョンは、SQL Server 2016 のプレリリース版と共にインストールされました。

| バージョン | ビルド         |
|---------|---------------|
| CTP 3.0 | 13.0.xxx      |
| CTP 3.1 | 13.0.801.12   |
| CTP 3.2 | 13.0.900.73   |
| CTP 3.3 | 13.0.1000.281 |
| RC1     | 13.0.1200.242 |
| RC2     | 13.0.1300.275 |
| RC3     | 13.0.1400.361 |

バージョンを使用している疑いがある場合は、実行`@@VERSION`SQL Server Management Studio からのクエリでします。

一般に、アップグレード プロセスのとおりです。

1. スクリプトとデータをバックアップします。
2. プレリリース版をアンインストールします。
3. リリース バージョンをインストールします。

SQL Server のプレリリース バージョンをアンインストールする machine learning コンポーネントは複雑になることし、特別なスクリプトを実行する必要があります。 ご購入元に問い合わせてください。

###  <a name="bkmk_Uninstall"></a> Microsoft R Server の以前のバージョンからアップグレードする前にアンインストールします。

Microsoft R Server のプレリリース版がインストールされている場合は、それをアンインストールしてから新しいバージョンにアップグレードする必要があります。

1.  **[コントロール パネル]** を開き、**[プログラムの追加と削除]** をクリックし、 `Microsoft SQL Server 2016 <version number>`を選択します。

2.  コンポーネントに対する **[追加]**、**[修復]**、または **[削除]** オプションを含むダイアログ ボックスが表示されたら、**[削除]** を選択します。
  
3.  **[機能の選択]** ページの **[共有機能]** で **[R Server (スタンドアロン)]** を選択します。 **[次へ]** をクリックし、**[完了]** をクリックして、選択したコンポーネントのみをアンインストールします。

## <a name="r-services-and-r-server-standalone-side-by-side-errors"></a>R Services と R Server (スタンドアロン) のサイド バイ サイドでのエラー 

SQL Server 2016 の以前のバージョンでセットアップが「アクセス拒否」メッセージで失敗する原因となったも同時に、R Server (スタンドアロン) と R Services (In-database) の両方をインストールします。 この問題は、SQL Server 2016 用 Service Pack 1 で修正されました。

、エラーが発生してこれらの機能をアップグレードする必要がある場合は、SQL Server 2016 SP1 のスリップ ストリーム インストールを実行します。 アンインストールして再インストールを必要とする、問題を解決するのには 2 つの方法はあります。

1. R Services (In-database) をアンインストールし、SQLRUserGroup のユーザー アカウントが削除されたかどうかを確認します。

2. サーバーを再起動し、R Server (スタンドアロン) を再インストールします。

3. 実行の SQL Server セットアップの詳細を 1 回と、この時間を選択**を既存の SQL Server 機能の追加**します。

4. インスタンスを選択し、選択、 **R Services (In-database)** を追加するオプション。

この手順では、問題を解決するのには失敗した場合、次の回避策を試してください。

1. 同時に、R Services (In-database) と R Server (スタンドアロン) をアンインストールします。

2. ローカル ユーザー アカウント (SQLRUserGroup) を削除します。

3. サーバーを再起動します。

4. SQL Server セットアップを実行し、R Services (In-database) の機能のみを追加します。 選択しない**R Server (スタンドアロン)** します。

一般に、同じコンピューターに R Services (In-database) と R Server (スタンドアロン) の両方をインストールしないことお勧めします。 ただし、サーバーに十分な容量と仮定すると、ありますスタンドアロンの R Server 開発ツールとして便利な場合。 もう 1 つの考えられるシナリオは、R Server の運用化機能を使用して、データ移動することがなく SQL Server データにアクセスすることも必要です。

## <a name="incompatible-version-of-r-client-and-r-server"></a>R Client および R Server の互換性のないバージョン

Microsoft R Client をインストールしてリモートの SQL Server 計算コンテキストで R を実行して、このようなエラーが発生した可能性があります。

*Microsoft R server バージョン 8.0.3 と互換性がないコンピューターには、バージョン 9.0.0 の Microsoft R client を実行しています。互換性のあるバージョンをダウンロードしてインストールしてください。*

SQL Server 2016 では必要な SQL Server R Services で実行されていた R のバージョンが Microsoft R Client でのライブラリと同じであること。 以降のバージョンでその要件が削除されました。 ただし、常に、機械学習、コンポーネントの最新バージョンを取得してインストールするすべてのサービス パックお勧めします。 

Microsoft R Server の以前のバージョンを Microsoft R Client 9.0.0 との互換性を確保する必要がある場合は、これで説明されている更新プログラムをインストール[サポート記事](https://support.microsoft.com/kb/3210262)します。


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

## <a name="see-also"></a>関連項目

 [SQL Server Machine Learning Services (In-database)](../r/sql-server-r-services.md)

 [SQL Server Machine Learning Server (スタンドアロン)](../r/r-server-standalone.md)
