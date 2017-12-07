---
title: "データを一括コピーする SQL Server on Linux |Microsoft ドキュメント"
description: 
author: sanagama
ms.author: sanagama
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 7b93d0d7-7946-4b78-b33a-57d6307cdfa9
ms.workload: On Demand
ms.openlocfilehash: a6c760a78894dbda62320da0f8e59ed1aa3f2bcf
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="bulk-copy-data-with-bcp-to-sql-server-on-linux"></a>SQL Server on Linux に bcp を使用したデータの一括コピー

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

このトピックの内容を使用する方法を示しています、 [bcp](../tools/bcp-utility.md) Linux 上の SQL Server 2017 のインスタンスと、ユーザー指定の形式でデータ ファイル間でデータの一括コピーするコマンド ライン ユーティリティです。

使用することができます`bcp`SQL Server テーブルに大量の行をインポートする、または SQL Server テーブルからデータ ファイルにデータをエクスポートします。 Queryout オプションと共に使用する場合を除く`bcp`TRANSACT-SQL の知識は必要ありません。 `bcp`コマンド ライン ユーティリティは、内部設置型を実行する Microsoft SQL Server または Linux、Windows または Docker と Azure SQL Database および Azure SQL Data Warehouse でのクラウドで動作します。

このトピック方法を説明します。
- 使用してテーブルにデータをインポート、`bcp in`コマンド
- テーブルの使用からデータをエクスポート、`bcp out`コマンド

## <a name="install-the-sql-server-command-line-tools"></a>SQL Server コマンド ライン ツールをインストールします。

`bcp`SQL Server on Linux で自動的にインストールされていない SQL Server コマンド ライン ツールの一部です。 場合は、SQL Server コマンド ライン ツールを Linux コンピューターに既にインストールしていない、インストールする必要があります。 ツールをインストールする方法の詳細については、次の一覧から、ディストリビューションを選択します。

- [Red Hat Enterprise Linux (RHEL)](sql-server-linux-setup-tools.md#RHEL)
- [Ubuntu](sql-server-linux-setup-tools.md#ubuntu)
- [SUSE Linux Enterprise Server (SLES)](sql-server-linux-setup-tools.md#SLES)

## <a name="import-data-with-bcp"></a>Bcp を使用したデータのインポート

このチュートリアルでは作成するサンプル データベースとテーブル ローカルの SQL Server インスタンス上 (**localhost**) をクリックして`bcp`ディスク上のテキスト ファイルからサンプル テーブルを読み込む。

### <a name="create-a-sample-database-and-table"></a>サンプル データベースとテーブルを作成します。

このチュートリアルの残りの部分で使用される単純なテーブルのサンプル データベースを作成して開始しましょう。

1. Linux マシンでは、コマンド ターミナルを開きます。

2. コピーし、ターミナル ウィンドウに次のコマンドを貼り付けます。 これらのコマンドを使用して、 **sqlcmd**サンプル データベースを作成するコマンド ライン ユーティリティ (**BcpSampleDB**) と、テーブル (**TestEmployees**) ローカルの SQL Server インスタンスに (**localhost**)。 置き換えます、`username`と`<your_password>`コマンドを実行する前に必要に応じて。

データベースを作成**BcpSampleDB**:
```bash 
sqlcmd -S localhost -U sa -P <your_password> -Q "CREATE DATABASE BcpSampleDB;"
```
テーブルを作成**TestEmployees**データベース**BcpSampleDB**:
```bash 
sqlcmd -S localhost -U sa -P <your_password> -d BcpSampleDB -Q "CREATE TABLE TestEmployees (Id INT IDENTITY(1,1) NOT NULL PRIMARY KEY, Name NVARCHAR(50), Location NVARCHAR(50));"
```
### <a name="create-the-source-data-file"></a>元のデータ ファイルを作成します。
コピーし、ターミナル ウィンドウで、以下のコマンドを貼り付けます。 組み込みを使用して`cat`3 個のレコードでサンプル テキスト データ ファイルを作成するコマンドと、ホーム ディレクトリにファイルを保存する**~/test_data.txt**です。 レコードのフィールドはコンマで区切られます。

```bash
cat > ~/test_data.txt << EOF
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
EOF
```

ターミナル ウィンドウで、以下のコマンドを実行して、データ ファイルが正しく作成されたことを確認することができます。
```bash 
cat ~/test_data.txt
```

これにより、ターミナル ウィンドウで、次が表示する必要があります。
```bash
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
```

### <a name="import-data-from-the-source-data-file"></a>元のデータ ファイルからデータをインポートします。
コピーし、ターミナル ウィンドウに次のコマンドを貼り付けます。 このコマンドを使用して`bcp`ローカルの SQL Server インスタンスに接続する (**localhost**)、データ ファイルからデータをインポートし、(**~/test_data.txt**) テーブルに (**TestEmployees**) データベースに (**BcpSampleDB**)。 ユーザー名を置き換えますと`<your_password>`コマンドを実行する前に必要に応じて。

```bash 
bcp TestEmployees in ~/test_data.txt -S localhost -U sa -P <your_password> -d BcpSampleDB -c -t  ','
```

使用してコマンド ライン パラメーターの概要を次に示します`bcp`この例では。
- `-S`: 接続先の SQL Server のインスタンスを指定します
- `-U`: ID が SQL Server への接続に使用するログインを指定します
- `-P`: ログイン ID のパスワードを指定します。
- `-d`: データベースへの接続を指定します
- `-c`: の文字データ型を使用して操作を実行します
- `-t`: フィールド ターミネータを指定します。 使用している`comma`データ ファイル内のレコードのフィールド ターミネータとして

> [!NOTE]
> ユーザー設定の行終端記号を指定して、この例ではおは限りません。 テキスト データ ファイル内の行で正常に終了された`newline`使用したときに、`cat`前に、データ ファイルを作成するコマンド。

データが、ターミナル ウィンドウで、以下のコマンドを実行して正常にインポートされたことを確認することができます。 置き換えます、`username`と`<your_password>`コマンドを実行する前に必要に応じて。
```bash 
sqlcmd -S localhost -d BcpSampleDB -U sa -P <your_password> -I -Q "SELECT * FROM TestEmployees;"
```

これにより、次の結果が表示する必要があります。
```bash
Id          Name                Location
----------- ------------------- -------------------
          1 Jared               Australia
          2 Nikita              India
          3 Tom                 Germany

(3 rows affected)
```

## <a name="export-data-with-bcp"></a>Bcp を使用したデータのエクスポート

このチュートリアルでは使用して`bcp`を新しいデータ ファイルに以前に作成したサンプル テーブルからデータをエクスポートします。

コピーし、ターミナル ウィンドウに次のコマンドを貼り付けます。 これらのコマンドを使用して、`bcp`テーブルからデータをエクスポートするコマンド ライン ユーティリティ**TestEmployees**で、データベースに**BcpSampleDB**と呼ばれる新しいデータ ファイルに**~/test_export.txt**です。  ユーザー名を置き換えますと`<your_password>`コマンドを実行する前に必要に応じて。

```bash 
bcp TestEmployees out ~/test_export.txt -S localhost -U sa -P <your_password> -d BcpSampleDB -c -t ','
```

データが、ターミナル ウィンドウで、以下のコマンドを実行して正しくエクスポートされたことを確認することができます。
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
- [BULK INSERT を使用してデータを一括インポート](../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)
- [一括挿入 (TRANSACT-SQL)](../t-sql/statements/bulk-insert-transact-sql.md)
