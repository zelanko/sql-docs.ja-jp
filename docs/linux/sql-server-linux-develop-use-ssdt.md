---
title: 開発および Linux 用のデータベースを SQL Server の展開 |Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 1e924704-e07c-4a8b-b243-8c1dd8cff0d3
ms.custom: sql-linux
ms.openlocfilehash: 874fd8948d4098e9003fb2c54e1feb8b5cbbe4e3
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52750364"
---
# <a name="use-visual-studio-to-create-databases-for-sql-server-on-linux"></a>Visual Studio を使用して、Linux 上の SQL Server のデータベースを作成するには

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server Data Tools (SSDT) は、Visual Studio を SQL Server on Linux の強力な開発およびデータベース ライフ サイクル管理 (DLM) 環境に変化させます。 アプリケーション コードを開発するのと同じように、ソース管理のプロジェクトからデータベースを開発、構築、テストおよび発行することができます。

## <a name="install-visual-studio-and-sql-server-data-tools"></a>Visual Studio と SQL Server Data Tools をインストールします。

1. 既にインストールしていない Visual Studio、Windows コンピューターの場合[ダウンロードして Visual Studio のインストール]します。 Visual Studio Community エディションは、受講者、完全に機能を備えた無料の IDE、Visual Studio のライセンスがない、オープン ソース、個人の開発者。

2. Visual Studio のインストール中に次のように選択します。**カスタム**の、**インストールの種類を選択**オプション。  **[次へ]** をクリックします。

3. 選択**Microsoft SQL Server Data Tools**、 **Git for Windows**、および**Visual Studio 向け GitHub 拡張**機能の選択項目の一覧。

    <img src="./media/sql-server-linux-develop-use-ssdt/ssdt-setup.png" alt="ssdt setup" style="width: 400px;"/>

4. 続行して、Visual Studio のインストールを完了します。 これには数分かかることができます。

## <a name="upgrade-sql-server-data-tools-to-ssdt-170-rc-release"></a>SQL Server Data Tools を SSDT 17.0 RC リリースにアップグレードします。

Linux 上の SQL Server は、SSDT 17.0 RC またはそれ以降のバージョンによってサポートされます。

* [ダウンロードしてインストール SSDT 17.0 RC2](https://go.microsoft.com/fwlink/?linkid=837939)します。

## <a name="create-a-new-database-project-in-source-control"></a>ソース管理で新しいデータベース プロジェクトを作成します。

1. Visual Studio を起動します。

2. 選択**チーム エクスプ ローラー**上、**ビュー**メニュー。 

3. クリックして**新規**で**ローカル Git リポジトリ**セクションで、 **Connect**ページ。

    <img src="./media/sql-server-linux-develop-use-ssdt/git-repository.png" alt="local repository" style="width: 300px;"/>

3. **[作成]** をクリックします。 ローカルの Git リポジトリが作成されると、ダブルクリック**SSDTRepo**します。

4. クリックして**新規**で、**ソリューション**セクション。 選択**SQL Server** **他の言語**内のノード、**新しいプロジェクト**ダイアログ。

    <img src="./media/sql-server-linux-develop-use-ssdt/new-project.png" alt="local repository" style="width: 480px;"/>

5. 入力**TutorialDB**クリックと名前の **[ok]** 新しいデータベース プロジェクトを作成します。

## <a name="create-a-new-table-in-the-database-project"></a>データベース プロジェクトに新しいテーブルを作成します。

1. 選択**ソリューション エクスプ ローラー**上、**ビュー**メニュー。

2. 右クリックし、データベース プロジェクト メニューを開いて**TutorialDB**ソリューション エクスプ ローラーでします。

3. 選択**テーブル** **追加**します。

    <img src="./media/sql-server-linux-develop-use-ssdt/create-table.png" alt="create table" style="width: 480px;"/>

4. テーブル デザイナーを使用して、2 つの列名を追加`nvarchar(50)`と場所`nvarchar(50)`の図に示すようにします。 SSDT の生成、`CREATE TABLE`デザイナーで列を追加するときのスクリプトを作成します。

    <img src="./media/sql-server-linux-develop-use-ssdt/add-columns.png" alt="add columns" style="width: 480px;"/>

5. 保存、 **Table1.sql**ファイル。

## <a name="build-and-validate-the-database"></a>ビルドして、データベースの検証

1. データベース プロジェクト メニューを開く**TutorialDB**選択と**ビルド**します。 SSDT では、プロジェクトに .sql のソース コード ファイルをコンパイルし、データ層アプリケーション パッケージ (dacpac) ファイルのビルドします。 Linux 上の SQL Server インスタンスにデータベースをパブリッシュするために使用できます。 

    <img src="./media/sql-server-linux-develop-use-ssdt/build.png" alt="add columns" style="width: 400px;"/>

2. ビルドの成功メッセージをチェックイン**出力**Visual Studio のウィンドウ。 

## <a name="publish-the-database-to-sql-server-instance-on-linux"></a>Linux 上の SQL Server インスタンスにデータベースをパブリッシュします。

1. データベース プロジェクト メニューを開く**TutorialDB**選択**発行**します。

2. クリックして**編集**on Linux で、SQL Server インスタンスを選択します。

    <img src="./media/sql-server-linux-develop-use-ssdt/publish-dialog.png" alt="publish dialog" style="width: 480px;"/>

3. [接続] ダイアログでは、Linux、ユーザー名とパスワードで SQL Server インスタンスの IP アドレスまたはホスト名に入力します。

    <img src="./media/sql-server-linux-develop-use-ssdt/connection-dialog.png" alt="connection dialog" style="width: 400px;"/>

4. をクリックして、**発行**発行 ダイアログ ボックスのボタンをクリックします。

5. 発行状態を確認、**データ ツール操作**ウィンドウ。

6. をクリックして**結果を表示する**または**スクリプトの表示**SQL Server on Linux での結果を発行データベースの詳細を確認します。

    <img src="./media/sql-server-linux-develop-use-ssdt/publish-result.png" alt="publish result" style="width: 480px;"/>

Linux 上の SQL Server インスタンスに新しいデータベースを作成し、ソース管理の対象のデータベース プロジェクトへのデータベース開発の基本を学習できました。

## <a name="next-steps"></a>次の手順

T-SQL に慣れていない場合は、次を参照してください。[チュートリアル:TRANSACT-SQL ステートメントの作成]と[TRANSACT-SQL リファレンス (データベース エンジン)]します。

SQL Data Tools でのデータベース開発の詳細については、次を参照してください[SSDT MSDN ドキュメント]

[ダウンロードして Visual Studio のインストール]:https://www.visualstudio.com/downloads/
[Download and Install SSDT]:https://aka.ms/ssdt-download
[SSDT MSDN ドキュメント]: https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx
[チュートリアル:TRANSACT-SQL ステートメントの作成]:https://msdn.microsoft.com/library/ms365303.aspx
[TRANSACT-SQL リファレンス (データベース エンジン)]:https://msdn.microsoft.com/library/bb510741.aspx
