---
title: "状態レコード |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 4a987f69-158f-4cc4-a31b-2b7dd8dcbb87
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: eabde5fad5c72cb8d3a662462759c0c342ca4ac2
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="status-records"></a>状態レコード
状態レコード内のフィールドは、特定のエラーや、SQLSTATE、ネイティブ エラー番号、診断メッセージ、列番号、および行番号を含む、ドライバー マネージャー、ドライバー、またはデータ ソースによって返される警告についてを説明します。 関数に SQL_ERROR、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_NEED_DATA、または SQL_STILL_EXECUTING が返された場合にのみ、ステータス レコードを作成することができます。 状態レコード内のフィールドの完全な一覧を参照してください、 [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)関数の説明。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [状態レコードのシーケンス](../../../odbc/reference/develop-app/sequence-of-status-records.md)  
  
-   [SQLSTATE](../../../odbc/reference/develop-app/sqlstates.md)  
  
-   [診断メッセージ](../../../odbc/reference/develop-app/diagnostic-messages.md)
