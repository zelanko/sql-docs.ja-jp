---
title: "SQLGetInfo (テキスト ファイル ドライバー) |Microsoft ドキュメント"
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
helpviewer_keywords:
- SQLGetInfo function [ODBC], Text File Driver
- text file driver [ODBC], SQLGetInfo
ms.assetid: 6b7a630e-47f8-4ee1-b2a7-476bc1d0b0d4
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9a5fe524a3c95c4f01cea5902612a5e8a8c1b537
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqlgetinfo-text-file-driver"></a>SQLGetInfo (テキスト ファイル ドライバー)
> [!NOTE]  
>  このトピックでは、テキスト ファイル ドライバー固有の情報を提供します。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 **SQLGetInfo** SQL_FILE_USAGE 情報の種類をサポートしています。 返される値は、ドライバーが直接データ ソース内のファイルを扱う方法を示す 16 ビット整数を示します。  
  
-   SQL_FILE_NOT_SUPPORTED —、ドライバーは、1 階層ドライバーではありません。  
  
-   SQL_FILE_TABLE — 1 階層ドライバー データ ソース内のファイルはテーブルとして扱います。  
  
-   SQL_FILE_QUALIFIER — 1 階層ドライバーでは修飾子としてデータ ソース内のファイルを扱います。  
  
 ODBC ドライバーは、各ファイルはテーブルなので、Textdriver の SQL_FILE_TABLE を返します。  
  
## <a name="sqldbmsver"></a>SQL_DBMS_VER  
  
|ISAM|バージョン|バージョン番号の形式|  
|----------|-------------|-------------------------------|  
|テキスト|1.0|01.00.0000|  
  
## <a name="sqlcatalogusage"></a>SQL_CATALOG_USAGE  
 SQL_QU_DML_STATEMENTS &#124;です。SQL_QU_TABLE_DEFINITION  
  
## <a name="sqltimedatefunctions"></a>SQL_TIMEDATE_FUNCTIONS  
 SQL_FN_TD_CURDATE &#124; です。 SQL_FN_TD_CURTIME &#124; です。 SQL_FN_TD_DAYOFMONTH &#124;です。 SQL_FN_TD_DAYOFWEEK &#124; です。SQL_FN_TD_DAYOFYEAR &#124; です。 SQL_FN_TD_HOUR &#124; です。SQL_FN_TD_MINUTE &#124;です。SQL_FN_TD_MONTH &#124;です。 SQL_FN_TD_NOW &#124; です。SQL_FN_TD_SECOND&#124;です。SQL_FN_TD_WEEK&#124;です。SQL_FN_TD_YEAR
