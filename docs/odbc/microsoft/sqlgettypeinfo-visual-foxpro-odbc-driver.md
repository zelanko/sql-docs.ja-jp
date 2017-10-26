---
title: "SQLGetTypeInfo (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント"
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
- SQLGetTypeInfo function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5f25e20b-a4ef-42da-aeb6-00e0510fb1cc
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c0240734459de6fd86d86aef2b192f13842acae7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgettypeinfo-visual-foxpro-odbc-driver"></a>SQLGetTypeInfo (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 サポート: 完全  
  
 レベル 1 の ODBC API への準拠:  
  
 データ ソースによってサポートされるデータ型に関する情報を返します。 ドライバーは、SQL 結果セット内の情報を返します。 次の表には、ODBC データ型と、対応する Visual FoxPro データ型が一覧表示します。  
  
|ODBC 型|Visual FoxPro 型|  
|---------------|------------------------|  
|SQL_BIGINT|サポートされていません。 64 ビット Visual FoxPro 型はありません。|  
|SQL_BIT|論理|  
|SQL_CHAR|文字|  
|SQL_DATE|日付|  
|SQL_DECIMAL|数値|  
|SQL_DOUBLE|Double|  
|SQL_FLOAT|Double|  
|SQL_INTEGER|Integer|  
|SQL_LONGVARBINARY|メモ (バイナリ)|  
|SQL_LONGVARCHAR|メモ|  
|SQL_NUMERIC|数値 *、通貨、Float|  
|SQL_REAL|Double|  
|SQL_SMALLINT|Integer|  
|SQL_TIME|サポートされていません。 Visual FoxPro がない*時間*型です。|  
|SQL_TIMESTAMP|DateTime|  
|SQL_TINYINT|Integer|  
|SQL_VARBINARY|メモ (バイナリ) *、一般的な|  
|SQL_VARCHAR|文字|  
  
 * 既定の種類  
  
 Visual FoxPro データ型の詳細については、次を参照してください。 [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md)です。 この関数の詳細については、次を参照してください。 [SQLGetTypeInfo](../../odbc/reference/syntax/sqlgettypeinfo-function.md)で、 *ODBC プログラマ リファレンス*です。

