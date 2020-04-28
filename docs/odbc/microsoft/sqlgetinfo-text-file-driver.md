---
title: SQLGetInfo (テキストファイルドライバー) |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298503"
---
# <a name="sqlgetinfo-text-file-driver"></a>SQLGetInfo (テキスト ファイル ドライバー)
> [!NOTE]  
>  このトピックでは、テキストファイルドライバー固有の情報について説明します。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
 **SQLGetInfo**では、SQL_FILE_USAGE 情報の種類がサポートされています。 返される値は、ドライバーがデータソース内のファイルを直接扱う方法を示す16ビット整数です。  
  
-   SQL_FILE_NOT_SUPPORTED-ドライバーが単一層のドライバーではありません。  
  
-   SQL_FILE_TABLE-1 層ドライバーは、データソース内のファイルをテーブルとして扱います。  
  
-   SQL_FILE_QUALIFIER-1 層ドライバーは、データソース内のファイルを修飾子として扱います。  
  
 ODBC ドライバーは、各ファイルがテーブルであるため、Textdriver の SQL_FILE_TABLE を返します。  
  
## <a name="sql_dbms_ver"></a>SQL_DBMS_VER  
  
|ドライバー|バージョン|バージョン番号の形式|  
|----------|-------------|-------------------------------|  
|テキスト|1.0|01.00.0000|  
  
## <a name="sql_catalog_usage"></a>SQL_CATALOG_USAGE  
 SQL_QU_DML_STATEMENTS &#124; SQL_QU_TABLE_DEFINITION  
  
## <a name="sql_timedate_functions"></a>SQL_TIMEDATE_FUNCTIONS  
 SQL_FN_TD_CURDATE &#124; SQL_FN_TD_CURTIME &#124; SQL_FN_TD_DAYOFMONTH &#124; SQL_FN_TD_DAYOFWEEK &#124; SQL_FN_TD_DAYOFYEAR &#124; SQL_FN_TD_HOUR &#124; SQL_FN_TD_MINUTE &#124; SQL_FN_TD_MONTH &#124; SQL_FN_TD_NOW &#124; SQL_FN_TD_SECOND &#124; SQL_FN_TD_WEEK &#124; SQL_FN_TD_YEAR
