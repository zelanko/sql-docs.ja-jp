---
title: SQLError のマッピング |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4a278609ee53fe7898d32c1986da2650202b8a98
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63199478"
---
# <a name="sqlerror-mapping"></a>SQLError のマッピング
アプリケーションを呼び出すと**SQLError**を通じて、ODBC 3 *.x*ドライバーへの呼び出し  
  
```  
SQLError(henv, hdbc, hstmt, szSqlState, pfNativeError, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)   
```  
  
 をマップされます。  
  
```  
SQLGetDiagRec(HandleType, Handle, RecNumber, szSqlstate, pfNativeErrorPtr, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)  
```  
  
 *HandleType*引数を必要に応じて、値は sql_handle_env として、sql_handle_dbc として、または sql_handle_stmt として、設定、および*処理*引数の値に設定*henv*、 *hdbc*、または*hstmt*必要に応じて、します。 *RecNumber*引数は、ドライバー マネージャーによって決定されます。
