---
title: FILESTREAM データ
description: FILESTREAM 属性によって SQL Server 2008 に格納されている大きな値のデータを操作する方法について説明します。
ms.date: 08/15/2019
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: e3e26a76522d1c1a99794076c5f152e6ec1e1f7d
ms.sourcegitcommit: 610e49c3e1fa97056611a85e31e06ab30fd866b1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/07/2020
ms.locfileid: "78896740"
---
# <a name="filestream-data"></a>FILESTREAM データ

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

FILESTREAM ストレージ属性は、varbinary(max) 列に格納されているバイナリ (BLOB) データ用です。 FILESTREAM 以前は、バイナリデータの格納に特別な処理が必要でした。 テキスト ドキュメント、画像、ビデオなどの非構造化データは、多くの場合にデータベースの外部に格納されるため、管理が困難になります。

> [!NOTE]
> SqlClient を使用して FILESTREAM データを操作するには、.NET Framework 3.5 SP1 (またはそれ以降) または .NET Core をインストールする必要があります。

varbinary(max) 列に FILESTREAM 属性を指定すると、SQL Server では、データがデータベース ファイルではなくローカルの NTFS ファイル システムに保存されます。 データは個別に保存されますが、データベースに保存されている varbinary(max) データの操作をサポートする同じ Transact-SQL ステートメントを使用できます。

## <a name="sqlclient-support-for-filestream"></a>SqlClient による FILESTREAM のサポート

Microsoft SqlClient Data Provider for SQL Server <xref:Microsoft.Data.SqlClient> は、<xref:System.Data.SqlTypes> 名前空間に定義された <xref:Microsoft.Data.SqlTypes.SqlFileStream> クラスを使用して、FILESTREAM データからの読み取りと FILESTREAM データへの書き込みをサポートします。 `SqlFileStream` は <xref:System.IO.Stream> クラスから継承されます。このクラスには、データのストリームの読み取りと書き込みのためのメソッドがあります。 ストリームからの読み取りでは、データをストリームからバイト配列などのデータ構造に転送します。 書き込みでは、データをデータ構造からストリームに転送します。

### <a name="creating-the-sql-server-table"></a>SQL Server テーブルの作成

次の Transact-SQL ステートメントによって、従業員の名前の付いたテーブルが作成され、データ行が挿入されます。 FILESTREAM ストレージを有効にしたら、このテーブルを以下のコード例と組み合わせて使用できます。 SQL Server オンライン ブックの関連トピックへのリンクは、このトピックの終わりにあります。

```sql
CREATE TABLE employees
(
  EmployeeId INT  NOT NULL  PRIMARY KEY,
  Photo VARBINARY(MAX) FILESTREAM  NULL,
  RowGuid UNIQUEIDENTIFIER  NOT NULL  ROWGUIDCOL
  UNIQUE DEFAULT NEWID()
)
GO
Insert into employees
Values(1, 0x00, default)
GO
```

### <a name="example-reading-overwriting-and-inserting-filestream-data"></a>例:FILESTREAM データの読み取り、上書き、および挿入

次のサンプルは、FILESTREAM からデータを読み取る方法を示しています。 このコードでは、ファイルへの論理パスを取得し、`FileAccess` を `Read` に、`FileOptions` を `SequentialScan` に設定します。 次に、コードが SqlFileStream からバッファーにバイトを読み取ります。 次に、バイトがコンソール ウィンドウに書き込まれます。

さらに、このサンプルでは、既存のすべてのデータが上書きされる FILESTREAM にデータを書き込む方法も示しています。 このコードでは、ファイルへの論理パスを取得し、`SqlFileStream` を作成して、`FileAccess` を `Write` に、`FileOptions` を `SequentialScan` に設定します。 1 バイトが `SqlFileStream` に書き込まれ、ファイル内のすべてのデータが置き換えられます。

このサンプルはまた、Seek メソッドを使用してデータをファイルの末尾に追加することによって、データを FILESTREAM に書き込む方法を示しています。 このコードでは、ファイルへの論理パスを取得し、`SqlFileStream` を作成して、`FileAccess` を `ReadWrite` に、`FileOptions` を `SequentialScan` に設定します。 このコードは、Seek メソッドを使用してファイルの末尾までシークし、既存のファイルに 1 バイトを追加します。

```csharp
using System;
using Microsoft.Data.SqlClient;
using System.Data.SqlTypes;
using System.Data;
using System.IO;

namespace FileStreamTest
{
    class Program
    {
        static void Main(string[] args)
        {
            SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder("server=(local);integrated security=true;database=myDB");
            ReadFileStream(builder);
            OverwriteFileStream(builder);
            InsertFileStream(builder);

            Console.WriteLine("Done");
        }

        private static void ReadFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for the file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        // Create the SqlFileStream
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Read, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Read the contents as bytes and write them to the console
                            for (long index = 0; index < fileStream.Length; index++)
                            {
                                Console.WriteLine(fileStream.ReadByte());
                            }
                        }
                    }
                }
                tran.Commit();
            }
        }

        private static void OverwriteFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();

                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        // Create the SqlFileStream
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Write, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Write a single byte to the file. This will
                            // replace any data in the file.
                            fileStream.WriteByte(0x01);
                        }
                    }
                }
                tran.Commit();
            }
        }

        private static void InsertFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();

                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.ReadWrite, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Seek to the end of the file
                            fileStream.Seek(0, SeekOrigin.End);

                            // Append a single byte
                            fileStream.WriteByte(0x01);
                        }
                    }
                }
                tran.Commit();
            }

        }
    }
}
```

別のサンプルについては、「[ファイル ストリーム列にバイナリ データをフェッチおよび格納する方法](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str)」を参照してください。

## <a name="resources-in-sql-server-books-online"></a>SQL Server オンライン ブックのリソース

FILESTREAM の詳細なドキュメントは、SQL Server オンライン ブックの次のセクションにあります。

|トピック|説明|
|-----------|-----------------|
|[FILESTREAM (SQL Server)](../../../relational-databases/blob/filestream-sql-server.md)|FILESTREAM ストレージを使用するタイミングと、SQL Server データベース エンジンと NTFS ファイル システムを統合する方法について説明します。|
|[FILESTREAM データ用のクライアント アプリケーションの作成](../../../relational-databases/blob/create-client-applications-for-filestream-data.md)|FILESTREAM データを操作するための Windows API 関数について説明します。|
|[FILESTREAM と SQL Server のその他の機能](../../../relational-databases/blob/filestream-compatibility-with-other-sql-server-features.md)|FILESTREAM データを SQL Server の他の機能で使用する場合の考慮事項、ガイドライン、および制限事項について説明します。|

## <a name="next-steps"></a>次のステップ
- [SQL Server のデータ型と ADO.NET](sql-server-data-types.md)
- [SQL Server のバイナリ データと大きな値のデータ](sql-server-binary-large-value-data.md)
