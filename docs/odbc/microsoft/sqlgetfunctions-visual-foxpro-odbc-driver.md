---
title: "SQLGetFunctions (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLGetFunctions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8102932a-88b3-49d8-bf7a-c766f54878c0
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9e4f5b152bf1234c59783f52c64c5bbb06cb2903
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqlgetfunctions-visual-foxpro-odbc-driver"></a>SQLGetFunctions (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 サポート: 完全  
  
 レベル 1 の ODBC API への準拠:  
  
 サポートされているすべての関数の場合は TRUE を返します。  
  
 Visual FoxPro ODBC ドライバーには、すべての ODBC API のコアと第 1 レベルの関数がサポートされています。 次の表では、ドライバーが第 2 レベルの特定の機能をサポートしているかどうかを示します。  
  
|*関数*|Supported|  
|----------------|---------------|  
|SQL_API_SQLBROWSECONNECT|不可|  
|SQL_API_SQLCOLUMNPRIVELEGES|不可|  
|SQL_API_SQLDATASOURCES|可|  
|SQL_API_SQLDESCRIBEPARAM|不可|  
|SQL_API_SQLDRIVERS|可|  
|SQL_API_SQLEXTENDEDFETCH|可|  
|SQL_API_SQLFOREIGNKEYS|不可|  
|SQL_API_SQLMORERESULTS|可|  
|SQL_API_SQLNATIVESQL|不可|  
|SQL_API_SQLNUMPARAMS|可|  
|SQL_API_SQLPARAMOPTIONS|可|  
|SQL_API_SQLPRIMARYKEYS|可|  
|SQL_API_SQLPROCEDURECOLUMNS|不可|  
|SQL_API_SQLPROCEDURES|不可|  
|SQL_API_SQLSETPOS|可|  
|SQL_API_SQLSETSCROLLOPTIONS|可|  
|SQL_API_SQLTABLEPRIVILEGES|不可|  
  
 詳細については、次を参照してください。 [SQLGetFunctions](../../odbc/reference/syntax/sqlgetfunctions-function.md)で、 *ODBC プログラマ リファレンス*です。
