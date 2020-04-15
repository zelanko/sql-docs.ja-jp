---
title: データの更新の概要 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], about updating data
- data updates [ODBC]
- updating data [ODBC]
- data updates [ODBC], about data updates
ms.assetid: 062036a4-cda6-4aaa-9765-f1ec3e0b31b1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9972ab61f041385ae4ca616df093ae63ad7a47d9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300388"
---
# <a name="updating-data-overview"></a>データの概要の更新
アプリケーションは、SQL ステートメントを実行するか **、SQLSetPos**または**SQLBulkOperations**を呼び出すことによってデータを更新できます。 **UPDATE** **、DELETE、** および**INSERT**ステートメントは、データ ソースに直接作用し、通常はドライバーによってサポートされます。 検索された更新および削除ステートメントには、変更する行の指定が含まれています。 位置指定更新および削除ステートメントと**SQLSetPos**は、カーソルを介してデータ ソースに対して動作し、あまり広くサポートされていません。  
  
 このセクションで説明するメソッドを使用して結果セットに加えられた変更をカーソルが検出できるかどうかは、カーソルの種類と実装方法によって異なります。 前方方向のカーソルは行を再訪しないため、変更は検出されません。 スクロール可能なカーソルが変更を検出できるかどうかについては、「[スクロール可能なカーソル](../../../odbc/reference/develop-app/scrollable-cursors.md)」を参照してください。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [UPDATE、DELETE、INSERT ステートメント](../../../odbc/reference/develop-app/update-delete-and-insert-statements.md)  
  
-   [位置指定の UPDATE および DELETE ステートメント](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)  
  
-   [位置指定の UPDATE および DELETE ステートメントのシミュレート](../../../odbc/reference/develop-app/simulating-positioned-update-and-delete-statements.md)  
  
-   [影響を受ける行数の決定](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md)  
  
-   [SQLSetPos によるデータの更新](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md)  
  
-   [SQLBulkOperations によるデータの更新](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md)  
  
-   [長い形式のデータ、SQLSetPos および SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)
