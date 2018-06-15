---
title: 状態レコード |Microsoft ドキュメント
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
- diagnostic information [ODBC], diagnostic records
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 4a987f69-158f-4cc4-a31b-2b7dd8dcbb87
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5d36b40394f3f968f2ab841006a82b7ccb2218bd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32910887"
---
# <a name="status-records"></a>状態レコード
状態レコード内のフィールドは、特定のエラーや、SQLSTATE、ネイティブ エラー番号、診断メッセージ、列番号、および行番号を含む、ドライバー マネージャー、ドライバー、またはデータ ソースによって返される警告についてを説明します。 関数に SQL_ERROR、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_NEED_DATA、または SQL_STILL_EXECUTING が返された場合にのみ、ステータス レコードを作成することができます。 状態レコード内のフィールドの完全な一覧を参照してください、 [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)関数の説明。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [状態レコードのシーケンス](../../../odbc/reference/develop-app/sequence-of-status-records.md)  
  
-   [SQLSTATE](../../../odbc/reference/develop-app/sqlstates.md)  
  
-   [診断メッセージ](../../../odbc/reference/develop-app/diagnostic-messages.md)
