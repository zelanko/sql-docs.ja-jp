---
title: 新しい R 言語パッケージ - SQL Server Machine Learning Services のインストールします。
description: SQL Server 2016 R Services または SQL Server 2017 の Machine Learning Services (In-database) に新しい R パッケージを追加します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/22/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: b8c935400188ae6905a9915907fb097d02100ad2
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2019
ms.locfileid: "65994208"
---
# <a name="install-new-r-packages-on-sql-server"></a>SQL Server に新しい R パッケージをインストールします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、機械学習が有効になっている SQL Server のインスタンスに新しい R パッケージをインストールする方法について説明します。 SQL Server のバージョンがあると、サーバーがインターネットに接続を持つかどうかに応じて、新しい R パッケージをインストールするための複数の方法はあります。 新しいパッケージのインストールを次の方法があります。

| アプローチ                           | アクセス許可               | リモート/ローカル |
|------------------------------------|---------------------------|--------------|
| [従来の R パッケージ マネージャーを使用します。](use-r-package-managers-on-sql-server.md)  | 管理 | Local |
| [RevoScaleR の使用](use-revoscaler-to-manage-r-packages.md) |  データベース ロールの管理者が有効なその後 | both|
| [T-SQL (外部ライブラリの作成) を使用して、](install-r-packages-tsql.md) | データベース ロールの管理者が有効なその後 | both 

## <a name="who-installs-permissions"></a>(アクセス許可) をインストールします。

R パッケージ ライブラリは限定的なアクセスのセキュリティで保護されたフォルダーには、SQL Server インスタンスの Program Files フォルダー内に物理的に配置します。 この場所に書き込むには、管理者のアクセス許可が必要です。

管理者以外のユーザーがパッケージをインストールできますが、これは追加の構成と機能の初期インストールでは使用できないために必要です。 管理者以外のパッケージのインストールの 2 つの方法はあります。RevoScaleR バージョン 9.0.1 と以降、またはを使用して外部ライブラリの作成 (SQL Server 2017 のみ) を使用します。 SQL Server 2017 で**dbo_owner** CREATE EXTERNAL LIBRARY のアクセス許可を持つ別のユーザーは、現在のデータベースに R パッケージをインストールすることもできます。

R 開発者は、中央に配置されたライブラリが手付かずの状態がある場合に必要なパッケージのユーザーのライブラリの作成に慣れています。 この実習では、SQL Server データベース エンジンのインスタンスで実行される R コードの問題が発生します。 SQL Server は、そのライブラリが同じコンピューター上にある場合でも、外部ライブラリをからパッケージを読み込むことはできません。 インスタンスのライブラリからのみパッケージは、SQL Server で実行される R コードで使用できます。

ファイル システム アクセスは通常、サーバーで制限されているし、SQL server を実行する外部スクリプトのランタイムがアクセスできる既定のインスタンスの外部にインストールされているパッケージではない場合でも、管理者権限とアクセスは、サーバー上のユーザー ドキュメント フォルダーにある、ライブラリです。 

## <a name="considerations-for-package-installation"></a>パッケージのインストールに関する考慮事項

新しいパッケージをインストールする前に、特定のパッケージで有効化機能が SQL Server 環境に適しているかどうかを検討してください。 セキュリティを強化した SQL Server 環境では、次のことを回避する可能性があります。

+ ネットワーク アクセスを必要とするパッケージ
+ 管理者特権でのファイル システムへのアクセスを必要とするパッケージ
+ パッケージを web 開発または SQL Server 内部で実行することで利点を得られるしないその他のタスクの使用します。

## <a name="offline-installation-no-internet-access"></a>オフライン インストール (インターネット アクセスなし)

一般に、実稼働データベースをホストするサーバーは、インターネット接続をブロックします。 このような環境で新しい R または Python のパッケージをインストールするには、パッケージと依存関係を事前に準備し、オフライン インストール用のサーバー上のフォルダーにファイルをコピーする必要があります。

すべての依存関係を識別する複雑なを取得します。 R、私たちにを使用することを推奨[ローカル リポジトリを作成する miniCRAN](create-a-local-package-repository-using-minicran.md)し、分離の SQL Server インスタンスに完全に定義されているリポジトリを転送します。

または、次の手順を手動で実行できます。

1. すべてのパッケージの依存関係を特定します。 
2. サーバーで、必要なパッケージが既にインストールされているかどうかを確認します。 パッケージがインストールされている場合は、バージョンが正しいことを確認します。
3. パッケージとすべての依存関係を別のコンピューターにダウンロードします。
4. サーバーがアクセスできるフォルダーにファイルを移動します。
5. インスタンスのライブラリにパッケージをインストールするには、サポートされているインストール コマンドまたは DDL ステートメントを実行します。

### <a name="download-the-package-as-a-zipped-file"></a>Zip ファイルとしてパッケージをダウンロードします。

インターネットにアクセスできないサーバーへのインストール、オフライン インストール用の zip ファイルの形式でパッケージのコピーをダウンロードする必要があります。 **パッケージを解凍できません。**

たとえば、次の手順は、の正しいバージョンを取得するようになりましたについて説明します。、 [FISHalyseR](https://bioconductor.org/packages/release/bioc/html/FISHalyseR.html) Bioconductor、コンピューターがインターネットへのアクセスからのパッケージ。

1.  **[パッケージ アーカイブ]** ボックスの一覧で、 **Windows バイナリ** バージョンを見つけます。

2.  リンクを右クリックします。ZIP ファイル、および選択**として保存ターゲット**します。

3.  Zip 形式のパッケージが格納されていると、クリックしてのローカル フォルダーに移動します**保存**します。

    このプロセスにより、パッケージのローカル コピーが作成されます。 

4. ダウンロード エラーが発生する場合は、別のミラー サイトをお試しください。

5. パッケージのアーカイブをダウンロードすると、パッケージをインストールまたはインターネットへのアクセスがないサーバーに zip 形式のパッケージをコピーできます。

> [!TIP]
> 誤って、バイナリをダウンロードする代わりに、パッケージをインストールする場合も、コンピューターにダウンロードした zip ファイルのコピーが保存されます。 ファイルの場所を決定するパッケージがインストールされているステータス メッセージをご覧ください。 インターネットへのアクセスがないサーバーには、その zip ファイルをコピーできます。
> 
> ただし、このメソッドを使用してパッケージを取得すると、依存関係は含まれません。 


## <a name="side-by-side-installation-with-standalone-r-or-python-servers"></a>スタンドアロン R または Python のサーバーとのサイド バイ サイドでインストール

同じコンピューターに共存させるすべての可能性があります、複数のマイクロソフト製品では、R と Python の機能が含まれています。

コンピューターが個別にデータベース内分析 (SQL Server 2017 Machine Learning Services および SQL Server 2016 R Services) だけでなく SQL Server 2017 Microsoft Machine Learning Server (スタンドアロン) または SQL Server 2016 R Server (スタンドアロン) をインストールした場合ごとに、重複をすべての R ツールとライブラリの R のインストール。

R_SERVER ライブラリにインストールされているパッケージは、スタンドアロン サーバーでのみ使用され、SQL Server (In-database) のインスタンスではアクセスできません。 常に使用して、`R_SERVICES`ライブラリで SQL Server データベースでを使用するパッケージをインストールするときにします。 パスの詳細については、次を参照してください。[ライブラリの場所をパッケージ化](installing-and-managing-r-packages.md#package-library-location)します。


## <a name="see-also"></a>関連項目

+ [新しい Python パッケージのインストール](../python/install-additional-python-packages-on-sql-server.md)
+ [チュートリアル、サンプル、ソリューション](../tutorials/machine-learning-services-tutorials.md)
