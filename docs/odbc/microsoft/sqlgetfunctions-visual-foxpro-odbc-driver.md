---
title: SQLGetFunctions (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLGetFunctions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8102932a-88b3-49d8-bf7a-c766f54878c0
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c17cbabc7f07fa079ef2c635ac7652a072943186
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
|SQL_API_SQLBROWSECONNECT|いいえ|  
|SQL_API_SQLCOLUMNPRIVELEGES|いいえ|  
|SQL_API_SQLDATASOURCES|はい|  
|SQL_API_SQLDESCRIBEPARAM|いいえ|  
|SQL_API_SQLDRIVERS|はい|  
|SQL_API_SQLEXTENDEDFETCH|はい|  
|SQL_API_SQLFOREIGNKEYS|いいえ|  
|SQL_API_SQLMORERESULTS|はい|  
|SQL_API_SQLNATIVESQL|いいえ|  
|SQL_API_SQLNUMPARAMS|はい|  
|SQL_API_SQLPARAMOPTIONS|はい|  
|SQL_API_SQLPRIMARYKEYS|はい|  
|SQL_API_SQLPROCEDURECOLUMNS|いいえ|  
|SQL_API_SQLPROCEDURES|いいえ|  
|SQL_API_SQLSETPOS|はい|  
|SQL_API_SQLSETSCROLLOPTIONS|はい|  
|SQL_API_SQLTABLEPRIVILEGES|いいえ|  
  
 詳細については、次を参照してください。 [SQLGetFunctions](../../odbc/reference/syntax/sqlgetfunctions-function.md)で、 *ODBC プログラマ リファレンス*です。
