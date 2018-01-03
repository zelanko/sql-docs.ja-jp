---
title: "SQLError マッピング |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLError
- SQLError function [ODBC], mapping
ms.assetid: 802ac711-7e5d-4152-9698-db0cafcf6047
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 518814868a7fafe91a166564771af51fd8a49505
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
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
