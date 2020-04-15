---
title: SQLGetInfo (パラドックス ドライバー) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Paradox driver [ODBC], SQLGetInfo
- SQLGetInfo function [ODBC], Paradox Driver
ms.assetid: 43aab762-68f4-4128-b8f5-8878ea5f1258
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 354fa7f08797ee1fbfb057bfc2f2c192a8c5eddc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298572"
---
# <a name="sqlgetinfo-paradox-driver"></a>SQLGetInfo (Paradox ドライバー)
> [!NOTE]  
>  このトピックでは、Paradox ドライバー固有の情報を提供します。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 **情報**の種類SQL_FILE_USAGEサポートします。 戻り値は、ドライバーがデータ ソース内のファイルを直接処理する方法を示す 16 ビットの整数です。  
  
-   SQL_FILE_NOT_SUPPORTED - ドライバーは単一層ドライバーではありません。  
  
-   SQL_FILE_TABLE - 単一層のドライバーは、データ ソース内のファイルをテーブルとして扱います。  
  
-   SQL_FILE_QUALIFIER - 単一層のドライバーは、データ ソース内のファイルを修飾子として扱います。  
  
 ODBC ドライバは、各ファイルがテーブルであるため、SQL_FILE_TABLE返します。  
  
## <a name="sql_alter_table"></a>SQL_ALTER_TABLE  
 SQL_AT_ADD_COLUMN&#124;SQL_AT_DROP_COLUMN  
  
## <a name="sql_ddl_index"></a>SQL_DDL_INDEX  
 SQL_DL_CREATE_INDEX  
  
 SQL_DL_DROP_INDEX  
  
## <a name="sql_dbms_ver"></a>SQL_DBMS_VER  
  
|Isam|Version|バージョン番号の形式|  
|----------|-------------|-------------------------------|  
|パラドックス|3.x|03.00.0000|  
||4.x|04.00.0000|  
||5.x|05.00.0000|  
  
## <a name="sql_catalog_usage"></a>SQL_CATALOG_USAGE  
 &#124;SQL_QU_INDEX_DEFINITIONSQL_QU_TABLE_DEFINITION&#124;SQL_QU_DML_STATEMENTS  
  
## <a name="sql_timedate_functions"></a>SQL_TIMEDATE_FUNCTIONS  
 SQL_FN_TD_MONTH&#124;のSQL_FN_TD_YEARを&#124;SQL_FN_TD_DAYOFYEARSQL_FN_TD_MONTHSQL_FN_TD_HOURSQL_FN_TD_HOURSQL_FN_TD_HOURSQL_FN_TD_HOURSQL_FN_TD_HOURSQL_FN_TD_DAYOFWEEKSQL_FN_TD_DAYOFWEEKSQL_FN_TD_DAYOFWEEKSQL_FN_TD_DAYOFWEEKSQL_FN_TD_DAYOFWEEKSQL_FN_TD_DAYOFWEEK。 &#124; SQL_FN_TD_WEEK SQL_FN_TD_SECOND &#124; SQL_FN_TD_MINUTE &#124; &#124; &#124; &#124; SQL_FN_TD_DAYOFMONTH
