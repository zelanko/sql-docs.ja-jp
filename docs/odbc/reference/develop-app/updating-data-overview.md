---
title: データの概要の更新 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], about updating data
- data updates [ODBC]
- updating data [ODBC]
- data updates [ODBC], about data updates
ms.assetid: 062036a4-cda6-4aaa-9765-f1ec3e0b31b1
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 64f61563836b7deddc65b2dc61307ed686f030ef
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915897"
---
# <a name="updating-data-overview"></a>データの更新の概要
SQL ステートメントを実行することによって、または呼び出すことによって、アプリケーションでデータを更新できる**SQLSetPos**または**SQLBulkOperations**です。 **更新**、**削除**、および**挿入**ステートメントは、データ ソース上で直接実行し、は、通常、ドライバーでサポートします。 更新プログラムを検索し、delete ステートメントには変更する行の仕様が含まれています。 更新プログラムの配置、および delete ステートメントと**SQLSetPos**カーソルによる、データ ソースで動作し、小さい広くサポートされています。  
  
 カーソルがこのセクションで説明する方法を使用して結果セットに加えられた変更を検出できるかどうかは、カーソルとそれを実装する方法の種類によって異なります。 順方向専用カーソルでは、行を再確認されませんし、そのため、変更は検出されません。 スクロール可能なカーソルが変更を検出するかどうかについては、次を参照してください。[スクロール可能なカーソル](../../../odbc/reference/develop-app/scrollable-cursors.md)です。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [UPDATE、DELETE、INSERT ステートメント](../../../odbc/reference/develop-app/update-delete-and-insert-statements.md)  
  
-   [位置指定の UPDATE および DELETE ステートメント](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)  
  
-   [位置指定の UPDATE および DELETE ステートメントのシミュレート](../../../odbc/reference/develop-app/simulating-positioned-update-and-delete-statements.md)  
  
-   [影響を受ける行数の決定](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md)  
  
-   [SQLSetPos によるデータの更新](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md)  
  
-   [SQLBulkOperations によるデータの更新](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md)  
  
-   [長い形式のデータ、SQLSetPos および SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)
