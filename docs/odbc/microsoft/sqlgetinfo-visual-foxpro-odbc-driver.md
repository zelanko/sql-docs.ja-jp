---
title: SQLGetInfo (ビジュアル フォックスプロ ODBC ドライバー) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetInfo function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: fbc39e3d-67d9-4331-bf5f-76dbd74c4c45
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2d4b976083b46bf632c4890c7fce3b0f13a9a761
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295192"
---
# <a name="sqlgetinfo-visual-foxpro-odbc-driver"></a>SQLGetInfo (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、ビジュアル フォックス プロ ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 サポート: フル  
  
 ODBC API 準拠: レベル 1  
  
 接続ハンドル*hdbc*に関連付けられている Visual FoxPro ODBC ドライバーとデータ ソースに関する一般的な情報を返します。 次の一覧は、*各 fInfoType*引数の Visual FoxPro ODBC ドライバーによって返される値と、戻り値に関するコメントを示します。  
  
 詳細については *、ODBC プログラマ リファレンス*の[SQLGetInfo](../../odbc/reference/syntax/sqlgetinfo-function.md)を参照してください。  
  
## <a name="a"></a>A  
 SQL_ACCESSIBLE_PROCEDURESは 'N' を返します。  
  
 SQL_ACCESSIBLE_TABLESは 'Y' を返します。  
  
 SQL_ACTIVE_CONNECTIONSは 0 を返します。  
  
 SQL_ACTIVE_STATEMENTSは 0 を返します。  
  
 SQL_ALTER_TABLEは、SQL_AT_ADD_COLUMNまたはSQL_AT_DROP_COLUMNを返します。  
  
## <a name="b"></a>B  
 SQL_BOOKMARK_PERSISTENCEはSQL_BP_SCROLLを返します。  
  
## <a name="c"></a>C  
 SQL_COLUMN_ALIASは 'Y' を返します。  
  
 SQL_CONCAT_NULL_BEHAVIORはSQL_CB_NULLを返します。  
  
 SQL_CONVERT_BIGINTは 0 を返します。 ビジュアル フォックスプロ ODBC ドライバーは*BigInt*をサポートしていません。  
  
 SQL_CONVERT_BINARYは 0 を返します。  
  
 SQL_CONVERT_BITは 0 を返します。  
  
 SQL_CONVERT_CHARは 0 を返します。  
  
 SQL_CONVERT_DATEは 0 を返します。  
  
 SQL_CONVERT_DECIMALは 0 を返します。  
  
 SQL_CONVERT_DOUBLEは 0 を返します。  
  
 SQL_CONVERT_FLOATは 0 を返します。  
  
 SQL_CONVERT_INTEGERは 0 を返します。  
  
 SQL_CONVERT_LONGVARBINARYは 0 を返します。  
  
 SQL_CONVERT_LONGVARCHARは 0 を返します。  
  
 SQL_CONVERT_NUMERICは 0 を返します。  
  
 SQL_CONVERT_REALは 0 を返します。  
  
 SQL_CONVERT_SMALLINTは 0 を返します。  
  
 SQL_CONVERT_TIMEは 0 を返します。  
  
 SQL_CONVERT_TIMESTAMPは 0 を返します。  
  
 SQL_CONVERT_TINYINTは 0 を返します。  
  
 SQL_CONVERT_VARBINARYは 0 を返します。  
  
 SQL_CONVERT_VARCHARは 0 を返します。  
  
 SQL_CONVERT_FUNCTIONSは 0 を返します。  
  
 SQL_CORRELATION_NAMEはSQL_CN_ANYを返します。  
  
 SQL_CURSOR_COMMIT_BEHAVIORはSQL_CB_PRESERVEを返します。  
  
 SQL_CURSOR_ROLLBACK_BEHAVIORはSQL_CB_PRESERVEを返します。  
  
## <a name="d"></a>D  
 SQL_DATA_SOURCE_NAMEは[、DSN](../../odbc/microsoft/sqlconnect-visual-foxpro-odbc-driver.md)として渡された値を SQLConnect または[SQL ドライバ接続に](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)返します。DSN が指定されていない場合は空の文字列を返します。  
  
 SQL_DATA_SOURCE_READ_ONLYは 'N' を返します。  
  
 SQL_DATABASE_NAMEは、データ ソースがデータベースの場合、現在のデータベースへの完全な UNC パスを返[します](../../odbc/microsoft/visual-foxpro-terminology.md)。 データ ソースが[テーブル](../../odbc/microsoft/visual-foxpro-terminology.md)のディレクトリ に接続する場合、関数はディレクトリへのパスを返します。  
  
 SQL_DBMS_NAMEは「ビジュアルフォックスプロ」を返します。  
  
 SQL_DBMS_VERは"03.00.0000"を返します。  
  
 SQL_DEFAULT_TXN_ISOLATIONはSQL_TXN_READ_COMMITTEDを返します。 ダーティ読み取りはできませんが、反復不可能な読み取りとファントムは可能です。  
  
 SQL_DRIVER_HDBCは、ドライバー マネージャーによって実装されます。  
  
 SQL_DRIVER_HENVは、ドライバー マネージャーによって実装されます。  
  
 SQL_DRIVER_HLIBは、ドライバー マネージャーによって実装されます。  
  
 SQL_DRIVER_HSTMTは、ドライバー マネージャーによって実装されます。  
  
 SQL_DRIVER_NAMEは "vfpodbc.dll" を返します。  
  
 SQL_DRIVER_ODBC_VERは "02.50" (SQL_SPEC_MAJOR、SQL_SPEC_MINOR) を返します。  
  
 SQL_DRIVER_VERは"01.00.0000"を返します。  
  
## <a name="e"></a>E  
 SQL_EXPRESSIONS_IN_ORDERBYは 'N' を返します。  
  
## <a name="f"></a>F  
 SQL_FETCH_DIRECTION返します:  
  
-   SQL_FD_FETCH_NEXT  
  
-   SQL_FD_FETCH_FIRST  
  
-   SQL_FD_FETCH_LAST  
  
-   SQL_FD_FETCH_PRIOR  
  
-   SQL_FD_FETCH_ABSOLUTE  
  
-   SQL_FD_FETCH_RELATIVE  
  
-   SQL_FD_FETCH_BOOKMARK。  
  
 SQL_FILE_USAGEは、データベース (.dbc ファイル) と空きテーブル (.dbf ファイル) のデータ ソースの両方のSQL_FILE_QUALIFIERを返します。  
  
## <a name="g-h"></a>G-H  
 SQL_GETDATA_EXENSIONS返します。  
  
-   SQL_GD_ANY_COLUMN  
  
-   SQL_GD_ANY_BLOCK  
  
-   SQL_GD_ANY_BOUND  
  
-   SQL_GD_ANY_ORDER  
  
 SQL_GROUP_BYはSQL_GB_NO_RELATIONを返します。  
  
## <a name="i-j"></a>I-J  
 SQL_IDENTIFIER_CASEはSQL_IC_MIXEDを返します。  
  
 SQL_IDENTIFIER_QUOTE_CHARは '.  
  
## <a name="k"></a>K  
 SQL_KEYWORDSは "" を返します。  
  
## <a name="l"></a>L  
 SQL_LIKE_ESCAPE_CLAUSEは 'N' を返します。  
  
 SQL_LOCK_TYPESはSQL_LCK_NO_CHANGEを返します。  
  
## <a name="m"></a>M  
 SQL_MAX_BINARY_LITERAL_LENは 0 を返します。  
  
 SQL_MAX_CHAR_LITERAL_LENは 254 を返します。  
  
 SQL_MAX_COLUMN_NAME_LENは 128 を返します。  
  
 SQL_MAX_COLUMNS_IN_GROUP_BYは 16 を返します。  
  
 SQL_MAX_COLUMNS_IN_ORDER_BYは 16 を返します。  
  
 SQL_MAX_COLUMNS_IN_INDEXは 0 を返します。  
  
 SQL_MAX_COLUMNS_IN_SELECTは 254 を返します。  
  
 SQL_MAX_COLUMNS_IN_TABLEは 254 を返します。  
  
 SQL_MAX_CURSOR_NAME_LENは 254 を返します。  
  
 SQL_MAX_INDEX_SIZEは 0 を返します。  
  
 SQL_MAX_OWNER_NAME_LENは 0 を返します。  
  
 SQL_MAX_PROCEDURE_NAME_LENは 0 を返します。 ビジュアル フォックスプロ ODBC ドライバーは、Visual FoxPro ストアド プロシージャに直接アクセスを許可しません。  
  
 SQL_MAX_QUALIFIER_NAME_LENは、オペレーティング システムのパスの最大長を返します。  
  
 SQL_MAX_ROW_SIZEは 254^2 を返します。  
  
 SQL_MAX_ROW_SIZE_INCLUDES_LONGは 'N' を返します。  
  
 SQL_MAX_STATEMENT_LENは 8192 を返します。  
  
 SQL_MAX_TABLE_NAME_LENは 128 を返します。  
  
 SQL_MAX_TABLES_IN_SELECTは 16 を返します。  
  
 SQL_MAX_USER_NAME_LENは 0 を返します。  
  
 SQL_MULT_RESULT_SETSは'Y' を返します。  
  
 SQL_MULTIPLE_ACTIVE_TXNは'Y' を返します。 複数の接続で複数のトランザクションを同時に開くことができます。  
  
## <a name="n"></a>N  
 SQL_NEED_LONG_DATA_LENは 'N' を返します。  
  
 SQL_NON_NULLABLE_COLUMNSはSQL_NNC_NON_NULLを返します。  
  
 SQL_NULL_COLLATIONはSQL_NC_LOWを返します。  
  
 SQL_NUMERIC_FUNCTIONSは、SQL_FN_NUM_POWERを除くすべての関数を返しますが、これは Visual FoxPro ODBC ドライバーではサポートされていません。 次の関数がサポートされています。  
  
-   SQL_FN_NUM_ABS  
  
-   SQL_FN_NUM_ACOS  
  
-   SQL_FN_NUM_ASIN  
  
-   SQL_FN_NUM_ATAN  
  
-   SQL_FN_NUM_ATAN2  
  
-   SQL_FN_NUM_CELING  
  
-   SQL_FN_NUM_COS  
  
-   SQL_FN_NUM_COT  
  
-   SQL_FN_NUM_DEGREES  
  
-   SQL_FN_NUM_EXP  
  
-   SQL_FN_NUM_FLOOR  
  
-   SQL_FN_NUM_LOG  
  
-   SQL_FN_NUM_LOG10  
  
-   SQL_FN_NUM_MOD  
  
-   SQL_FN_NUM_PI  
  
-   SQL_FN_NUM_RADIANS  
  
-   SQL_FN_NUM_RAND  
  
-   SQL_FN_NUM_ROUND  
  
-   SQL_FN_NUM_SIGN  
  
-   SQL_FN_NUM_SIN  
  
-   SQL_FN_NUM_SQRT  
  
-   SQL_FN_NUM_TAN  
  
## <a name="o"></a>O  
 SQL_ODBC_API_CONFORMANCEはSQL_OAC_LEVEL1を返します。  
  
 SQL_ODBC_SAG_CLI_CONFORMANCEはSQL_OSCC_COMPLIANTを返します。  
  
 SQL_ODBC_SQL_CONFORMANCEはSQL_OSC_MINIMUMを返します。 最小 SQL 構文がサポートされています。  
  
 SQL_ODBC_SQL_OPT_IEFは"N"を返します。  
  
 SQL_ODBC_VERは、ドライバー マネージャーによって実装されます。  
  
 SQL_ORDER_BY_COLUMNS_IN_SELECTは "N" を返します。  
  
 SQL_OUTER_JOINSは"N"を返します。  
  
 SQL_OWNER_TERMは "" を返します。 ビジュアル フォックスプロ ODBC ドライバーは、そのオブジェクトの所有者をサポートしていません。  
  
 SQL_OWNER_USAGEは 0 を返します。 ビジュアル フォックスプロ ODBC ドライバーは、そのオブジェクトの所有者をサポートしていません。  
  
## <a name="p"></a>P  
 SQL_POS_OPERATIONSはSQL_POS_POSITIONを返します。  
  
 SQL_POSITIONED_STATEMENTSは 0 を返します。  
  
 SQL_PROCEDURE_TERMは "" を返します。  
  
 SQL_PROCEDURESは 'N' を返します。  
  
## <a name="q"></a>Q  
 SQL_QUALIFIER_LOCATIONはSQL_QL_STARTを返します。  
  
 SQL_QUALIFIER_NAME_SEPARATORは '!'\\または ' を返します。 データベースとテーブルの間の区切りは、[データベース](../../odbc/microsoft/visual-foxpro-terminology.md)に接続されているデータ ソースの場合\\は '!'、[空きテーブル](../../odbc/microsoft/visual-foxpro-terminology.md)のディレクトリであるデータ ソースの場合は ' ' です。  
  
 SQL_QUALIFIER_TERMは"データベース"または"ディレクトリ"を返します。 修飾子は、データベースに接続されたデータ ソースの "[データベース](../../odbc/microsoft/visual-foxpro-terminology.md)" と空[きテーブル](../../odbc/microsoft/visual-foxpro-terminology.md)のディレクトリであるデータ ソースの "ディレクトリ" です。  
  
 SQL_QUALIFIER_USAGEはSQL_QU_PRIVILEGE_DEFINITIONをサポートしていません。SQL_QU_DML_STATEMENTまたはSQL_QU_TABLE_DEFINITIONを返します。  
  
 SQL_QUOTED_IDENTIFIER_CASEはSQL_IC_MIXEDを返します。  
  
## <a name="r"></a>R  
 SQL_ROW_UPDATESは"N"を返します。 ビジュアル フォックスプロ ODBC ドライバーは、静的カーソルと前方カーソルのみをサポートします。  
  
## <a name="s"></a>S  
 SQL_SCROLL_CONCURRENCYはSQL_SCCO_READ_ONLYを返します。  
  
 SQL_SCROLL_OPTIONSは、SQL_SO_STATICまたはSQL_SO_READONLYを返します。  
  
 SQL_SEARCH_PATTERN_ESCAPEは\\" " " を返します。  
  
 SQL_SERVER_NAMEは "" を返します。  
  
 SQL_SPECIAL_CHARACTERSは "~@@#$%^" を返します。  
  
 SQL_STATIC_SENSITIVITYは 0 を返します。 ビジュアル フォックスプロ ODBC ドライバーは、位置の更新をサポートしていません。  
  
 SQL_STRING_FUNCTIONSは、SQL_FN_STR_INSERT、SQL_FN_STR_LOCATE、SQL_FN_STR_LOCATE_2、またはSQL_FN_STR_SOUNDEXをサポートしていません。  
  
 戻り値は次のとおりです。  
  
-   SQL_FN_STR_ASCII  
  
-   SQL_FN_STR_CHAR  
  
-   SQL_FN_STR_CONCAT  
  
-   SQL_FN_STR_DIFFERENCE  
  
-   SQL_FN_STR_LCASE  
  
-   SQL_FN_STR_LEFT  
  
-   SQL_FN_STR_LENGTH  
  
-   SQL_FN_STR_LTRIM  
  
-   SQL_FN_STR_REPEAT  
  
-   SQL_FN_STR_REPLACE  
  
-   SQL_FN_STR_RIGHT  
  
-   SQL_FN_STR_RTRIM  
  
-   SQL_FN_STR_SUBSTRING  
  
-   SQL_FN_STR_UCASE  
  
-   SQL_FN_STR_SPACE。  
  
 SQL_SUBQUERIESは次の値を返します。  
  
-   SQL_SQ_CORRELATED_SUBQUERIES  
  
-   SQL_SQ_COMPARISON  
  
-   SQL_SQ_EXISTS  
  
-   SQL_SQ_IN  
  
-   SQL_SQ_QUANTIFIED。  
  
 SQL_SYSTEM_FUNCTIONS返します:  
  
-   SQL_FN_SYS_DBNAME  
  
-   SQL_FN_SYS_IFNULL  
  
 しかし、そうではありません:  
  
-   SQL_FN_SYS_USERNAME  
  
## <a name="t"></a>T  
 SQL_TABLE_TERMは "テーブル" を返します。  
  
 SQL_TIMEDATE_ADD_INTERVALSは次の値を返します。  
  
-   SQL_FN_TSI_秒  
  
-   SQL_FN_TSI_MINUTE  
  
-   SQL_FN_TSI_HOUR  
  
-   SQL_FN_TSI_DAY  
  
-   SQL_FN_TSI_MONTH  
  
-   SQL_FN_TSI_YEAR  
  
 しかし、そうではありません:  
  
-   SQL_FN_TSI_FRAC_SECOND  
  
-   SQL_FN_TSI_WEEK  
  
-   SQL_FN_TSI_QUARTER  
  
 SQL_TIMEDATE_DIFF_INTERVALSは次の値を返します。  
  
-   SQL_FN_TSI_秒  
  
-   SQL_FN_TSI_MINUTE  
  
-   SQL_FN_TSI_HOUR  
  
-   SQL_FN_TSI_DAY  
  
-   SQL_FN_TSI_MONTH  
  
-   SQL_FN_TSI_YEAR  
  
 SQL_TIMEDATE_FUNCTIONSは、SQL_FN_TD_QUARTER、SQL_FN_TD_TIMESTAMPADD、SQL_FN_TD_DAYOFYEAR、またはSQL_FN_TD_WEEKをサポートしていません。  
  
 戻り値は次のとおりです。  
  
-   SQL_FN_TD_CURDATE  
  
-   SQL_FN_TD_CURTIME  
  
-   SQL_FN_TD_DAYNAME  
  
-   SQL_FN_TD_DAYOFMONTH  
  
-   SQL_FN_TD_DAYOFWEEK  
  
-   SQL_FN_TD_HOUR  
  
-   SQL_FN_TD_MINUTE  
  
-   SQL_FN_TD_MONTH  
  
-   SQL_FN_TD_MONTHNAME  
  
-   SQL_FN_TD_NOW  
  
-   SQL_FN_TD_SECOND  
  
-   SQL_FN_TD_TIMESTAMPDIFF  
  
-   SQL_FN_TD_YEAR .  
  
 SQL_TXN_CAPABLEはSQL_TC_DMLを返します。  
  
 SQL_TXN_ISOLATION_OPTIONはSQL_TXN_READ_COMMITTEDを返します。  
  
## <a name="u-z"></a>U-Z  
 SQL_UNIONは、SQL_U_UNIONまたはSQL_U_UNION_ALLを返します。  
  
 SQL_USER_NAMEは\<空白の>を返します。
