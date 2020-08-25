---
description: バッチ モード
title: バッチモード |Microsoft Docs
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 353e5ae0fe15fb21f04f6efcc97195a5e237b58e
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806400"
---
# <a name="batch-mode"></a>バッチ モード
バッチモードは、 **LockType** プロパティが **Adlockbatchoptimistic** に設定され、バッチ更新がプロバイダーによってサポートされている場合に有効になります。 特定のロックの種類の設定は、カーソルの場所によっては使用できません。 たとえば、 **カーソル位置** が **adUseClient**に設定されている場合、ペシミスティックロックの種類は使用できません。 逆に、プロバイダーは、カーソル位置がサーバー上にある場合にバッチオプティミスティックロックをサポートできません。 バッチ更新は、キーセットまたは静的カーソルのいずれかでのみ使用してください。  
  
 **UpdateBatch**メソッドを使用して、コピーバッファーに保持されている**レコードセット**の変更をサーバーに送信し、データソースを更新します。 次のセクションでは、 **レコードセット** をバッチモードで開き、コピーバッファーに変更を加えた後、 **UpdateBatch**の呼び出しを使用して変更をデータソースに送信します。  
  
 このセクションのトピックは次のとおりです。  
  
-   [更新プログラムの送信: UpdateBatch メソッド](./sending-the-updates-updatebatch-method.md)  
  
-   [更新されたレコードのフィルター処理](./filtering-for-updated-records.md)  
  
-   [失敗した更新の処理](./dealing-with-failed-updates.md)  
  
-   [競合の検出および解決](./detecting-and-resolving-conflicts.md)  
  
-   [レコードセットの切断と再接続](./disconnecting-and-reconnecting-the-recordset.md)  
  
-   [JOINed の結果の更新: Unique Table](./updating-joined-results-unique-table.md)