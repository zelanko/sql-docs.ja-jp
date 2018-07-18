---
title: Linux 上の SQL Server にデータのコピーを一括 |Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 01/30/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 7b93d0d7-7946-4b78-b33a-57d6307cdfa9
ms.openlocfilehash: d792a7dfd4481d5c5cce3e2517559dcb0b3e22be
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37984169"
---
# <a name="bulk-copy-data-with-bcp-to-sql-server-on-linux"></a>SQL Server on Linux に bcp を使用したデータの一括コピー

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、使用する方法を示します、 [bcp](../tools/bcp-utility.md)コマンド ライン ユーティリティを SQL Server 2017 on Linux のインスタンスと、ユーザー指定の形式でデータ ファイルのデータの一括コピーします。

使用することができます`bcp`SQL Server テーブルに大量の行をインポートするか、SQL Server テーブルからデータをデータ ファイルにエクスポートします。 Queryout オプションと共に使用する場合を除く`bcp`Transact SQL の知識は必要ありません。 `bcp`コマンド ライン ユーティリティで、オンプレミスで実行されている Microsoft SQL Server または Linux、Windows または Docker と Azure SQL Database および Azure SQL Data Warehouse では、クラウドでの動作します。

この記事で取り上げるテクニック:
- 使用してテーブルにデータをインポート、`bcp in`コマンド
- 使用してテーブルからデータをエクスポート、`bcp out`コマンド

## <a name="install-the-sql-server-command-line-tools"></a>SQL Server コマンド ライン ツールをインストールします。

`bcp` SQL Server on Linux で自動的にインストールされていない SQL Server コマンド ライン ツールの一部です。 SQL Server コマンド ライン ツールを Linux コンピューターに既にインストールしていない、それらをインストールする必要があります。 ツールをインストールする方法の詳細については、次の一覧から、Linux ディストリビューションを選択します。

- [Red Hat Enterprise Linux (RHEL)](sql-server-linux-setup-tools.md#RHEL)
- [Ubuntu](sql-server-linux-setup-tools.md#ubuntu)
- [SUSE Linux Enterprise Server (SLES)](sql-server-linux-setup-tools.md#SLES)

## <a name="import-data-with-bcp"></a>Bcp を使用したデータのインポート

このチュートリアルで作成するサンプル データベースとテーブルをローカルの SQL Server インスタンスで (**localhost**) をクリックして`bcp`ディスク上のテキスト ファイルからサンプル テーブルに読み込む。

### <a name="create-a-sample-database-and-table"></a>サンプル データベースとテーブルを作成します。

このチュートリアルの残りの部分で使用されている単純なテーブルにサンプル データベースを作成してみましょう。

1. Linux ボックスでは、コマンド ターミナルを開きます。

2. コピーして、ターミナル ウィンドウに、次のコマンドを貼り付けます。 これらのコマンドを使用して、 **sqlcmd**サンプル データベースを作成するコマンド ライン ユーティリティ (**BcpSampleDB**) とテーブル (**TestEmployees**) ローカルの SQL Server インスタンス (上**localhost**)。 置き換えてください、`username`と`<your_password>`に応じてコマンドを実行する前にします。

データベースを作成**BcpSampleDB**:
```bash 
sqlcmd -S localhost -U sa -P <your_password> -Q "CREATE DATABASE BcpSampleDB;"
```
テーブルを作成する**TestEmployees**データベース**BcpSampleDB**:
```bash 
sqlcmd -S localhost -U sa -P <your_password> -d BcpSampleDB -Q "CREATE TABLE TestEmployees (Id INT IDENTITY(1,1) NOT NULL PRIMARY KEY, Name NVARCHAR(50), Location NVARCHAR(50));"
```
### <a name="create-the-source-data-file"></a>ソース データ ファイルを作成します。
コピーして、ターミナル ウィンドウに次のコマンドを貼り付けます。 使用して、組み込み`cat`サンプル テキスト データ ファイルを 3 つのレコードを作成するコマンドと、ホーム ディレクトリにファイルを保存する **~/test_data.txt**します。 レコードのフィールドはコンマで区切られます。

```bash
cat > ~/test_data.txt << EOF
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
EOF
```

ターミナル ウィンドウで、次のコマンドを実行して、データ ファイルが正しく作成されたことを確認することができます。
```bash 
cat ~/test_data.txt
```

これにより、ターミナル ウィンドウで、次が表示する必要があります。
```bash
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
```

### <a name="import-data-from-the-source-data-file"></a>データ ソースのデータ ファイルからインポートします。
コピーして、ターミナル ウィンドウに、次のコマンドを貼り付けます。 このコマンドを使用して`bcp`ローカルの SQL Server インスタンスに接続する (**localhost**)、データ ファイルからデータをインポートし、(**~/test_data.txt**) テーブルに (**TestEmployees**) データベースに (**BcpSampleDB**)。 ユーザー名に置き換えてくださいと`<your_password>`に応じてコマンドを実行する前にします。

```bash 
bcp TestEmployees in ~/test_data.txt -S localhost -U sa -P <your_password> -d BcpSampleDB -c -t  ','
```

使用しましたコマンド ライン パラメーターの概要を次に示します`bcp`この例では。
- `-S`: 接続先となる SQL Server のインスタンスを指定します
- `-U`: ID が SQL Server への接続に使用するログインを指定します
- `-P`: ログイン ID のパスワードを指定します。
- `-d`: 接続先のデータベースを指定します
- `-c`: 文字データ型を使用して操作を実行します
- `-t`: フィールド ターミネータを指定します。 使用している`comma`データ ファイル内のレコードのフィールド ターミネータとして

> [!NOTE]
> この例ではカスタムの行終端記号が指定されていません。 テキストのデータ ファイル内の行で正常に終了された`newline`使用して、`cat`前に、データ ファイルを作成するコマンド。

データが、ターミナル ウィンドウで、次のコマンドを実行して正常にインポートされたことを確認することができます。 置き換えてください、`username`と`<your_password>`に応じてコマンドを実行する前にします。
```bash 
sqlcmd -S localhost -d BcpSampleDB -U sa -P <your_password> -I -Q "SELECT * FROM TestEmployees;"
```

これは、次の結果を表示する必要があります。
```bash
Id          Name                Location
----------- ------------------- -------------------
          1 Jared               Australia
          2 Nikita              India
          3 Tom                 Germany

(3 rows affected)
```

## <a name="export-data-with-bcp"></a>Bcp を使用したデータのエクスポート

このチュートリアルで使用する`bcp`新しいデータ ファイルに以前に作成したサンプル テーブルからデータをエクスポートします。

コピーして、ターミナル ウィンドウに、次のコマンドを貼り付けます。 これらのコマンドを使用して、`bcp`テーブルからデータをエクスポートするコマンド ライン ユーティリティ**TestEmployees**データベース**BcpSampleDB**と呼ばれる新しいデータ ファイルに **~/test_export.txt**.  ユーザー名に置き換えてくださいと`<your_password>`に応じてコマンドを実行する前にします。

```bash 
bcp TestEmployees out ~/test_export.txt -S localhost -U sa -P <your_password> -d BcpSampleDB -c -t ','
```

ターミナル ウィンドウで、次のコマンドを実行して、データが正しくエクスポートされたことを確認することができます。
```bash 
cat ~/test_export.txt
```

これにより、ターミナル ウィンドウで、次が表示する必要があります。
```
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
```

## <a name="see-also"></a>参照
- [bcp ユーティリティ](../tools/bcp-utility.md)
- [Bcp を使用した互換性のためのデータの形式](../relational-databases/import-export/specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)
- [一括挿入を使用した一括データのインポート](../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)
- [一括挿入 (TRANSACT-SQL)](../t-sql/statements/bulk-insert-transact-sql.md)
