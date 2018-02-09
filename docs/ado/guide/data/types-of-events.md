---
title: "イベントの種類 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- EventComplete event [ADO]
- events [ADO], types
- Will events [ADO]
- complete events [ADO]
- WillEvent event [ADO]
ms.assetid: f3327ea0-635a-43d4-bd78-c1674f62f1a2
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 52d78d1a6ae1fc2ccb34ee6b8d810f1ca5ba1c22
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="types-of-events"></a>イベントの種類
2 つの基本的な種類のイベントがあります。 「は、イベント」と呼ばれる操作の開始前に、通常、名前に「は」を含める-たとえば、 **WillChangeRecordset**または**WillConnect**です。 通常、イベントが完了した後に呼び出されるイベントが、名前に「完了」を含める-たとえば、 **RecordChangeComplete**または**ConnectComplete**です。 例外の存在-など**InfoMessage** — がこれらは、関連する操作が完了した後にエラーが発生します。  
  
## <a name="will-events"></a>イベントには  
 操作の開始からの確認または操作のパラメーターを変更しし、操作をキャンセルまたは完了することを許可する機会を提供する前に、イベント ハンドラーが呼び出されます。 これらのイベント ハンドラー ルーチンは通常、フォームの名前を持つ **は*イベント * * *。  
  
## <a name="complete-events"></a>完了イベント  
 操作が完了した後に呼び出されるイベント ハンドラーは、操作の完了をアプリケーションに通知できます。 このようなイベント ハンドラーはイベント ハンドラーが保留中の操作をキャンセルしたときにも通知されます。 これらのイベント ハンドラー ルーチンは通常、フォームの名前を持つ ***イベント * 完了**です。  
  
 完了イベントは、通常のペアで使用されます。  
  
## <a name="other-events"></a>その他のイベント  
 他のイベント ハンドラー: 名前を持つの形式ではないイベントは、**は * イベント*** または ***イベント * 完了**: 操作の完了後にのみと呼ばれます。 これらのイベントは**切断**、 **EndOfRecordset**、および**InfoMessage**です。  
  
## <a name="see-also"></a>参照  
 [ADO イベント ハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)   
 [言語によって、ADO イベントのインスタンス化](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [イベントのパラメーター](../../../ado/guide/data/event-parameters.md)   
 [複数のイベント ハンドラーの連携方法](../../../ado/guide/data/how-event-handlers-work-together.md)
