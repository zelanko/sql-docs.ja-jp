---
title: SQLExecDirect |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLExecDirect function
ms.assetid: e7c2a5b5-83f4-4c72-9aca-7b9fb4748b11
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 36a5d580b6edb04f51d2fcf77dcc8ff0c8ba042f
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82706146"
---
# <a name="sqlexecdirect"></a>SQLExecDirect
  ステートメント属性 SQL_SOPT_SS_PARAM_FOCUS が0でない場合、SQLExecDirect は SQL_ERROR を返し、SQLSTATE = HY024 の診断レコードと、"無効な属性値、SQL_SOPT_SS_PARAM_FOCUS (実行時にはゼロでなければなりません)" というメッセージを生成します。 SQL_SOPT_SS_PARAM_FOCUS の詳細については、「 [SQLSetStmtAttr](sqlsetstmtattr.md)」を参照してください。  
  
 テーブル値パラメーターの詳細については、「[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=80709)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  
