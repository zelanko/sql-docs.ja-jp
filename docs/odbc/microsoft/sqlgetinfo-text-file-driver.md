---
title: SQLGetInfo (テキスト ファイル ドライバ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetInfo function [ODBC], Text File Driver
- text file driver [ODBC], SQLGetInfo
ms.assetid: 6b7a630e-47f8-4ee1-b2a7-476bc1d0b0d4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 09ca2e42e20a6f314de3b68fe5d5b143f41269c3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298503"
---
# <a name="sqlgetinfo-text-file-driver"></a>SQLGetInfo (テキスト ファイル ドライバー)
> [!NOTE]  
>  このトピックでは、テキスト ファイル ドライバー固有の情報を提供します。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 **情報**の種類SQL_FILE_USAGEサポートします。 戻り値は、ドライバーがデータ ソース内のファイルを直接処理する方法を示す 16 ビットの整数です。  
  
-   SQL_FILE_NOT_SUPPORTED - ドライバーは単一層ドライバーではありません。  
  
-   SQL_FILE_TABLE - 単一層のドライバーは、データ ソース内のファイルをテーブルとして扱います。  
  
-   SQL_FILE_QUALIFIER - 単一層のドライバーは、データ ソース内のファイルを修飾子として扱います。  
  
 ODBC ドライバは、各ファイルがテーブルであるため、テキストドライバのSQL_FILE_TABLEを返します。  
  
## <a name="sql_dbms_ver"></a>SQL_DBMS_VER  
  
|Isam|Version|バージョン番号の形式|  
|----------|-------------|-------------------------------|  
|Text|1.0|01.00.0000|  
  
## <a name="sql_catalog_usage"></a>SQL_CATALOG_USAGE  
 SQL_QU_DML_STATEMENTS &#124; SQL_QU_TABLE_DEFINITION  
  
## <a name="sql_timedate_functions"></a>SQL_TIMEDATE_FUNCTIONS  
 &#124;&#124;の&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;&#124;SQL_FN_TD_DAYOFWEEK&#124;SQL_FN_TD_DAYOFWEEK&#124;SQL_FN_TD_DAYOFWEEK&#124;SQL_FN_TD_DAYOFWEEKSQL_FN_TD_DAYOFWEEK&#124;&#124;&#124;&#124;&#124;&#124;を&#124; SQL_FN_TD_YEAR SQL_FN_TD_WEEK &#124; SQL_FN_TD_SECOND &#124; SQL_FN_TD_NOW &#124; SQL_FN_TD_MONTH SQL_FN_TD_MINUTE &#124; SQL_FN_TD_HOUR &#124; SQL_FN_TD_DAYOFYEAR &#124; SQL_FN_TD_DAYOFMONTH &#124; SQL_FN_TD_CURTIME &#124; SQL_FN_TD_CURDATEします
