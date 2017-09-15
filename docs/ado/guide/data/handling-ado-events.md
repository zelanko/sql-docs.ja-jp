---
title: "ADO イベントの処理 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [ADO]
- ADO, events
- event handlers [ADO]
ms.assetid: e9003457-0762-48b3-942f-0820266b158f
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a451023d3e3501ac60cd2724349337f30c46b689
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="handling-ado-events"></a>ADO イベントの処理
ADO イベント モデルは、同期および非同期 ADO する特定の操作を発行をサポートしている*イベント*、または、操作を開始する前に、または完了後に、通知します。 イベントは、実際には、アプリケーションで定義するイベント ハンドラー ルーチンの呼び出しです。  
  
 グループの操作を開始する前に発生するイベントのハンドラー関数またはプロシージャを指定する場合は、確認または操作に渡されたパラメーターを変更できます。 まだ実行されていないが、ため、操作を取り消すか、完了することを許可します。  
  
 操作が完了した後に発生するイベントは、ADO を非同期的に使用する場合に特に重要です。 たとえば、非同期に開始するアプリケーション[Recordset.Open](../../../ado/reference/ado-api/open-method-ado-recordset.md)操作は、操作の終了時の実行完了イベントによって通知されます。  
  
 ADO イベント モデルを使用して、アプリケーションに追加のオーバーヘッドがかかるが、監視などの非同期操作を処理する場合の他のメソッドよりもはるかに柔軟性を提供、[状態](../../../ado/reference/ado-api/state-property-ado.md)ループが発生するオブジェクトのプロパティです。  
  
> [!NOTE]
>  イベントを処理するには、ADO をメッセージ ポンプか、シングル スレッド アパートメント (STA) モデルで使用する必要があります。 ADO イベントは、非表示のウィンドウを作成することで内部的に処理されます。 ADO では、イベントを発生させる必要がある場合に、このウィンドウにメッセージを送信します。 呼び出したスレッドに送信されるイベントを確認してください。 これは、 **iconnectionpoint::advise**接続ポイント。 このアーキテクチャには、通知を受け取る必要のあるスレッドがウィンドウのメッセージをポンプいないときに問題が発生します。 潜在的な問題には、スレッドとタイムアウトの可能性のあるパフォーマンスの低下システム全体を非表示のウィンドウは、メッセージを処理できないためグローバル ウィンドウ ブロードキャストに配信されない ADO イベントが含まれます。 STA スレッドには、通常、この問題は見られません STA スレッドで実行しているメッセージ ポンプがあります。 MTA スレッド、ただし、通常ことはありませんメッセージ ポンプ問題は、通常現れます MTA スレッドのようにします。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ADO イベント ハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)  
  
-   [イベントの種類](../../../ado/guide/data/types-of-events.md)  
  
-   [イベントのパラメーター](../../../ado/guide/data/event-parameters.md)  
  
-   [イベント ハンドラーがどのように連携](../../../ado/guide/data/how-event-handlers-work-together.md)  
  
-   [言語によって、ADO イベントのインスタンス化](../../../ado/guide/data/ado-event-instantiation-by-language.md)  
  
## <a name="see-also"></a>参照  
 [ADO イベント ハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)   
 [言語によって、ADO イベントのインスタンス化](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [ADO イベント](../../../ado/reference/ado-api/ado-events.md)   
 [イベントのパラメーター](../../../ado/guide/data/event-parameters.md)   
 [イベントの種類](../../../ado/guide/data/types-of-events.md)
