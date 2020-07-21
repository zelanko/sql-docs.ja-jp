---
title: SQL Database プロジェクトの拡張機能
description: Azure Data Studio の SQL Database プロジェクトの拡張機能 (プレビュー) をインストールして使用する
ms.custom: seodec18
ms.date: 06/25/2020
ms.reviewer: drskwier, maghan, sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: dzsquared
ms.author: drskwier
ms.openlocfilehash: 609af04cec2f6eaaaf1890e19c6d85fbd4bd5b8a
ms.sourcegitcommit: b860fe41b873977649dca8c1fd5619f294c37a58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2020
ms.locfileid: "85519171"
---
# <a name="sql-database-projects-extension-preview"></a>SQL Database プロジェクトの拡張機能 (プレビュー)

SQL Database プロジェクトの拡張機能 (プレビュー) は、プロジェクトベースの開発環境で SQL データベースを開発するための拡張機能です。 この拡張機能は現在プレビュー段階であり、[Azure Data Studio Insider Build](https://github.com/microsoft/azuredatastudio#try-out-the-latest-insiders-build-from-main) で使用できます。


## <a name="install-the-sql-database-projects-extension"></a>SQL Database プロジェクトの拡張機能をインストールする

1. 拡張機能マネージャーを開いて、使用可能な拡張機能にアクセスするには、拡張機能アイコンを選択するか、 **[表示]** メニューの **[拡張機能]** を選択します。
2. 拡張機能の検索ボックスに名前の一部または全部を入力して、"*SQL Database プロジェクト*" の拡張機能を特定します。 使用可能な拡張機能を選択すると、その詳細が表示されます。

   ![拡張機能のインストール](media/extensions/sql-database-projects-extension/install-database-projects.png)

3. 必要な拡張機能を選択して**インストール**します。
4. **[再読み込み]** を選択して拡張機能を有効にします (拡張機能を初めてインストールするときにのみ必要です)。
5. アクティビティ バーから [ファイル] アイコンを選択するか、 **[表示]** メニューから **[エクスプローラー]** を選択します。 **プロジェクト**用の新しい viewlet が使用できるようになりました。

   > [!NOTE]
   > すべての機能を使用するには、SQL Database プロジェクトの拡張機能と共に [Schema Compare の拡張機能](schema-compare-extension.md)をインストールすることをお勧めします。

## <a name="getting-started-with-database-projects"></a>データベース プロジェクトの概要

* 新しいデータベース プロジェクトを作成するには、エクスプローラーの下の **プロジェクト** viewlet に移動するか、コマンド パレットで**新しいデータベース プロジェクト**を検索します。
* 既存のデータベース プロジェクトは、コマンド パレットで **[Open Database Project]\(データベース プロジェクトを開く\)** を使用して開くことができます。
* コマンド パレットから **[Import New Database Project]\(新しいデータベース プロジェクトをインポート\)** を使用して、既存のデータベースから開始します。

   ![新しい viewlet](media/extensions/sql-database-projects-extension/projects-viewlet.png)


### <a name="create-an-empty-database-project"></a>空のデータベース プロジェクトを作成する

 **エクスプローラー**の下の**プロジェクト** viewlet で、 **[新しいプロジェクト]** ボタンをクリックし、表示されるテキスト入力にプロジェクト名を入力します。  表示される [フォルダーの選択] ダイアログ ボックスで、プロジェクトのフォルダー、.sqlproj ファイル、およびそこに含まれるその他の内容を選択します。
空のプロジェクトが開き、編集のために **プロジェクト** viewlet に表示されます。

### <a name="open-an-existing-project"></a>既存のプロジェクトを開く

**プロジェクト** viewlet で、 **[プロジェクトを開く]** ボタンをクリックし、表示されたファイル ピッカーから既存の *.sqlproj* ファイルを開きます。 既存のプロジェクトは、Azure Data Studio または [Visual Studio SQL Server Data Tools](../ssdt/sql-server-data-tools.md) から作成できます。

既存のプロジェクトが開かれ、編集のためにその内容が **プロジェクト** viewlet に表示されます。

### <a name="create-a-database-project-from-an-existing-database"></a>既存のデータベースからデータベース プロジェクトを作成する

**プロジェクト** viewlet で、 **[Import Project from Database]\(データベースからプロジェクトをインポート\)** ボタンをクリックして SQL Server に接続します。  接続が確立されたら、使用可能なデータベースのリストからデータベースを選択し、プロジェクトの名前を設定します。

最後に、抽出のターゲット構造を選択します。  新しいプロジェクトが開き、選択したデータベースの内容に対応する SQL スクリプトが含まれます。

## <a name="build-and-publish"></a>ビルドして発行する

データベース プロジェクトのデプロイは、Azure Data Studio の SQL Database プロジェクトの拡張機能でプロジェクトを[データ層アプリケーション ファイル](../relational-databases/data-tier-applications/data-tier-applications.md) (DACPAC) にビルドし、サポートされているプラットフォームに発行することで実現されます。 このプロセスの詳細については、「[プロジェクトをビルドして発行する](sql-database-project-extension-build.md)」を参照してください。

## <a name="schema-compare"></a>スキーマ比較
SQL Database プロジェクトの拡張機能は、[Schema Compare の拡張機能](schema-compare-extension.md)がインストールされている場合はそれとやり取りして、プロジェクトの内容を dacpac または既存のデータベースと比較します。  結果として得られるスキーマ比較を使用して、ソースとターゲットの違いを表示し、適用することができます。

## <a name="next-steps"></a>次のステップ

- [Azure Data Studio の SQL Database プロジェクトの拡張機能を使用してプロジェクトをビルドして発行する](sql-database-project-extension-build.md)
- [データ層アプリケーション](../relational-databases/data-tier-applications/data-tier-applications.md)