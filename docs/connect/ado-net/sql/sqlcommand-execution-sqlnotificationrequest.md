---
title: SqlCommand の実行と SqlNotificationRequest
description: クエリ通知と連携するように SqlCommand オブジェクトを構成する方法を示します。
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: b4ec71c2bd693599106692a45f9e9aa10a63babd
ms.sourcegitcommit: 610e49c3e1fa97056611a85e31e06ab30fd866b1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/07/2020
ms.locfileid: "78896237"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a>SqlCommand の実行と SqlNotificationRequest

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

<xref:Microsoft.Data.SqlClient.SqlCommand> は、データがサーバーからフェッチされた後に変更された場合、また、クエリを再度実行すると結果セットが異なるような場合に、通知を生成するように構成することができます。 これは、サーバー上でカスタム通知キューを使用する場合や、ライブ オブジェクトを保持しない場合に便利です。

## <a name="creating-the-notification-request"></a>通知要求の作成

<xref:Microsoft.Data.Sql.SqlNotificationRequest> オブジェクトを使用して通知要求を作成し、これを `SqlCommand` オブジェクトにバインドできます。 要求を作成したら、`SqlNotificationRequest` オブジェクトは不要になります。 キューに対して任意の通知を照会し、適切に応答することができます。 通知は、アプリケーションがシャットダウンされ、その後再起動された場合でも発生する可能性があります。

コマンドに通知を関連付けて実行した場合、元の結果セットに何らかの変更が生じると、通知要求で構成した SQL Server キューにメッセージが送信されます。

SQL Server のキューをポーリングしメッセージを解釈する方法は、アプリケーションごとに固有なものになります。 アプリケーションは、メッセージの内容に基づいてキューのポーリングと応答を行います。

> [!NOTE]
> <xref:Microsoft.Data.SqlClient.SqlDependency> と共に SQL Server 通知要求を使用する場合は、既定のサービス名を使用するのではなく、独自のキュー名を作成してください。

<xref:Microsoft.Data.Sql.SqlNotificationRequest> に対応する新しいクライアント側セキュリティ要素はありません。 これはそもそもサーバー機能であり、ユーザーが通知を要求するために保持する必要がある特権はサーバーによって作成されています。

### <a name="example"></a>例

次のコード フラグメントは、<xref:Microsoft.Data.Sql.SqlNotificationRequest> を作成し、<xref:Microsoft.Data.SqlClient.SqlCommand> に関連付ける方法を示しています。

```csharp
// Assume connection is an open SqlConnection.
// Create a new SqlCommand object.
SqlCommand command=new SqlCommand(
 "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection);

// Create a SqlNotificationRequest object.
SqlNotificationRequest notificationRequest=new SqlNotificationRequest();
notificationRequest.id="NotificationID";
notificationRequest.Service="mySSBQueue";

// Associate the notification request with the command.
command.Notification=notificationRequest;
// Execute the command.
command.ExecuteReader();
// Process the DataReader.
// You can use Transact-SQL syntax to periodically poll the
// SQL Server queue to see if you have a new message.
```

## <a name="next-steps"></a>次のステップ
- [SQL Server でのクエリ通知](query-notifications-sql-server.md)
