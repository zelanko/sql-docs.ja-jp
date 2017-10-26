---
title: "SQLSetPos を含む行セット内の行を削除する |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLSetPos function [ODBC], deleting rows
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
ms.assetid: 3117a47d-e179-4f76-89d0-656582f1c9bb
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ac33a8370cbd76a3dde43df68c12c9417fc78e07
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="deleting-rows-in-the-rowset-with-sqlsetpos"></a>SQLSetPos を含む行セット内の行を削除します。
削除操作**SQLSetPos**ようにデータ ソース テーブルの 1 つまたは複数の選択した行を削除します。 行を削除する**SQLSetPos**、アプリケーション呼び出し**SQLSetPos**で*操作*SQL_DELETE に設定し、 *RowNumber*に設定、削除する行の数です。 場合*RowNumber*が 0 の行セット内のすべての行が削除されます場合、。  
  
 後に**SQLSetPos**削除された行は、現在の行とその状態は SQL_ROW_DELETED を返します。 呼び出しなど、さらに位置指定操作で行を使用することはできません**SQLGetData**または**SQLSetPos**です。  
  
 行セットのすべての行を削除するときに (*RowNumber*が 0 に等しい)、アプリケーションが使用できなくドライバーの更新操作と同じ方法で、行操作配列を使用して、特定の行を削除する**SQLSetPos**. (を参照してください[SQLSetPos で行セット内の行を更新](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md))。  
  
 削除対象の各行は、行セット内に存在する行でなければなりません。 フェッチによってアプリケーション バッファーが入力し、行の状態配列が維持されている場合は、これらの各の行位置でその値しないで SQL_ROW_DELETED、SQL_ROW_ERROR、または SQL_ROW_NOROW です。

