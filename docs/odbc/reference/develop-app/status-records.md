---
title: ステータスレコード |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4afef16137404fcdfd3e1d328642f1d314829538
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301373"
---
# <a name="status-records"></a>状態レコード
ステータス レコードのフィールドには、ドライバー マネージャー、ドライバー、またはデータ ソースによって返される特定のエラーまたは警告に関する情報が含まれています、 SQLSTATE、ネイティブ エラー番号、診断メッセージ、列番号、行番号など。 状態レコードは、関数がSQL_ERROR、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_NEED_DATA、またはSQL_STILL_EXECUTINGを返す場合にのみ作成できます。 ステータス レコードのフィールドの完全な一覧については[、SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)関数の説明を参照してください。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [状態レコードのシーケンス](../../../odbc/reference/develop-app/sequence-of-status-records.md)  
  
-   [SQLSTATE](../../../odbc/reference/develop-app/sqlstates.md)  
  
-   [診断メッセージ](../../../odbc/reference/develop-app/diagnostic-messages.md)
