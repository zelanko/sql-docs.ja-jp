---
title: SQL Server の Machine Learning のサービスに新しい R パッケージをインストール |Microsoft ドキュメント
description: SQL Server 2016 の R Services または SQL Server 2017 Machine Learning Services (In-database) に新しい R パッケージを追加します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/29/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e05842a8e8a5a1d2454dbbe500b4d5aa95fca660
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34707080"
---
# <a name="install-new-r-packages-on-sql-server"></a>SQL Server に新しい R パッケージをインストールします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、機械学習が有効になっている SQL Server のインスタンスに新しい R パッケージをインストールする方法について説明します。 SQL Server のバージョンがある場合、および、サーバーがインターネットに接続を持つかどうかに応じて、新しい R パッケージをインストールするための複数の方法はあります。 新しいパッケージのインストールの次の方法は、考えられます。

| アプローチ                           | アクセス許可               | リモート/ローカル |
|------------------------------------|---------------------------|--------------|
| [従来の R パッケージ マネージャーを使用します。](use-r-package-managers-on-sql-server.md)  | 管理 | Local |
| [RevoScaleR の使用](use-revoscaler-to-manage-r-packages.md) |  データベース ロールの管理者が有効な後 | both|
| [T-SQL (外部ライブラリの作成) を使用します。](install-r-packages-tsql.md) | データベース ロールの管理者が有効な後 | both 

## <a name="who-installs-permissions"></a>(アクセス許可) をインストールします。

パッケージの R ライブラリは物理的にアクセスが制限されたセキュリティで保護されたフォルダーには、SQL Server インスタンスの Program Files フォルダーに配置します。 この場所に書き込むには、管理者のアクセス許可が必要です。

管理者以外は、パッケージをインストールできますが、求め addititional 構成と機能の初期インストールでは使用できません。 管理者以外のパッケージのインストールの 2 つの方法: RevoScaleR バージョン 9.0.1 とを使用するか、その後、外部ライブラリの作成 (SQL Server 2017 のみ) を使用します。 SQL Server の 2017 で**dbo_owner**外部ライブラリの作成アクセス許可を持つ別のユーザーは、現在のデータベースに R パッケージをインストールすることもできます。

R 開発者は、中央に配置されたライブラリは触れません場合に必要なパッケージのユーザーのライブラリの作成に慣れています。 この実習では、SQL Server データベース エンジン インスタンスで実行される R コードの問題です。 SQL Server は、そのライブラリが同じコンピューター上にある場合でも、外部のライブラリからパッケージをロードできません。 SQL Server で実行されている R コードでは、インスタンスのライブラリからのパッケージのみを使用できます。

サーバーで、ファイル システム アクセスが制限されている通常、外部スクリプトの実行時 SQL Server で実行されるがアクセスできる既定のインスタンスの外部にインストール パッケージではない場合でも、サーバー上のユーザー ドキュメント フォルダーにある場合の管理者権限とアクセスは、ライブラリです。 

## <a name="considerations-for-package-installation"></a>パッケージのインストールに関する注意点

新しいパッケージをインストールする前に、特定のパッケージで有効な機能が SQL Server 環境に適しているかどうかを検討してください。 セキュリティを強化した SQL Server の環境では、次を回避する可能性があります。

+ ネットワーク アクセスが必要なパッケージ
+ Java、またはその他のフレームワークを SQL Server 環境で通常使用が必要なパッケージ
+ 管理者特権でのファイル システム アクセスが必要なパッケージ
+ パッケージを web 開発または SQL Server 内で実行するパフォーマンスを改善しないその他のタスクの使用します。

## <a name="offline-installation-no-internet-access"></a>オフライン インストール (インターネットにアクセスできない)

一般に、実稼働データベースをホストするサーバーは、インターネット接続をブロックします。 このような環境で新しい R パッケージまたは Python パッケージをインストールするには、パッケージと依存関係を事前に準備し、オフライン インストール用のサーバー上のフォルダーにファイルをコピーする必要があります。

すべての依存関係を識別することは、複雑な取得します。 使用することお勧めを r、 [miniCRAN ローカル リポジトリを作成する](create-a-local-package-repository-using-minicran.md)し、分離の SQL Server インスタンスに完全に定義されたリポジトリを転送します。

Alternativley、操作を行いますこの手動で。

1. すべてのパッケージの依存関係を識別します。 
2. サーバーで、必要なパッケージが既にインストールされているかどうかを確認してください。 パッケージがインストールされている場合は、バージョンが正しいことを確認します。
3. パッケージとすべての依存関係を別のコンピューターにダウンロードします。
4. サーバーがアクセスできるフォルダーにファイルを移動します。
5. インスタンスのライブラリにパッケージをインストールするには、サポートされているインストール コマンドまたは DDL ステートメントを実行します。

### <a name="download-the-package-as-a-zipped-file"></a>Zip ファイルとしてパッケージをダウンロードします。

サーバーのインストールに、インターネットにアクセスせず、オフライン インストールの zip ファイルの形式でパッケージのコピーをダウンロードする必要があります。 **パッケージを解凍できません。**

たとえば、次の手順は、の正しいバージョンを取得するようになりましたについて説明します。、 [FISHalyseR](http://bioconductor.org/packages/release/bioc/html/FISHalyseR.html)パッケージを Bioconductor、コンピューターがインターネットにアクセスしていると仮定してからです。

1.  **[パッケージ アーカイブ]** ボックスの一覧で、 **Windows バイナリ** バージョンを見つけます。

2.  リンクを右クリックします。ZIP ファイル、および選択**として保存ターゲット**です。

3.  Zip 形式のパッケージが格納されているをクリックして、ローカル フォルダーに移動**保存**です。

    このプロセスにより、パッケージのローカル コピーが作成されます。 

4. ダウンロード エラーが発生した場合は、さまざまなミラー サイトを再試行してください。

5. パッケージのアーカイブをダウンロードすると、パッケージをインストールまたは zip 形式のパッケージをインターネット アクセスが許可されていないサーバーにコピーできます。

> [!TIP]
> 場合は、誤ってバイナリをダウンロードする代わりに、パッケージをインストールすると、ダウンロードした zip ファイルのコピーがコンピューターにも保存されます。 ファイルの場所を決定するパッケージがインストールされているステータス メッセージをご覧ください。 インターネット アクセスが許可されていないサーバーには、その zip ファイルをコピーできます。
> 
> ただし、このメソッドを使用してパッケージを取得するときに、依存関係は含まれません。 


## <a name="side-by-side-installation-with-standalone-r-or-python-servers"></a>スタンドアロン R または Python サーバーとのサイド バイ サイド インストール

同じコンピューターに共存するすべての可能性がありますをいくつかの Microsoft 製品では、R、Python の機能が含まれています。

お使いのコンピューターは独立したデータベース内分析 (SQL Server 2017 Machine Learning Services および SQL Server 2016 R サービス) に加えて SQL Server 2017 Microsoft Machine Learning サーバー (スタンドアロン) または SQL Server 2016 R Server (スタンドアロン) をインストールした場合ごとに、すべての R ツールとライブラリの重複を削除しない R のインストール。

R_SERVER ライブラリにインストールされているパッケージは、スタンドアロン サーバーでのみ使用され、SQL Server (In-database) のインスタンスからはアクセスできません。 常に使用する、`R_SERVICES`ライブラリ データベースに SQL Server を使用するパッケージをインストールするときにします。 パスの詳細については、次を参照してください。[ライブラリの場所にパッケージ化](installing-and-managing-r-packages.md#package-library-location)です。


## <a name="see-also"></a>参照

+ [新しい Python パッケージのインストール](../python/install-additional-python-packages-on-sql-server.md)
+ [チュートリアル、サンプル、ソリューション](../tutorials/machine-learning-services-tutorials.md)