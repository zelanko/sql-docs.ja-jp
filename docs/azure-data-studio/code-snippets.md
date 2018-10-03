---
title: Azure Data Studio でコード スニペットの作成 |Microsoft Docs
description: 作成して Azure Data Studio で SQL コード スニペットを使用する方法について説明します
ms.custom: tools|sos
ms.date: 09/24/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.prod_service: sql-tools
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e24d1adc2c6a77d8416d63e205abc3c6c3e2f872
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "48039020"
---
# <a name="create-and-use-code-snippets-to-quickly-create-transact-sql-t-sql-scripts-in-includename-sosincludesname-sos-shortmd"></a>作成し、コード スニペットを使用して、迅速で TRANSACT-SQL (T-SQL) スクリプトを作成するには [!INCLUDE[name-sos](../includes/name-sos-short.md)]

コード スニペットで[!INCLUDE[name-sos](../includes/name-sos-short.md)]データベースおよびデータベース オブジェクトに簡単にテンプレートが作成されます。 

[!INCLUDE[name-sos](../includes/name-sos-short.md)] 適切な構文をすばやく生成する際のいくつかの T-SQL スニペットを提供します。 

ユーザー定義のコード スニペットを作成することもできます。

## <a name="using-built-in-t-sql-code-snippets"></a>組み込みの T-SQL コード スニペットを使用します。

1. 使用可能なスニペットにアクセスするには、入力*sql*クエリ エディターの一覧を開きます。

   ![スニペット](media/code-snippets/sql-snippets.png)

1. 使用するには、必要なスニペットを選択し、T-SQL スクリプトを生成します。 たとえば、 *sqlCreateTable*:

   ![テーブルのスニペットを作成します。](media/code-snippets/create-table.png)

1. 特定の値で強調表示されたフィールドを更新します。 たとえば、置き換える*TableName*と*スキーマ*データベースの値に置き換えます。

   ![テンプレートのフィールドを置き換えます](media/code-snippets/table-from-snippet.png)

   変更するフィールドが強調表示されている場合 (このようなエディターの周りにカーソルを移動する場合) を変更して、選択する単語を右クリックして**出現箇所をすべて**:

   ![テンプレートのフィールドを置き換えます](media/code-snippets/change-all.png)

1. 更新するか、選択したスニペットは、必要な追加 T-SQL を追加します。 たとえば、更新*Column1*、 *Column2*、多くの列を追加します。


 
## <a name="creating-sql-code-snippets"></a>SQL コード スニペットの作成 

独自のスニペットを定義することができます。 編集するための SQL スニペット ファイルを開く。

1. 開く、*コマンド パレット*(**Shift + Ctrl + P**)、および種類*切り取り領域*を選択し、**の基本設定: オープン ユーザー スニペット**:

   ![テンプレートのフィールドを置き換えます](media/code-snippets/user-snippets.png)

1. 選択**SQL**:

   > [!NOTE]
   > [!INCLUDE[name-sos](../includes/name-sos-short.md)] 具体的にはこの記事では SQL スニペットの使用について説明しますので、Visual Studio Code からそのコード スニペット機能を継承します。 詳細についてを参照してください。 [、独自のスニペットを作成する](https://code.visualstudio.com/docs/editor/userdefinedsnippets)、Visual Studio Code のドキュメント。 

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
1. 新しいクエリ エディター ウィンドウを開きます**Ctrl + N**します。
2. 型**sql**と追加した 2 つのユーザーのスニペットを参照してください。*sqlCreateTable2*と*sqlSelectTop5*します。

新しいスニペットのいずれかを選択し、テストの実行を付けます。


## <a name="additional-resources"></a>その他のリソース

SQL エディターの詳細については、次を参照してください。[コード エディターのチュートリアル](tutorial-sql-editor.md)します。
