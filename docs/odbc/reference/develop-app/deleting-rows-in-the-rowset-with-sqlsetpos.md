---
title: SQLSetPos を使用して行セットの行を削除する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetPos function [ODBC], deleting rows
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
ms.assetid: 3117a47d-e179-4f76-89d0-656582f1c9bb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 940bcc3e2ee6a042394797d6038028cce64862f1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305953"
---
# <a name="deleting-rows-in-the-rowset-with-sqlsetpos"></a>SQLSetPos による行セットの行の削除
**SQLSetPos**の削除操作により、データ ソースは、テーブルの 1 つまたは複数の選択された行を削除します。 **SQLSetPos**を使用して行を削除するには、アプリケーションは**SQLSetPos**を呼び出し *、操作*をSQL_DELETEに設定し、*行番号を*削除する行の番号に設定します。 *行番号が*0 の場合、行セット内のすべての行が削除されます。  
  
 **SQLSetPos**が戻った後、削除された行は現在の行になり、その状態はSQL_ROW_DELETED。 **SQLGetData**または**SQLSetPos**の呼び出しなど、それ以降の位置指定操作では、この行を使用できません。  
  
 行セットのすべての行を削除する場合 *(RowNumber*は 0)、アプリケーションは **、SQLSetPos**の更新操作と同じ方法で、行操作配列を使用して、ドライバーが特定の行を削除することを防ぐことができます。 [(SQLSetPos を使用した行セットの行の更新を](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md)参照してください。  
  
 削除対象の各行は、行セット内に存在する行でなければなりません。 アプリケーション・バッファーがフェッチによって満たされ、行状況配列が維持されている場合、これらの行位置のそれぞれの値を、SQL_ROW_DELETED、SQL_ROW_ERROR、またはSQL_ROW_NOROWにすることはできません。
