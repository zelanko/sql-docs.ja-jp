---
title: バッチ モード |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data updates [ADO], batch mode
- batch mode [ADO]
- updating data [ADO], batch mode
ms.assetid: 0cb548e0-fcb4-4c49-98c8-be287911f826
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e825fad70386144e6e59dc7631c8d31b99fee5b6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="batch-mode"></a>バッチ モード
バッチ モードが有効になってときに、 **LockType**プロパティに設定されている**adLockBatchOptimistic**バッチ更新は、プロバイダーでサポートされています。 特定のロックの種類の設定は、カーソル位置に応じてご利用いただけません。 たとえば、排他ロックの種類場合は使用できません、 **CursorLocation**に設定されている**adUseClient**です。 逆に、プロバイダーは、カーソルの場所は、サーバーの場合、バッチ オプティミスティック ロックをサポートできません。 バッチ更新を keyset または static カーソルのみを使用する必要があります。  
  
 **UpdateBatch**メソッドを使用して、送信**Recordset**コピー バッファーでデータ ソースを更新するためにサーバーの変更を保持します。 開くことは、次のセクションで、 **Recordset**バッチ モードでは、コピー バッファーを変更してへの呼び出しを使用してデータ ソースに変更を送信**UpdateBatch**です。  
  
 このセクションのトピックは次のとおりです。  
  
-   [更新プログラムの送信: UpdateBatch メソッド](../../../ado/guide/data/sending-the-updates-updatebatch-method.md)  
  
-   [更新されたレコードのフィルター処理](../../../ado/guide/data/filtering-for-updated-records.md)  
  
-   [失敗した更新の処理](../../../ado/guide/data/dealing-with-failed-updates.md)  
  
-   [競合の検出および解決](../../../ado/guide/data/detecting-and-resolving-conflicts.md)  
  
-   [レコードセットの切断と再接続](../../../ado/guide/data/disconnecting-and-reconnecting-the-recordset.md)  
  
-   [JOINed の結果の更新: Unique Table](../../../ado/guide/data/updating-joined-results-unique-table.md)
