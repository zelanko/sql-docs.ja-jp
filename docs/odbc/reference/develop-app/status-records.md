---
title: 状態レコード |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 4a987f69-158f-4cc4-a31b-2b7dd8dcbb87
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f6ed360c39b87efe851bcbbb5c60762288ea1719
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68114279"
---
# <a name="status-records"></a>状態レコード
ステータスレコードのフィールドには、SQLSTATE、ネイティブエラー番号、診断メッセージ、列番号、行番号など、ドライバーマネージャー、ドライバー、またはデータソースによって返された特定のエラーまたは警告に関する情報が含まれます。 状態レコードを作成できるのは、関数が SQL_ERROR、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_NEED_DATA、または SQL_STILL_EXECUTING を返した場合のみです。 状態レコード内のフィールドの完全な一覧については、 [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)関数の説明を参照してください。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [状態レコードのシーケンス](../../../odbc/reference/develop-app/sequence-of-status-records.md)  
  
-   [SQLSTATE](../../../odbc/reference/develop-app/sqlstates.md)  
  
-   [診断メッセージ](../../../odbc/reference/develop-app/diagnostic-messages.md)
