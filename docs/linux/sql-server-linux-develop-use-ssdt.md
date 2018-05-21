---
title: 開発および Linux 用のデータベースを SQL Server のデプロイ |Microsoft ドキュメント
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.component: ''
ms.suite: sql
ms.technology: linux
ms.assetid: 1e924704-e07c-4a8b-b243-8c1dd8cff0d3
ms.custom: sql-linux
ms.openlocfilehash: 41eabe46f654f2cb0464d2f7589cb0ce50a7c214
ms.sourcegitcommit: 6fd8a193728abc0a00075f3e4766a7e2e2859139
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="use-visual-studio-to-create-databases-for-sql-server-on-linux"></a>Visual Studio を使用して Linux 上の SQL Server のデータベースを作成するには

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server Data Tools (SSDT) は、SQL Server on Linux の強力な開発およびデータベース ライフ サイクル管理 (DLM) 環境に Visual Studio をオンにします。 ことができますを開発、構築、テスト、およびアプリケーション コードを開発するのと同じように、ソース管理のプロジェクトからデータベースを発行します。

## <a name="install-visual-studio-and-sql-server-data-tools"></a>Visual Studio および SQL Server Data Tools をインストールします。

1. 既にインストールしていない Visual Studio、Windows コンピューターに場合[ダウンロードおよび Visual Studio のインストール]です。 Visual Studio Community エディション、受講者、無料の完全な機能を備えた IDE は、Visual Studio のライセンスがない、オープン ソース、および個々 の開発者。

2. Visual Studio のインストール中に次のように選択します。**カスタム**の、**インストールの種類を選択**オプション。 **[次へ]** をクリックします。

3. 選択**Microsoft SQL Server Data Tools**、 **Git for Windows**、および**Visual Studio 向け GitHub 拡張**機能選択項目の一覧です。

    <img src="./media/sql-server-linux-develop-use-ssdt/ssdt-setup.png" alt="ssdt setup" style="width: 400px;"/>

4. 続行して、Visual Studio のインストールを完了します。 これには数分かかることができます。

## <a name="upgrade-sql-server-data-tools-to-ssdt-170-rc-release"></a>SQL Server Data Tools を SSDT 17.0 RC のリリースにアップグレードします。

Linux 上の SQL Server 2017 は、SSDT 17.0 RC またはそれ以降のバージョンでサポートされています。

* [ダウンロードしてインストール SSDT 17.0 RC2](https://go.microsoft.com/fwlink/?linkid=837939)です。

## <a name="create-a-new-database-project-in-source-control"></a>ソース管理で新しいデータベース プロジェクトを作成します。

1. Visual Studio を起動します。

2. 選択**チーム エクスプ ローラー**上、**ビュー**メニュー。 

3. をクリックして**新規**で**ローカル Git リポジトリ**セクションで、**接続**ページ。

    <img src="./media/sql-server-linux-develop-use-ssdt/git-repository.png" alt="local repository" style="width: 300px;"/>

3. **[作成]** をクリックします。 ローカルの Git リポジトリが作成されると、ダブルクリックして**SSDTRepo**です。

4. をクリックして**新規**で、**ソリューション**セクションです。 選択**SQL Server** **他の言語**内のノード、**新しいプロジェクト**ダイアログ。

    <img src="./media/sql-server-linux-develop-use-ssdt/new-project.png" alt="local repository" style="width: 480px;"/>

5. 入力**TutorialDB**クリックと名前の **[ok]** 新しいデータベース プロジェクトを作成します。

## <a name="create-a-new-table-in-the-database-project"></a>データベース プロジェクトに新しいテーブルを作成します。

1. 選択**ソリューション エクスプ ローラー**上、**ビュー**メニュー。

2. メニューを開き、データベース プロジェクトを右クリックして**TutorialDB**ソリューション エクスプ ローラーでします。

3. 選択**テーブル****追加**です。

    <img src="./media/sql-server-linux-develop-use-ssdt/create-table.png" alt="create table" style="width: 480px;"/>

4. テーブル デザイナーを使用して、2 つの列名を追加`nvarchar(50)`と場所`nvarchar(50)`の図に示すように、します。 SSDT の生成、`CREATE TABLE`デザイナーで列を追加するときのスクリプトを作成します。

    <img src="./media/sql-server-linux-develop-use-ssdt/add-columns.png" alt="add columns" style="width: 480px;"/>

5. 保存、 **Table1.sql**ファイル。

## <a name="build-and-validate-the-database"></a>ビルド、およびデータベースの確認

1. データベース プロジェクト メニューを開き**TutorialDB**選択**ビルド**です。 SSDT では、.sql ソース コード ファイル、プロジェクトをコンパイルして、データ層アプリケーション パッケージ (dacpac) ファイルを構築します。 Linux に SQL Server 2017 インスタンスにデータベースを発行するために使用できます。 

    <img src="./media/sql-server-linux-develop-use-ssdt/build.png" alt="add columns" style="width: 400px;"/>

2. ビルドに成功メッセージを確認してください。**出力**Visual Studio のウィンドウ。 

## <a name="publish-the-database-to-sql-server-2017-instance-on-linux"></a>Linux 上の SQL Server 2017 インスタンスにデータベースをパブリッシュします。

1. データベース プロジェクト メニューを開き**TutorialDB**選択**発行**です。

2. をクリックして**編集**Linux 上の SQL Server インスタンスを選択します。

    <img src="./media/sql-server-linux-develop-use-ssdt/publish-dialog.png" alt="publish dialog" style="width: 480px;"/>

3. [接続] ダイアログのでは、Linux、ユーザー名とパスワードで SQL Server インスタンスの IP アドレスまたはホスト名に入力します。

    <img src="./media/sql-server-linux-develop-use-ssdt/connection-dialog.png" alt="connection dialog" style="width: 400px;"/>

4. クリックして、**発行**発行ダイアログ ボックスにボタンをクリックします。

5. 発行状態を確認して、**データ ツール操作**ウィンドウです。

6. をクリックして**ビュー Reulst**または**スクリプトの表示**SQL Server on Linux での結果を発行、データベースの詳細を確認します。

    <img src="./media/sql-server-linux-develop-use-ssdt/publish-result.png" alt="publish result" style="width: 480px;"/>

Linux 上の SQL Server インスタンスに新しいデータベースを作成し、ソース管理の対象のデータベース プロジェクトを持つデータベースの開発の基本を学習しました。

## <a name="next-steps"></a>次の手順

T-SQL を新しい場合を参照してください[チュートリアル: TRANSACT-SQL ステートメントの記述]と[TRANSACT-SQL リファレンス (データベース エンジン)]です。

SQL Data Tools のデータベースの開発に関する詳細については、次を参照してください[SSDT MSDN ドキュメント。]

[ダウンロードおよび Visual Studio のインストール]:https://www.visualstudio.com/downloads/
[Download and Install SSDT 17.0 RC2]:https://aka.ms/ssdt-download
[SSDT MSDN ドキュメント。]: https://msdn.microsoft.com/en-us/library/hh272686(v=vs.103).aspx
[チュートリアル: TRANSACT-SQL ステートメントの記述]:https://msdn.microsoft.com/library/ms365303.aspx
[TRANSACT-SQL リファレンス (データベース エンジン)]:https://msdn.microsoft.com/library/bb510741.aspx
