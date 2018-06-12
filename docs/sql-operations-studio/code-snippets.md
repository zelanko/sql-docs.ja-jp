---
title: SQL Operations Studio (プレビュー) でコード スニペットを作成 |Microsoft ドキュメント
description: 作成して、SQL Operations Studio (プレビュー) で SQL コード スニペットを使用する方法をについてください。
ms.custom: tools|sos
ms.date: 11/15/2017
ms.reviewer: alayu; sstein
ms.prod: sql
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e8cd2dc80f7a719f82bd4ff09729cbbd5dfb4186
ms.sourcegitcommit: 6fd8a193728abc0a00075f3e4766a7e2e2859139
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="create-and-use-code-snippets-to-quickly-create-transact-sql-t-sql-scripts-in-includename-sosincludesname-sos-shortmd"></a>作成し、迅速で TRANSACT-SQL (T-SQL) スクリプトを作成するコード スニペットを使用します。 [!INCLUDE[name-sos](../includes/name-sos-short.md)]

コード スニペットで[!INCLUDE[name-sos](../includes/name-sos-short.md)]はデータベースとデータベース オブジェクトを作成するテンプレートをより簡単にします。 

[!INCLUDE[name-sos](../includes/name-sos-short.md)] 適切な構文をすばやく生成するに役立ついくつかの T-SQL でスニペットを提供します。 

ユーザー定義のコード スニペットを作成することもできます。

## <a name="using-built-in-t-sql-code-snippets"></a>組み込みの T-SQL コード スニペットを使用します。

1. 使用可能なスニペットにアクセスするには、入力*sql*クエリ エディターを開くには、一覧で。

   ![スニペット](media/code-snippets/sql-snippets.png)

1. を使用するスニペットを選択し、T-SQL スクリプトを生成します。 たとえば、選択*sqlCreateTable*:

   ![テーブルのスニペットを作成します。](media/code-snippets/create-table.png)

1. 強調表示されたフィールドを特定の値に更新します。 たとえば、置き換える*TableName*と*スキーマ*データベースの値を持つ。

   ![テンプレートのフィールドを置き換えます](media/code-snippets/table-from-snippet.png)

   変更するフィールドが強調表示されている場合 (この場合、エディターの周りにカーソルを移動)、変更、および選択する単語を右クリックして**すべて置換**:

   ![テンプレートのフィールドを置き換えます](media/code-snippets/change-all.png)

1. 更新または追加、追加の T-SQL で、選択したスニペットをする必要があります。 たとえば、更新*Column1*、 *Column2*、複数の列を追加します。


 
## <a name="creating-sql-code-snippets"></a>SQL のコード スニペットの作成 

独自のスニペットを定義することができます。 編集するため、SQL のスニペット ファイルを開くには。

1. 開く、*コマンド パレット*(**shift キーを押しながら CTRL + P**)、および種類*切り取り領域*を選択し、**設定: 開いているユーザーのスニペット**:

   ![テンプレートのフィールドを置き換えます](media/code-snippets/user-snippets.png)

1. 選択**SQL**:

   > [!NOTE]
   > [!INCLUDE[name-sos](../includes/name-sos-short.md)] 具体的にはこの記事では SQL スニペットの使用について説明しますので、Visual Studio のコードからそのコード スニペットの機能を継承します。 詳細についてを参照してください。 [、独自のスニペットを作成する](https://code.visualstudio.com/docs/editor/userdefinedsnippets)、Visual Studio Code マニュアルを参照します。 

   ![テンプレートのフィールドを置き換えます](media/code-snippets/select-sql.png)

1. 次のコードを貼り付けます*sql.json*:

   ```sql
   "Select top 5": {
    "prefix": "sqlSelectTop5",
    "body": "SELECT TOP 5 * FROM ${1:TableName}",
    "description": "User-defined snippet example 1"
    },
    "Create Table snippet":{
    "prefix": "sqlCreateTable2",
    "body": [
    "-- Create a new table called '${1:TableName}' in schema '${2:SchemaName}'",
    "-- Drop the table if it already exists",
    "IF OBJECT_ID('$2.$1', 'U') IS NOT NULL",
    "DROP TABLE $2.$1",
    "GO",
    "-- Create the table in the specified schema",
    "CREATE TABLE $2.$1",
    "(",
    "   $1Id INT NOT NULL PRIMARY KEY, -- primary key column",
    "   Column1 [NVARCHAR](50) NOT NULL,",
    "   Column2 [NVARCHAR](50) NOT NULL",
    "   -- specify more columns here",
    ");",
    "GO"
    ],
   "description": "User-defined snippet example 2"
   }
   ```

1. Sql.json ファイルを保存します。
1. クリックして新しいクエリ エディター ウィンドウを開く**Ctrl + N**です。
2. 型**sql**、; 追加した 2 つのユーザーのスニペットを参照してください、*sqlCreateTable2*と*sqlSelectTop5*です。

新しいスニペットのいずれかを選択し、テストの実行を付けます。


## <a name="additional-resources"></a>その他のリソース

SQL エディターの概要については、次を参照してください。[コード エディターのチュートリアル](tutorial-sql-editor.md)です。