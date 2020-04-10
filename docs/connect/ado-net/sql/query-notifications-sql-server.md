---
title: SQL Server でのクエリ通知
description: データが変更されたときに .NET アプリケーションが SQL Server に通知を要求する方法について説明します。
ms.date: 08/15/2019
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: d3905604b45eec2f1e9c7c1c93bd53b1863695f3
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925465"
---
# <a name="query-notifications-in-sql-server"></a>SQL Server でのクエリ通知

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

クエリ通知は Service Broker インフラストラクチャに基づいて構築されており、データが変更されたときにクエリ通知を使用してアプリケーションに通知できます。 Web アプリケーションのように、データベースからの情報のキャッシュを用意し、データベースのデータが変更されたときに通知する必要があるアプリケーションでは、この機能が特に有用です。  
  
ADO.NET を使用してクエリ通知を実装する方法には、次の 3 つがあります。  
  
- 低レベルの実装は、サーバー側の機能を公開する `SqlNotificationRequest` クラスによって提供されます。これにより、通知要求を使用してコマンドを実行できるようになります。  
  
- 高レベルの実装は、ソース アプリケーションと SQL Server の間の通知機能の高レベルの抽象化を提供するクラスである `SqlDependency` クラスによって提供されます。これにより、依存関係を使用してサーバーの変更を検出できるようになります。 マネージド クライアント アプリケーションが Microsoft SqlClient Data Provider for SQL Server を使用して SQL Server の通知機能を活用するには、ほとんどの場合、これが最も簡単かつ効果的な方法です。  
  
- さらに、ASP.NET 2.0 以降を使用して構築された Web アプリケーションは、`SqlCacheDependency` ヘルパー クラスを使用できます。  
  
クエリ通知は、基になるデータの変更に応じて表示またはキャッシュを更新する必要のあるアプリケーションに使用されます。 Microsoft SQL Server では、最初に取得したものと異なる結果セットが同じコマンドで得られた場合には、.NET アプリケーションから SQL Server にコマンドを送信して通知を要求することができます。 サーバーで生成された通知は、後で処理するためにキュー経由で送信されます。  
  
通知は、SELECT および EXECUTE ステートメントに対して設定できます。 EXECUTE ステートメントを使用している場合、SQL Server はその EXECUTE ステートメント自体ではなく、実行されるコマンドについて通知を登録します。 コマンドは、SELECT ステートメントの要件と制限を満たしている必要があります。 通知を登録するコマンドに複数のステートメントが含まれている場合、Database Engine によりバッチ内のステートメントごとに通知が作成されます。  
  
データ変更時に、信頼できる即時の通知が必要なアプリケーションを開発している場合は、SQL Server オンライン ブックの「**通知の計画**」の「**効率的なクエリ通知方法の計画**」および「[クエリ通知に代わる方法](https://go.microsoft.com/fwlink/?LinkId=211984)」を参照してください。 クエリ通知と SQL Server Service Broker の詳細については、SQL Server オンライン ブックのトピックへの次のリンクを参照してください。  
  
**SQL Server のドキュメント**  
  
- [クエリ通知の使用](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))  
  
- [通知のためのクエリの作成](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
- [開発 (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))  
  
- [Service Broker 開発者向けの情報](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
- [開発者ガイド (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
## <a name="in-this-section"></a>このセクションの内容  
[クエリ通知の有効化](enable-query-notifications.md)  
クエリ通知を使用する方法、およびそれを有効にし、使用するための要件について説明します。  
  
[ASP.NET アプリケーションでの SqlDependency](sqldependency-aspnet-app.md)  
ASP.NET アプリケーションからクエリ通知を使用する方法を示します。  
  
[SqlDependency を使用した変更の検出](detect-changes-sqldependency.md)  
クエリの結果が、最初に受け取ったものと異なるタイミングを検出する方法を示します。  
  
[SqlCommand の実行と SqlNotificationRequest](sqlcommand-execution-sqlnotificationrequest.md)  
クエリ通知と連携するように <xref:Microsoft.Data.SqlClient.SqlCommand> オブジェクトを構成する方法を示します。  
  
## <a name="reference"></a>リファレンス  
<xref:Microsoft.Data.Sql.SqlNotificationRequest>  
<xref:Microsoft.Data.Sql.SqlNotificationRequest> クラスとそのすべてのメンバーについて説明します。  
  
<xref:Microsoft.Data.SqlClient.SqlDependency>  
<xref:Microsoft.Data.SqlClient.SqlDependency> クラスとそのすべてのメンバーについて説明します。  
  
<xref:System.Web.Caching.SqlCacheDependency>  
<xref:System.Web.Caching.SqlCacheDependency> クラスとそのすべてのメンバーについて説明します。  
  
## <a name="next-steps"></a>次のステップ
- [SQL Server と ADO.NET](index.md)
