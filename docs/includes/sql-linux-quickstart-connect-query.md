## <a name="connect-locally"></a>ローカル接続

次の手順では、**sqlcmd** を使用して新しい SQL Server インスタンスにローカル接続します。

1. **sqlcmd** に SQL Server 名 (-S)、ユーザー名 (-U)、およびパスワード (-P) のパラメーターを指定して実行します。 このチュートリアルでは、ローカルに接続するため、サーバー名は `localhost` です。 ユーザー名は `SA` で、パスワードはセットアップ時に SA アカウントに指定したものです。

   ```bash
   sqlcmd -S localhost -U SA -P '<YourPassword>'
   ```

   > [!TIP]
   > コマンド ラインでパスワードを省略すると、入力を求められます。

   > [!TIP]
   > 後でリモート接続する場合は、**-S** パラメーターとしてコンピューター名または IP アドレスを指定し、ファイアウォールでポート 1433 が開いていることを確認してください。

1. 成功すると、**sqlcmd** コマンド プロンプト `1>` が表示されます。

1. 接続エラーが発生した場合は、まずエラー メッセージから問題を診断します。 次に、[接続のトラブルシューティングに関する推奨事項](../linux/sql-server-linux-troubleshooting-guide.md#connection)を確認します。

## <a name="create-and-query-data"></a>データの作成とクエリ
以下のセクションでは、**sqlcmd** と Transact-SQL を使用して新しいデータベースを作成し、データを追加して簡単なクエリを実行します。

### <a name="create-a-new-database"></a>新しいデータベースの作成

次の手順では、`TestDB` という名前の新しいデータベースを作成します。

1. **sqlcmd** のコマンド プロンプトに次の Transact-SQL コマンドを貼り付け、テスト データベースを作成します。

   ```sql
   CREATE DATABASE TestDB
   ```

1. 次の行に、サーバー上のすべてのデータベースの名前を返すクエリを記述します。

   ```sql
   SELECT Name from sys.Databases
   ```

1. 前の 2 つのコマンドは、すぐに実行されていません。 前のコマンドを実行するには、新しい行に「`GO`」と入力する必要があります。

   ```sql
   GO
   ```

### <a name="insert-data"></a>データの挿入

次に、新しいテーブル `Inventory` を作成し、2 つの新しい行を挿入します。

1. **sqlcmd** のコマンド プロンプトで、コンテキストを新しい `TestDB` データベースに切り替えます。

   ```sql
   USE TestDB
   ```

1. `Inventory` という名前の新しいテーブルを作成します。

   ```sql
   CREATE TABLE Inventory (id INT, name NVARCHAR(50), quantity INT)
   ```

1. 新しいテーブルにデータを挿入します。

   ```sql
   INSERT INTO Inventory VALUES (1, 'banana', 150); INSERT INTO Inventory VALUES (2, 'orange', 154);
   ```

1. 「`GO`」と入力して前のコマンドを実行します。

   ```sql
   GO
   ```

### <a name="select-data"></a>データの選択

ここで、`Inventory` テーブルからデータを返すクエリを実行します。

1. **sqlcmd** のコマンド プロンプトで、`Inventory` テーブルから数量が 152 より大きい行を返すクエリを入力します。

   ```sql
   SELECT * FROM Inventory WHERE quantity > 152;
   ```

1. コマンドを実行します。

   ```sql
   GO
   ```

### <a name="exit-the-sqlcmd-command-prompt"></a>sqlcmd コマンド プロンプトの終了

**sqlcmd** セッションを終了するには、「`QUIT`」と入力します。

```sql
QUIT
```

## <a name="connect-from-windows"></a>Windows からの接続

Windows 上の SQL Server ツールは、あらゆるリモート SQL Server インスタンスへの接続と同じ方法で Linux 上の SQL Server インスタンスに接続するということが重要です。

Linux コンピューターに接続できる Windows コンピューターがある場合は、**sqlcmd** を実行する Windows コマンド プロンプトから、このトピックと同じ手順を試してみてください。 localhost ではなくターゲットの Linux コンピューター名または IP アドレスを使用していることを確認し、TCP ポート 1433 が開いていることを確かめます。 Windows からの接続に問題がある場合は、[接続のトラブルシューティングに関する推奨事項](../linux/sql-server-linux-troubleshooting-guide.md#connection)を参照してください。

Windows で実行し、Linux 上の SQL Server に接続するその他のツールについては、以下を参照してください。

- [SQL Server Management Studio (SSMS)](../linux/sql-server-linux-develop-use-ssms.md)
- [Windows PowerShell](../linux/sql-server-linux-manage-powershell.md)
- [SQL Server Data Tools (SSDT)](../linux/sql-server-linux-develop-use-ssdt.md)

## <a name="next-steps"></a>次の手順

T-SQL を初めて使う場合は、「[Tutorial: Writing Transact-SQL Statements](../t-sql/tutorial-writing-transact-sql-statements.md)」 (チュートリアル: Transact-SQL ステートメントの記述) と「[Transact-SQL Reference (Database Engine)](../t-sql/language-reference.md)」 (Transact-SQL リファレンス (データベース エンジン)) を参照してください。

SQL Server に接続して管理するその他の方法を調べるには、[Visual Studio のコード](../linux/sql-server-linux-develop-use-vscode.md)と [SQL Server Management Studio](../linux/sql-server-linux-develop-use-ssms.md) に関するトピックを参照してください。