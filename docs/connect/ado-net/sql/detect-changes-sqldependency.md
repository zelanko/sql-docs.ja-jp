---
title: SqlDependency を使用した変更の検出
description: クエリの結果が、最初に受け取ったものと異なるタイミングを検出する方法を示します。
ms.date: 09/30/2019
dev_langs:
- csharp
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 90b11516e9fa8ed993792bfec2a77757249b696d
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "78896984"
---
# <a name="detecting-changes-with-sqldependency"></a>SqlDependency を使用した変更の検出

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

<xref:Microsoft.Data.SqlClient.SqlDependency> オブジェクトを <xref:Microsoft.Data.SqlClient.SqlCommand> に関連付けて、クエリの結果が最初に取得したものと異なる場合を検出できます。 `OnChange` イベントにデリゲートを割り当てることもできます。これは、関連付けられたコマンドの結果が変更されたときに実行されます。 コマンドを実行する前に、<xref:Microsoft.Data.SqlClient.SqlDependency> をコマンドに関連付ける必要があります。 <xref:Microsoft.Data.SqlClient.SqlDependency> の `HasChanges` プロパティを使用して、データを最初に取得してからクエリの結果が変更されたかどうかを判断することもできます。

## <a name="security-considerations"></a>セキュリティに関する考慮事項

依存関係インフラストラクチャは <xref:Microsoft.Data.SqlClient.SqlConnection> に依存します。これは、<xref:Microsoft.Data.SqlClient.SqlDependency.Start%2A> が呼び出されたときに開かれ、特定のコマンドの基になるデータが変更されたことの通知を受信します。 クライアントが `SqlDependency.Start` への呼び出しを開始する機能は、<xref:Microsoft.Data.SqlClient.SqlClientPermission> およびコード アクセス セキュリティ属性を使用して制御します。 詳しくは、「[クエリ通知の有効化](enable-query-notifications.md)」をご覧ください。

### <a name="example"></a>例

次の手順では、依存関係を宣言し、コマンドを実行し、結果セットが変更されたときに通知を受け取る方法について説明します。

1. サーバーへの `SqlDependency` 接続を開始します。

2. サーバーに接続して Transact-SQL ステートメントを定義するための <xref:Microsoft.Data.SqlClient.SqlConnection> および <xref:Microsoft.Data.SqlClient.SqlCommand> オブジェクトを作成します。

3. 新しい `SqlDependency` オブジェクトを作成するか、既存のオブジェクトを使用して、それを `SqlCommand` オブジェクトにバインドします。 内部では、これによって <xref:Microsoft.Data.Sql.SqlNotificationRequest> オブジェクトが作成され、必要に応じてコマンド オブジェクトにバインドされます。 この通知要求には、この `SqlDependency` オブジェクトを一意に識別する内部識別子が含まれます。 また、これにより、クライアント リスナーがまだアクティブになっていない場合に起動されます。

4. イベント ハンドラーを `SqlDependency` オブジェクトの `OnChange` イベントにサブスクライブします。

5. `SqlCommand` オブジェクトの任意の `Execute` メソッドを使用して、コマンドを実行します。 コマンドは通知オブジェクトにバインドされているため、サーバーで通知を生成する必要があることが認識され、キュー情報が依存関係キューを指します。

6. サーバーへの `SqlDependency` 接続を停止します。

その後ユーザーが基になるデータを変更した場合、Microsoft SQL Server でその変更に対して保留中の通知があることが検出され、`SqlDependency.Start` を呼び出して作成された、基になる `SqlConnection` を介して処理され、クライアントに転送される通知が送信されます。 クライアント リスナーで、無効化メッセージが受信されます。 次にクライアント リスナーで、関連付けられている `SqlDependency` オブジェクトが検索され、`OnChange` イベントが起動されます。

次のコード フラグメントでは、サンプル アプリケーションの作成に使用する設計パターンを示しています。

```csharp
void Initialization()
{
    // Create a dependency connection.
    SqlDependency.Start(connectionString, queueName);
}

void SomeMethod()
{
    // Assume connection is an open SqlConnection.

    // Create a new SqlCommand object.
    using (SqlCommand command=new SqlCommand(
        "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers",
        connection))
    {

        // Create a dependency and associate it with the SqlCommand.
        SqlDependency dependency=new SqlDependency(command);
        // Maintain the reference in a class member.

        // Subscribe to the SqlDependency event.
        dependency.OnChange+=new
           OnChangeEventHandler(OnDependencyChange);

        // Execute the command.
        using (SqlDataReader reader = command.ExecuteReader())
        {
            // Process the DataReader.
        }
    }
}

// Handler method
void OnDependencyChange(object sender,
   SqlNotificationEventArgs e )
{
  // Handle the event (for example, invalidate this cache entry).
}

void Termination()
{
    // Release the dependency.
    SqlDependency.Stop(connectionString, queueName);
}
```

## <a name="next-steps"></a>次のステップ
- [SQL Server でのクエリ通知](query-notifications-sql-server.md)
