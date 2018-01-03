---
title: "SQLGetInfo (Paradox ドライバー) |Microsoft ドキュメント"
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
- Paradox driver [ODBC], SQLGetInfo
- SQLGetInfo function [ODBC], Paradox Driver
ms.assetid: 43aab762-68f4-4128-b8f5-8878ea5f1258
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bdfe77f36784217a7f708ee7d716083bac52055b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlgetinfo-paradox-driver"></a>SQLGetInfo (Paradox ドライバー)
> [!NOTE]  
>  このトピックでは、Paradox ドライバー固有の情報を提供します。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 **SQLGetInfo** SQL_FILE_USAGE 情報の種類をサポートしています。 返される値は、ドライバーが直接データ ソース内のファイルを扱う方法を示す 16 ビット整数を示します。  
  
-   SQL_FILE_NOT_SUPPORTED —、ドライバーは、1 階層ドライバーではありません。  
  
-   SQL_FILE_TABLE — 1 階層ドライバー データ ソース内のファイルはテーブルとして扱います。  
  
-   SQL_FILE_QUALIFIER — 1 階層ドライバーでは修飾子としてデータ ソース内のファイルを扱います。  
  
 ODBC ドライバーは、各ファイルはテーブルなので、SQL_FILE_TABLE を返します。  
  
## <a name="sqlaltertable"></a>SQL_ALTER_TABLE  
 SQL_AT_ADD_COLUMN &#124;です。SQL_AT_DROP_COLUMN  
  
## <a name="sqlddlindex"></a>SQL_DDL_INDEX  
 SQL_DL_CREATE_INDEX  
  
 SQL_DL_DROP_INDEX  
  
## <a name="sqldbmsver"></a>SQL_DBMS_VER  
  
|ISAM|[バージョンのオプション]|バージョン番号の形式|  
|----------|-------------|-------------------------------|  
|Paradox|3.x|03.00.0000|  
||4.x|04.00.0000|  
||5.x|05.00.0000|  
  
## <a name="sqlcatalogusage"></a>SQL_CATALOG_USAGE  
 SQL_QU_DML_STATEMENTS &#124;です。SQL_QU_TABLE_DEFINITION &#124;です。SQL_QU_INDEX_DEFINITION  
  
## <a name="sqltimedatefunctions"></a>SQL_TIMEDATE_FUNCTIONS  
 SQL_FN_TD_DAYOFMONTH &#124;です。 SQL_FN_TD_DAYOFWEEK &#124;です。SQL_FN_TD_DAYOFYEAR &#124;です。 SQL_FN_TD_HOUR &#124;です。SQL_FN_TD_MINUTE &#124;です。SQL_FN_TD_MONTH &#124;です。 SQL_FN_TD_SECOND &#124;です。SQL_FN_TD_WEEK &#124;です。SQL_FN_TD_YEAR
