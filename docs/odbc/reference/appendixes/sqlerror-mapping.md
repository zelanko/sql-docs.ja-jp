---
title: "SQLError マッピング |Microsoft ドキュメント"
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
- mapping deprecated functions [ODBC], SQLError
- SQLError function [ODBC], mapping
ms.assetid: 802ac711-7e5d-4152-9698-db0cafcf6047
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7ebbe17713149276acbe061bfb8ba41503026306
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlerror-mapping"></a>SQLError マッピング
アプリケーションを呼び出すと**SQLError**から ODBC 3*.x*ドライバーへの呼び出し  
  
```  
SQLError(henv, hdbc, hstmt, szSqlState, pfNativeError, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)   
```  
  
 をマップされます。  
  
```  
SQLGetDiagRec(HandleType, Handle, RecNumber, szSqlstate, pfNativeErrorPtr, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)  
```  
  
 *HandleType*引数に応じて、値は SQL_HANDLE_ENV、sql_handle_dbc として、または、SQL_HANDLE_STMT を設定し、*処理*引数の値に設定されて*henv*、 *hdbc*、または*hstmt* をクリックします。 *RecNumber*引数には、ドライバー マネージャーによってを決定します。
