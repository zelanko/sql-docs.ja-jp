---
title: SQL Server インポート拡張機能
titleSuffix: Azure Data Studio
description: インストールして Azure Data Studio の SQL Server インポート拡張機能 (プレビュー) を使用
ms.custom: seodec18
ms.date: 09/24/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: 012c2c880e81c095e90086cf26ebffd6117d534e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959121"
---
# <a name="sql-server-import-extension-preview"></a>SQL Server インポート拡張機能 (プレビュー)

SQL Server インポート拡張機能 (プレビュー) は、.txt、.csv ファイルを SQL テーブルに変換します。 このウィザードと呼ばれる Microsoft Research のフレームワークを利用して[Program Synthesis using 例 (PROSE)](https://microsoft.github.io/prose/)をインテリジェントに最小限のユーザー入力を使用してファイルを解析します。 これは、データの処理の強力なフレームワークと、Microsoft Excel で Flash Fill が作動するのと同じテクノロジが

この機能の SSMS のバージョンに関する詳細についてを参照して[今回](https://docs.microsoft.com/sql/relational-databases/import-export/import-flat-file-wizard)します。


## <a name="install-the-sql-server-import-extension"></a>SQL Server インポート拡張機能をインストールします。

1. 拡張機能マネージャーを開き、使用可能な拡張機能にアクセスするには、拡張機能 アイコンを選択するか、**ビュー**メニューの**拡張**を選択します。
2. 詳細を表示する使用可能な拡張機能を選択します。

   ![インポートの拡張機能マネージャー](media/sql-server-import-extension/import-wizard-install.png)

1. 必要な拡張機能を選択し、**インストール**します。
2. **再読み込み**を選択して拡張機能を有効にします(初めて拡張機能をインストールするときのみ必要です)。

## <a name="start-import-wizard"></a>インポート ウィザードを起動します。

1. SQL Server インポートを開始するには、[サーバー] タブで、サーバーへの接続をまず確認します。
2. 接続を確立した後は、SQL テーブルにファイルをインポートするターゲット データベースにドリルダウンします。
3. データベースを右クリックし、をクリックして**のインポート ウィザード**します。
    ![オープンのインポート ウィザード](media/sql-server-import-extension/open-import-wizard.png)

## <a name="importing-a-file"></a>ファイルをインポートします。
1. ウィザードを起動する右クリックすると、サーバーとデータベースは既に自動的に入力します。 その他のアクティブな接続がある場合は、ドロップダウン リストで選択できます。 
    
    クリックすると、ファイルを選択**参照します。** 自動入力ファイルの名前に基づいて、テーブル名が必要がありますが、変更することも、自分でします。

    既定では、スキーマ dbo になりますが、これを変更することができます。 **[次へ]** をクリックします。
    ![入力ファイル](media/sql-server-import-extension/import-wizard-input-file.png)
1. ウィザードでは、最初の 50 行に基づくプレビューを生成します。 このページで、追加の操作の他のデータの正確な表示形式を確認するより、 **[次へ]** をクリックします。
    ![オープンのインポート ウィザード](media/sql-server-import-extension/import-wizard-preview-data.png)
2. このページで、ことができますを変更する列名、データ型は、プライマリ キーまたは、null を許可するかどうか。 好きなように、多くの変更を行うことができます。 クリックして**データのインポート**を続行します。
    ![オープンのインポート ウィザード](media/sql-server-import-extension/import-wizard-modify-columns.png)
3. このページには、選択した操作の概要が表示されます。 テーブルが正常に挿入かどうかもわかります。 

    クリックするか**完了前**、変更を行う必要がある場合または**新しいファイルのインポート**をすばやく別のファイルをインポートします。
    ![オープンのインポート ウィザード](media/sql-server-import-extension/import-wizard-summary.png)
1. テーブルが、対象のデータベースを更新またはテーブル名で SELECT クエリを実行して正常にインポートを確認します。

## <a name="next-steps"></a>次の手順
- インポート ウィザードの詳細については、読み取り、[ブログの投稿](https://cloudblogs.microsoft.com/sqlserver/2018/08/30/the-august-release-of-sql-operations-studio-is-now-available/)します。
- PROSE の詳細については、読み取り、[ドキュメント。](https://microsoft.github.io/prose/)
