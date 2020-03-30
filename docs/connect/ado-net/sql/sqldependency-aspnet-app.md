---
title: ASP.NET アプリケーションでの SqlDependency
description: ASP.NET アプリケーションからクエリ通知を使用する方法を示します。
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 8e159a6db1820169cd81caa05e70765ac32f0d56
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "78896224"
---
# <a name="sqldependency-in-an-aspnet-application"></a>ASP.NET アプリケーションでの SqlDependency

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

このセクションの例は、ASP.NET <xref:Microsoft.Data.SqlClient.SqlDependency> オブジェクトを利用して <xref:System.Web.Caching.SqlCacheDependency> を間接的に使用する方法を示しています。 <xref:System.Web.Caching.SqlCacheDependency> オブジェクトは <xref:Microsoft.Data.SqlClient.SqlDependency> を使用して通知をリッスンし、キャッシュを正しく更新します。  
  
> [!NOTE]
>  このサンプル コードを実行するには、「[クエリ通知の有効化](enable-query-notifications.md)」のスクリプトを実行してクエリ通知を有効にしておく必要があります。  
  
## <a name="about-the-sample-application"></a>サンプル アプリケーションについて  
このサンプル アプリケーションでは、1 つの ASP.NET Web ページを使用して、SQL Server データベースである **AdventureWorks** に格納されている製品情報を <xref:System.Web.UI.WebControls.GridView> コントロールに表示します。 ページが読み込まれる際に、コードによって <xref:System.Web.UI.WebControls.Label> コントロールに現在の時刻が書き込まれます。 次に、<xref:System.Web.Caching.SqlCacheDependency> オブジェクトが定義され、最大 3 分間キャッシュ データが格納されるように <xref:System.Web.Caching.Cache> オブジェクトのプロパティが設定されます。 その後、データベースに接続され、データが取得されます。 ページが読み込まれ、アプリケーションが実行されると、ASP.NET によって、データがキャッシュから取得されます。これは、ページ上の時刻が変更されないことで確認できます。 監視対象のデータが変更されると、ASP.NET によりキャッシュが無効になり、`GridView` コントロールに最新データが再入力されます。これにより、`Label` コントロールに表示される時刻が更新されます。  
  
## <a name="creating-the-sample-application"></a>サンプル アプリケーションの作成  
サンプル アプリケーションを作成して実行するには、次の手順に従います。  
  
1. 新しい ASP.NET Web サイトの作成  
  
2. <xref:System.Web.UI.WebControls.Label> および <xref:System.Web.UI.WebControls.GridView> コントロールを Default.aspx ページに追加します。  
  
3. ページのクラス モジュールを開き、次のディレクティブを追加します。  
  
    ```csharp  
    using Microsoft.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4. 次のコードをページの `Page_Load` イベントに追加します。  
  
    [!code-csharp[DataWorks SqlDependency_Start#1](~/../sqlclient/doc/samples/SqlDependency_Start.cs#1)]
  
5. `GetConnectionString` および `GetSQL` という 2 つのヘルパー メソッドを追加します。 定義される接続文字列では、統合セキュリティが使用されます。 使用しているアカウントが、必要とされるデータベースへのアクセス許可を持っており、サンプル データベースの **AdventureWorks** で通知が有効になっていることを確認する必要があります。
  
    [!code-csharp[DataWorks SqlDependency_Start#2](~/../sqlclient/doc/samples/SqlDependency_Start.cs#2)]
  
### <a name="testing-the-application"></a>アプリケーションのテスト  
このアプリケーションは Web フォームに表示されるデータをキャッシュし、アクティビティがなければ 3 分ごとにそのデータを更新します。 データベースに変更があれば、キャッシュは直ちに更新されます。 Visual Studio からアプリケーションを実行すると、ブラウザーにページが読み込まれます。 表示されるキャッシュ更新時刻は、最後にキャッシュが更新された時刻を示します。 3 分間の待機後、ページを更新すると、ポストバック イベントが発生します。 ページに表示される時刻が変更されることに注意してください。 3 分経過する前にページを更新した場合、ページに表示される時刻は変わりません。  
  
次に、Transact-SQL の UPDATE コマンドを使用して、データベースのデータを更新し、ページを更新します。 表示される時刻を見ると、データベースの新しいデータを使ってキャッシュが更新されたことがわかります。 キャッシュは更新されますが、ページに表示される時刻はポストバック イベントが発生するまで変更されないことに注意してください。  
  
## <a name="next-steps"></a>次のステップ
- [SQL Server でのクエリ通知](query-notifications-sql-server.md)
