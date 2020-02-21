---
title: 非同期操作
description: .NET Framework で使用されている非同期モデルに基づいて設計された API を使用し、非同期データベース操作を実行する方法について説明します。
ms.date: 09/30/2019
ms.assetid: e7d32c3c-bf78-4bfc-a357-c9e82e4a4b3c
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 7a070d71b653b0afc9e94c898653432e7e388d07
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75250935"
---
# <a name="asynchronous-operations"></a>非同期操作

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET をダウンロードする](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

コマンドの実行など、一部のデータベース操作は、完了するまでに時間がかかる場合があります。 このような場合、シングルスレッド アプリケーションでは、他の操作をブロックしなければならず、そのコマンドの完了を待ってから独自の操作を続行する必要があります。 これに対して、実行時間の長い操作をバックグラウンド スレッドに割り当てることができると、フォアグラウンド スレッドが途中でブロックされることがなくなります。 たとえば、Windows アプリケーションでは、実行時間の長い操作をバックグラウンド スレッドに委任すると、その操作の実行中にユーザー インターフェイス スレッドの応答性を維持することができます。  
  
.NET には、開発者がバックグラウンド スレッドを利用し、ユーザー インターフェイスや優先順位の高いスレッドを解放してその <xref:Microsoft.Data.SqlClient.SqlCommand> クラスの他の操作を完了するために使用できる、標準の非同期デザイン パターンがいくつか用意されています。 具体的には、<xref:Microsoft.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A>、<xref:Microsoft.Data.SqlClient.SqlCommand.EndExecuteReader%2A>、<xref:Microsoft.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A> メソッドを <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>、<xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteReader%2A>、<xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A> メソッドと組み合わせて非同期サポートが提供されます。  
  
> [!NOTE]
>  非同期プログラミングは .NET のコアとなる機能です。 開発者が使用できるさまざまな非同期技法の詳細については、「[同期メソッドの非同期呼び出し](https://docs.microsoft.com/dotnet/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously)」を参照してください。  
  
ADO.NET 機能で非同期技法を使用しても特別な考慮事項は追加されませんが、マルチスレッド アプリケーションを作成する利点と落とし穴に注意することが重要です。 このセクションの以降の例では、開発者がマルチスレッド機能を組み込んだアプリケーションを構築する際に考慮する必要のあるいくつかの重要な問題をとりあげます。  
  
## <a name="in-this-section"></a>このセクションの内容  
[コールバックを使用する Windows アプリケーション](windows-applications-callbacks.md)  
非同期コマンドを安全に実行して、別のスレッドからのフォームやその内容の操作を正しく処理する方法の例を示します。  
  
[待機ハンドルを使用する ASP.NET アプリケーション](aspnet-apps-use-wait-handles.md)  
ASP.NET ページから複数の同時実行コマンドを実行する方法の例を示します。Wait ハンドルを使用してすべてのコマンドの完了時に操作を管理します。  
  
[コンソール アプリケーションでのポーリング](poll-console-applications.md)  
ポーリングを使用して、コンソール アプリケーションからの非同期コマンドの実行が完了するまで待機する例を示します。 この手法は、クラス ライブラリや、ユーザー インターフェイスのないその他のアプリケーションでも有効です。  
  
## <a name="next-steps"></a>次のステップ
- [SQL Server と ADO.NET](index.md)
- [同期メソッドの非同期呼び出し](https://docs.microsoft.com/dotnet/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously)
