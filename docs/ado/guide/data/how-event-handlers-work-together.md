---
title: イベント ハンドラーがどのように連携 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- events [ADO], about event handlers
- unpaired event handlers [ADO]
- paired event handlers [ADO]
- single event handlers [ADO]
- event handlers [ADO]
- multiple object event handlers [ADO]
ms.assetid: a86c8a02-dd69-420d-8a47-0188b339858d
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4ef9af3c4ba076048e0d04d31601b20e9d9ca321
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="how-event-handlers-work-together"></a>イベント ハンドラーがどのように連携
Visual Basic でのすべてのイベント ハンドラーでプログラミングしている場合を除き、**接続**と**Recordset**かどうか実際に処理するすべてのイベントに関係なく、イベントを実装する必要があります。 行う必要がある実装作業量は、使用するプログラミング言語によって異なります。 詳細については、次を参照してください。[言語で ADO イベントのインスタンス化](../../../ado/guide/data/ado-event-instantiation-by-language.md)です。  
  
## <a name="paired-event-handlers"></a>1 対のイベント ハンドラー  
 各はイベント ハンドラーが関連付けられている**完了**イベント ハンドラー。 アプリケーションが、フィールドの値に変更されたときになど、 **WillChangeField**イベント ハンドラーが呼び出されます。 変更が許容される場合は、アプリケーションのまま、 **adStatus**パラメーターが変更されず、操作を実行します。 操作の完了時、 **FieldChangeComplete**イベントを操作を完了したアプリケーションに通知します。 正常に完了する場合**adStatus**を含む**adStatusOK**、それ以外の**adStatus**が含まれています**adStatusErrorsOccurred**と確認する必要があります、**エラー**エラーの原因を特定するオブジェクト。  
  
 ときに**WillChangeField**が呼び出されると、判断、変更が行われていないこと。 その場合は、設定**adStatus**に**adStatusCancel です。** 操作が取り消されると、 **FieldChangeComplete**イベントを受け取る、 **adStatus**の値**adStatusErrorsOccurred**です。 **エラー**オブジェクトが含まれます**adErrOperationCancelled**できるように、 **FieldChangeComplete**ハンドラーは、操作がキャンセルされたことを認識します。 ただしの値を確認する必要があります、 **adStatus**を設定するために、それを変更する前にパラメーター **adStatus**に**adStatusCancel**パラメーターが設定されている場合は、効果がありません**adStatusCantDeny**プロシージャへのエントリにします。  
  
 場合もあります操作は、1 つ以上のイベントを発生させることができます。 たとえば、**レコード セット**のイベントのペアになっているオブジェクト**フィールド**変更と**レコード**変更します。 アプリケーションでの値が変更されたとき、**フィールド**、 **WillChangeField**イベント ハンドラーが呼び出されます。 操作を続行することと判断した場合、 **WillChangeRecord**イベント ハンドラーにも発生します。 このハンドラーは、引き続きイベントも許可している場合は、変更、および**FieldChangeComplete**と**RecordChangeComplete**イベント ハンドラーが呼び出されます。 特定の操作がイベント ハンドラーが呼び出される順序は定義されていませんので、特定の順序でハンドラーの呼び出しに依存するコードを作成しないでください。  
  
 インスタンスはの複数のイベントが発生したときは、保留中の操作インストールをキャンセル イベントのいずれかの可能性があります。 たとえば、アプリケーションが変更された時点の値、**フィールド**の両方を**WillChangeField**と**WillChangeRecord**イベント ハンドラーは通常呼び出されます。 ただし、イベント ハンドラーで、それに関連する操作が取り消されたかどうか**完了**でハンドラーが呼び出される直ちに**adStatusOperationCancelled**です。 2 番目のハンドラーは呼び出されません。 ただし、最初のイベント ハンドラーは、イベントの続行を許可している場合は、その他のイベント ハンドラーが呼び出されます。 場合は、操作をキャンセルし、両方とも**完了**イベントは、前の例のように呼び出されます。  
  
## <a name="unpaired-event-handlers"></a>対になっていないイベント ハンドラー  
 状態が渡されない限り、イベントでは使用されません**adStatusCantDeny**、任意のイベントのイベント通知をオフを返すことによって**adStatusUnwantedEvent**で、*ステータス*パラメーター。 たとえば、ときに、**完了**イベント ハンドラーは、最初に呼び出されますが、戻ることができます**adStatusUnwantedEvent**です。 のみを受信後**は**イベント。 ただし、1 つ以上の理由で一部のイベントをトリガーできます。 その場合は、イベントには、*理由*パラメーター。 戻ったら**adStatusUnwantedEvent**、その特定の理由で発生した場合にのみ、そのイベントの通知の受信を停止します。 つまり、する可能性がある通知を受信各原因はイベントを発生する可能性があります。  
  
 1 つ**は**操作で使用されるパラメーターを確認するときに、イベント ハンドラーが役に立ちます。 これらの操作パラメーターを変更したり、操作をキャンセルできます。  
  
 または、**完了**イベント通知を有効にします。 最初はイベント ハンドラーが呼び出されると、返す**adStatusUnwantedEvent**です。 のみを受信後**完了**イベント。  
  
 1 つ**完了**イベント ハンドラーは、非同期操作の管理に役立ちます。 各非同期操作に適切な**完了**イベント。  
  
 大規模な設定に長い時間がかかることが、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。 アプリケーションが適切に書き込まれる場合は、開始、`Recordset.Open(...,adAsyncExecute)`操作し、他の処理を続行します。 最終的になるときの通知、**レコード セット**によって設定されますが、 **ExecuteComplete**イベント。  
  
## <a name="single-event-handlers-and-multiple-objects"></a>1 つのイベント ハンドラーと複数のオブジェクト  
 Microsoft Visual C++® などのプログラミング言語の柔軟性を使用すると、複数のオブジェクトからのイベント ハンドラー プロセス イベントがあることができます。 たとえば、1 つがある可能性があります**切断**からいくつかのイベント ハンドラー プロセス イベント**接続**オブジェクト。 接続のいずれかが終了した場合、**切断**イベント ハンドラーが呼び出されます。 イベント ハンドラー オブジェクトのパラメーターは、対応する設定があるために、どの接続がイベントを発生させたかを判別できます**接続**オブジェクト。  
  
> [!NOTE]
>  この手法は、その言語は、イベント ハンドラーを 1 つのオブジェクトを関連付けることができますので、Visual Basic では使用できません。  
  
## <a name="see-also"></a>参照  
 [ADO イベント ハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)   
 [言語によって、ADO イベントのインスタンス化](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [イベントのパラメーター](../../../ado/guide/data/event-parameters.md)   
 [イベントの種類](../../../ado/guide/data/types-of-events.md)
