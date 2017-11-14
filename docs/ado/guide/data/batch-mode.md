---
title: "バッチ モード |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data updates [ADO], batch mode
- batch mode [ADO]
- updating data [ADO], batch mode
ms.assetid: 0cb548e0-fcb4-4c49-98c8-be287911f826
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 92e249a7c2d5b0c01e291f4829d5c4f8c580fb2c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="batch-mode"></a>バッチ モード
バッチ モードが有効になってときに、 **LockType**プロパティに設定されている**adLockBatchOptimistic**バッチ更新は、プロバイダーでサポートされています。 特定のロックの種類の設定は、カーソル位置に応じてご利用いただけません。 たとえば、排他ロックの種類場合は使用できません、 **CursorLocation**に設定されている**adUseClient**です。 逆に、プロバイダーは、カーソルの場所は、サーバーの場合、バッチ オプティミスティック ロックをサポートできません。 バッチ更新を keyset または static カーソルのみを使用する必要があります。  
  
 **UpdateBatch**メソッドを使用して、送信**Recordset**コピー バッファーでデータ ソースを更新するためにサーバーの変更を保持します。 開くことは、次のセクションで、 **Recordset**バッチ モードでは、コピー バッファーを変更してへの呼び出しを使用してデータ ソースに変更を送信**UpdateBatch**です。  
  
 このセクションのトピックは次のとおりです。  
  
-   [更新プログラムを送信する: UpdateBatch メソッド](../../../ado/guide/data/sending-the-updates-updatebatch-method.md)  
  
-   [更新されたレコードにフィルター処理](../../../ado/guide/data/filtering-for-updated-records.md)  
  
-   [失敗した更新を処理します。](../../../ado/guide/data/dealing-with-failed-updates.md)  
  
-   [検出および競合の解決](../../../ado/guide/data/detecting-and-resolving-conflicts.md)  
  
-   [接続を切断および再接続をレコード セット](../../../ado/guide/data/disconnecting-and-reconnecting-the-recordset.md)  
  
-   [一意テーブルを更新すると、結果が参加しています。](../../../ado/guide/data/updating-joined-results-unique-table.md)

