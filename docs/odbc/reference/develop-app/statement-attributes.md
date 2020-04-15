---
title: ステートメント属性 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], statement attributes
- statement attributes [ODBC]
ms.assetid: 4c59cd8e-a713-4095-9065-20d5bdeafe43
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ec24cc43e8c57e47ddda9f20fac1807f42453e84
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299645"
---
# <a name="statement-attributes"></a>ステートメント属性
ステートメント属性は、ステートメントの特性です。 たとえば、ブックマークを使用するかどうか、およびステートメントの結果セットで使用するカーソルの種類は、ステートメント属性です。  
  
 ステートメント属性は **、SQLSetStmtAttr**と、その現在の設定を**使用して**取得して設定されます。 アプリケーションがステートメント属性を設定する必要はありません。すべてのステートメント属性にはデフォルトがあり、その一部はドライバー固有です。  
  
 ステートメント属性を設定できるタイミングは、属性自体によって異なります。 SQL_ATTR_CONCURRENCY、SQL_ATTR_CURSOR_TYPE、SQL_ATTR_SIMULATE_CURSOR、およびSQL_ATTR_USE_BOOKMARKSステートメントの属性は、ステートメントの実行前に設定する必要があります。 SQL_ATTR_ASYNC_ENABLEおよびSQL_ATTR_NOSCANステートメント属性は、いつでも設定できますが、ステートメントが再び使用されるまで適用されません。 SQL_ATTR_MAX_LENGTH、SQL_ATTR_MAX_ROWS、およびSQL_ATTR_QUERY_TIMEOUTステートメントの属性はいつでも設定できますが、ステートメントを再び使用する前に適用されるかどうかは、ドライバー固有です。 残りのステートメント属性はいつでも設定できます。  
  
> [!NOTE]  
>  **SQLSetConnectAttr**を呼び出して、接続レベルでステートメント属性を設定する機能は、ODBC 3 で廃止されました。*x .* ODBC 3.*x*アプリケーションは、接続レベルでステートメント属性を設定しないでください。 ODBC 3.*x*ドライバは、ODBC 2 で動作する必要がある場合にのみ、この機能をサポートする必要があります。*x*アプリケーション。 詳細については、「付録 G: 下位互換性のためのドライバガイドライン」の[SQLSetConnect オプション マッピング](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md)を参照してください。  
>   
>  例外は、接続属性とステートメント属性の両方であるSQL_ATTR_METADATA_ID属性とSQL_ATTR_ASYNC_ENABLE属性であり、接続レベルまたはステートメント・レベルで設定できます。  
>   
>  ODBC 3 で導入されたステートメント属性はありません。*x* (SQL_ATTR_METADATA_IDを除く) は、接続レベルで設定できます。  
  
 詳細については、[関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)の説明を参照してください。
