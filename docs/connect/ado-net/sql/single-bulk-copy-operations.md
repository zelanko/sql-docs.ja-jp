---
title: 単一の一括コピー操作
description: SqlBulkCopy クラスを使用して、SQL Server のインスタンスへのデータの単一の一括コピーを実行する方法、および Transact-SQL ステートメントと SqlCommand クラスを使用して一括コピー操作を実行する方法について説明します。
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 1029d9a0121b23963ccfc12582bd9d9cc7fd6cd6
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "78896597"
---
# <a name="single-bulk-copy-operations"></a>単一の一括コピー操作

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

SQL Server の一括コピー操作を実行する最も簡単な方法は、データベースに対して単一操作を実行することです。 既定では、一括コピー操作は分離された操作として実行されます。このコピー操作は非トランザクション方式で処理され、ロールバックできません。  
  
> [!NOTE]
>  エラーの発生時に一括コピー処理の全部または一部をロールバックする必要がある場合は、<xref:Microsoft.Data.SqlClient.SqlBulkCopy> により管理されるトランザクションを使用するか、既存のトランザクション内で一括コピー操作を実行できます。 **SqlBulkCopy** は、**System.Transactions** トランザクションに (明示的または暗黙的に) 接続が参加している場合は <xref:System.Transactions> も使用します。  
>   
>  詳細については、「[トランザクションと一括コピー操作](transaction-bulk-copy-operations.md)」を参照してください。  
  
一括コピー操作を実行する一般的な手順は次のとおりです。  
  
1. コピー元のサーバーに接続し、コピーするデータを取得します。 <xref:System.Data.IDataReader> オブジェクトまたは <xref:System.Data.DataTable> オブジェクトからデータを取得できる場合は、他のソースから取得する場合もあります。  
  
2. コピー先のサーバーに接続します (**SqlBulkCopy** を使用して接続を確立しない場合)。  
  
3. <xref:Microsoft.Data.SqlClient.SqlBulkCopy> オブジェクトを作成し、必要なプロパティを設定します。  
  
4. バルク挿入操作の対象となるテーブルが示されるように **DestinationTableName** プロパティを設定します。  
  
5. **WriteToServer** メソッドのいずれかを呼び出します。  
  
6. オプションとして、プロパティを更新したり、必要に応じて **WriteToServer** をもう一度呼び出したりします。  
  
7. <xref:Microsoft.Data.SqlClient.SqlBulkCopy.Close%2A> を呼び出すか、一括コピー操作を `Using` ステートメント内にラップします。  
  
> [!CAUTION]
>  コピー元とコピー先の列のデータ型を一致させることをお勧めします。 データ型が一致していない場合、**SqlBulkCopy** は、<xref:Microsoft.Data.SqlClient.SqlParameter.Value%2A> によって採用されている規則を使用して、コピー元の値をコピー先のデータ型にそれぞれ変換しようとします。 この変換はパフォーマンスに影響を及ぼすだけでなく、予期しないエラーが発生する場合もあります。 たとえば、`Double` データ型はたいていの場合 `Decimal` データ型に変換できますが、変換できない場合もあります。  
  
## <a name="example"></a>例  
次のコンソール アプリケーションは、<xref:Microsoft.Data.SqlClient.SqlBulkCopy> クラスを使用してデータを読み込む方法を示しています。 この例では、<xref:Microsoft.Data.SqlClient.SqlDataReader> を使用し、SQL Server の **AdventureWorks** データベースに格納された **Production.Product** テーブルのデータを、同じデータベース内の同等のテーブルにコピーします。  
  
> [!IMPORTANT]
>  このサンプルは、「[一括コピーのセットアップ例](bulk-copy-example-setup.md)」で説明しているように作業テーブルを作成して取得してからでないと動作しません。 このコードでは、**SqlBulkCopy** だけを使用した構文について説明します。 コピー元およびコピー先のテーブルが同一の SQL Server インスタンス内に存在する場合、Transact-SQL `INSERT … SELECT` ステートメントを使用すれば簡単かつ高速にデータをコピーすることができます。  
  
[!code-csharp[DataWorks SqlBulkCopy_WriteToServer#1](~/../sqlclient/doc/samples/SqlBulkCopy_WriteToServer.cs#1)]
  
## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a>transact-SQL とコマンド クラスを使用した一括コピー操作の実行  
次の例では、BULK INSERT ステートメントを実行する <xref:Microsoft.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> メソッドの使用方法を説明します。  
  
> [!NOTE]
>  データ ソースのファイル パスはサーバーに対する相対パスです。 一括コピー操作を正常に実行するには、サーバー プロセスがこのパスにアクセスできる必要があります。  
  
```csharp  
using (SqlConnection connection = New SqlConnection(connectionString))  
{  
string queryString =  "BULK INSERT Northwind.dbo.[Order Details] " +  
    "FROM 'f:\mydata\data.tbl' " +  
    "WITH ( FORMATFILE='f:\mydata\data.fmt' )";  
connection.Open();  
SqlCommand command = new SqlCommand(queryString, connection);  
  
command.ExecuteNonQuery();  
}  
```  
  
## <a name="next-steps"></a>次のステップ
- [SQL Server での一括コピー操作](bulk-copy-operations-sql-server.md)
