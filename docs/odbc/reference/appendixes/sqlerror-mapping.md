---
title: SQL エラー マッピング |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLError
- SQLError function [ODBC], mapping
ms.assetid: 802ac711-7e5d-4152-9698-db0cafcf6047
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1aa3b66b29af755099cb273f3a19ca4e8230cd0b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302079"
---
# <a name="sqlerror-mapping"></a>SQLError のマッピング
アプリケーションが ODBC *3.x*ドライバを使用して**SQLError**を呼び出すと、次の  
  
```  
SQLError(henv, hdbc, hstmt, szSqlState, pfNativeError, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)   
```  
  
 にマップされています  
  
```  
SQLGetDiagRec(HandleType, Handle, RecNumber, szSqlstate, pfNativeErrorPtr, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)  
```  
  
 引数*HandleType*に必要に応じて値SQL_HANDLE_ENV、SQL_HANDLE_DBC、またはSQL_HANDLE_STMTを設定し、*引数 Handle*に*henv* *、hdbc*、または*hstmt*の値を設定します。 *RecNumber*引数は、ドライバー マネージャーによって決定されます。
