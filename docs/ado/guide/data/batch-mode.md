---
title: バッチ モード |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data updates [ADO], batch mode
- batch mode [ADO]
- updating data [ADO], batch mode
ms.assetid: 0cb548e0-fcb4-4c49-98c8-be287911f826
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c25cd688b5d74e4514e1af645f7917059ce4d445
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47602400"
---
# <a name="batch-mode"></a>バッチ モード
バッチ モードが有効なときに、 **LockType**プロパティに設定されて**adLockBatchOptimistic**バッチ更新プロバイダーによってサポートされています。 カーソル位置に応じて特定のロックの種類の設定が利用できません。 たとえば、ペシミスティック ロックの種類場合は使用できません、 **CursorLocation**に設定されている**adUseClient**します。 逆に、プロバイダーは、サーバー カーソルの場所がある場合、バッチ オプティミスティック ロックをサポートできません。 バッチ更新を keyset または static カーソルのみを使用する必要があります。  
  
 **UpdateBatch**メソッドを使用して、送信**Recordset**変更は、データ ソースを更新するサーバーに、コピー バッファーに保持します。 次のセクションで開くが、**レコード セット**バッチ モードで、コピー バッファーに変更を加えるし、呼び出しに使用してデータ ソースに変更を送信**UpdateBatch**します。  
  
 このセクションのトピックは次のとおりです。  
  
-   [更新プログラムの送信: UpdateBatch メソッド](../../../ado/guide/data/sending-the-updates-updatebatch-method.md)  
  
-   [更新されたレコードのフィルター処理](../../../ado/guide/data/filtering-for-updated-records.md)  
  
-   [失敗した更新の処理](../../../ado/guide/data/dealing-with-failed-updates.md)  
  
-   [競合の検出および解決](../../../ado/guide/data/detecting-and-resolving-conflicts.md)  
  
-   [レコードセットの切断と再接続](../../../ado/guide/data/disconnecting-and-reconnecting-the-recordset.md)  
  
-   [JOINed の結果の更新: Unique Table](../../../ado/guide/data/updating-joined-results-unique-table.md)
