---
title: を取得する ( Excel ドライバー ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLGetInfo
- SQLGetInfo function [ODBC], Excel Driver
ms.assetid: fed4aea2-6d3d-4199-a5db-3d033eb63927
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0a96b135bbd8d44b82e645fac59ddea795666f3f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298582"
---
# <a name="sqlgetinfo-excel-driver"></a>SQLGetInfo (Excel ドライバー)
> [!NOTE]  
>  このトピックでは、Excel ドライバー固有の情報を提供します。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 **情報**の種類SQL_FILE_USAGEサポートします。 戻り値は、ドライバーがデータ ソース内のファイルを直接処理する方法を示す 16 ビットの整数です。  
  
-   SQL_FILE_NOT_SUPPORTED - ドライバーは単一層ドライバーではありません。  
  
-   SQL_FILE_TABLE - 単一層のドライバーは、データ ソース内のファイルをテーブルとして扱います。  
  
-   SQL_FILE_QUALIFIER - 単一層のドライバーは、データ ソース内のファイルを修飾子として扱います。  
  
 ODBC ドライバは、各ファイルがテーブルであるため、Microsoft Excel ドライバのSQL_FILE_TABLEを返します。  
  
## <a name="sql_dbms_ver"></a>SQL_DBMS_VER  
  
|Isam|Version|バージョン番号の形式|  
|----------|-------------|-------------------------------|  
|Microsoft Excel|3.0|03.00.0000|  
||4.0|04.00.0000|  
||5.0/7.0|05.00.0000|  
||97/2000|08.00.0000|  
  
## <a name="sql_file_usage"></a>SQL_FILE_USAGE  
 SQL_FILE_TABLE (Excel 3.0/4.0)  
  
 SQL_FILE_CATALOG (Excel 5.0/7.0)  
  
## <a name="sql_max_char_literal_len"></a>SQL_MAX_CHAR_LITERAL_LEN  
 255 (Excel 3.0/4.0/5.0/7.0)  
  
 65535 (Excel 97)  
  
## <a name="sql_max_column_name_len"></a>SQL_MAX_COLUMN_NAME_LEN  
 30 (Excel 3.0/4.0)  
  
 64 (Excel 5.0/7.0/97)  
  
## <a name="sql_max_table_name_len"></a>SQL_MAX_TABLE_NAME_LEN  
 12 (Excel 3.0/4.0)  
  
 31 (Excel 5.0/7.0/97)  
  
## <a name="sql_catalog_name_separator"></a>SQL_CATALOG_NAME_SEPARATOR  
 "\\" (Excel 3.0/4.0)  
  
 "."(Excel 5.0/7.0/97)  
  
## <a name="sql_catalog_term"></a>SQL_CATALOG_TERM  
 "ディレクトリ" (Excel 3.0/4.0)  
  
 "ブック" (Excel 5.0/7.0/97)  
  
## <a name="sql_catalog_usage"></a>SQL_CATALOG_USAGE  
 SQL_QU_DML_STATEMENTS &#124; SQL_QU_TABLE_DEFINITION  
  
## <a name="sql_timedate_functions"></a>SQL_TIMEDATE_FUNCTIONS  
 &#124;&#124;の&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;SQL_FN_TD_DAYOFWEEK&#124;SQL_FN_TD_DAYOFWEEK&#124;SQL_FN_TD_DAYOFWEEK&#124;SQL_FN_TD_DAYOFWEEKSQL_FN_TD_DAYOFWEEK&#124;&#124;&#124;&#124;&#124;&#124;を&#124; SQL_FN_TD_YEAR SQL_FN_TD_WEEK &#124; SQL_FN_TD_SECOND &#124; SQL_FN_TD_NOW &#124; SQL_FN_TD_MONTH SQL_FN_TD_MINUTE &#124; SQL_FN_TD_HOUR &#124; SQL_FN_TD_DAYOFYEAR &#124; SQL_FN_TD_DAYOFMONTH &#124; SQL_FN_TD_CURTIME &#124; SQL_FN_TD_CURDATEします
