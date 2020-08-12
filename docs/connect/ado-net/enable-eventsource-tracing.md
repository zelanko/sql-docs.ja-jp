---
title: SqlClient でイベント トレースを有効化する
description: イベント リスナーを実装して SqlClient でイベントのトレースを有効化する方法と、イベント データにアクセスする方法について説明します。
ms.date: 06/15/2020
dev_langs:
- csharp
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: johnnypham
ms.author: v-jopha
ms.reviewer: ''
ms.openlocfilehash: 17e947c108d14accb880dbd6673231e82b0b133c
ms.sourcegitcommit: 6b3569977b034554883a94d73d1c4df6e2f74fe2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2020
ms.locfileid: "85110165"
---
# <a name="enabling-event-tracing-in-sqlclient"></a>SqlClient でイベント トレースを有効化する

[!INCLUDE [appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE [Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

[Windows イベント トレーシング (ETW)](https://docs.microsoft.com/windows/win32/etw/event-tracing-portal) は、効率的なカーネル レベルのトレース機能で、デバッグとテストの目的でドライバー定義イベントをログに記録することができます。 SqlClient では、さまざまな情報レベルでの ETW イベントのキャプチャがサポートされています。 イベント トレースのキャプチャを開始するには、クライアント アプリケーションで SqlClient の EventSource 実装からのイベントをリッスンする必要があります。

```
Microsoft.Data.SqlClient.EventSource
```

現在の実装では、次のイベント キーワードがサポートされています。

| キーワード名 | 値 | [説明] |
| ------------ | ----- | ----------- |
| ExecutionTrace | 1 | コマンドの実行前と実行後の Start/Stop イベントのキャプチャをオンにします。 |
| Trace | 2 | 基本的なアプリケーション フロー トレース イベントのキャプチャをオンにします。 |
| Scope | 4 | enter イベントと exit イベントのキャプチャをオンにします |
| NotificationTrace | 8 | `SqlNotification` トレース イベントのキャプチャをオンにします |
| NotificationScope | 16 | `SqlNotification` スコープの enter イベントと exit イベントのキャプチャをオンにします |
| PoolerTrace | 32 | 接続プール フロー トレース イベントのキャプチャをオンにします。 |
| PoolerScope | 64 | 接続プール スコープ トレース イベントのキャプチャをオンにします。 |
| AdvancedTrace | 128 | 高度なフロー トレース イベントのキャプチャをオンにします。 |
| AdvancedTraceBin  | 256 | 追加情報を含む高度なフロー トレース イベントのキャプチャをオンにします。 |
| CorrelationTrace | 512 | 相関関係フロー トレース イベントのキャプチャをオンにします。 |
| StateDump | 1024 | `SqlConnection` の完全な状態ダンプのキャプチャをオンにします |
| SNITrace | 2048 | マネージド ネットワーク実装からのフロー トレース イベントのキャプチャをオンにします (.NET Core でのみ適用可能) |
| SNIScope | 4096 | マネージド ネットワーク実装からのスコープ イベントのキャプチャをオンにします (.NET Core でのみ適用可能) |
|||

## <a name="example"></a>例
次の例では、**AdventureWorks** サンプル データベースでデータ操作のイベント トレースを有効にし、コンソール ウィンドウにそのイベントを表示します。

[!code-csharp [SqlClientEventSource#1](~/../sqlclient/doc/samples/SqlClientEventSource.cs#1)]

## <a name="external-resources"></a>外部リソース  
詳細については、次のリソースを参照してください。  
  
|リソース|説明|  
|--------------|-----------------|  
|[EventSource クラス](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventsource)|ETW イベントを作成する機能を提供します。| 
|[EventListener クラス](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventlistener)|イベント ソースからのイベントを有効または無効にするメソッドを提供します。| 
