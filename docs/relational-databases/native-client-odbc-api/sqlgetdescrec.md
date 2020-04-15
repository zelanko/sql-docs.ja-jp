---
title: をクリックする |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLGetDescRec function
ms.assetid: f3389ff2-f3be-4035-9fb5-c9ebc2f15025
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 42c8a45bb50e5fda8946cc3819aa4702f5c2fb3f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299562"
---
# <a name="sqlgetdescrec"></a>SQLGetDescRec
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  このトピックでは、ネイティブ クライアントに固有の SQLGetDescRec 機能について[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]説明します。  
  
## <a name="sqlgetdescrec-and-table-valued-parameters"></a>SQLGetDescRec とテーブル値パラメーター  
 SQLGetDescRec を使用して、テーブル値パラメーターおよびテーブル値パラメーター列の属性の値を取得できます。 パラメーターの*パラメーター*は、パラメーターパラメーターに対応します。 *ParameterNumber*  
  
 テーブル値パラメーター列は、記述子のヘッダー フィールド SQL_SOPT_SS_PARAM_FOCUS に、SQL_DESC_TYPE が SQL_SS_TABLE に設定されているレコードの序数が設定される場合のみ使用できます。 SQL_SOPT_SS_PARAM_FOCUSの詳細については、 [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)を参照してください。  
  
 次のデータを返します。  
  
|パラメーター|テーブル値パラメーター|テーブル値パラメーター列とその他のパラメーター|  
|---------------|-----------------------------|----------------------------------------------------------|  
|*名前*|ストアド プロシージャ呼び出しの場合は仮パラメーター名。それ以外の場合は長さが 0 の文字列。|テーブル値パラメーター列の名前。|  
|*タイププター*|SQL_DESC_TYPE。 テーブル値パラメーターの場合、これは SQL_SS_TABLE です。|SQL_DESC_TYPE|  
|*サブタイププター*|未定義。|SQL_DESC_DATETIME_INTERVAL_CODE (SQL_DATETIME 型または SQL_INTERVAL 型のレコードの場合)。|  
|*長さPtr*|0|SQL_DESC_OCTET_LENGTH|  
|*プレシジョンプター*|0|SQL_DESC_PRECISION|  
|*スケールプター*|0|SQL_DESC_SCALE|  
|*Null 可能なPtr*|1|SQL_DESC_NULLABLE|  
  
 テーブル値パラメーターの詳細については、「 [ODBC&#41;&#40;テーブル値パラメーター ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。  
  
## <a name="sqlgetdescrec-support-for-enhanced-date-and-time-features"></a>SQLGetDescRec による機能強化された日付と時刻のサポート  
 日付型または時刻型に対して返される値を次に示します。  
  
||*タイププター*|*サブタイププター*|*長さPtr*|*プレシジョンプター*|*スケールプター*|  
|-|---------------|------------------|-----------------|--------------------|----------------|  
|DATETIME|SQL_DATETIME|SQL_CODE_TIMESTAMP|4|3|3|  
|smalldatetime|SQL_DATETIME|SQL_CODE_TIMESTAMP|8|0|0|  
|date|SQL_DATETIME|SQL_CODE_DATE|6|0|0|  
|time|SQL_SS_TIME2|0|10|0..7|0..7|  
|datetime2|SQL_DATETIME|SQL_CODE_TIMESTAMP|16|0..7|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|0|20|0..7|0..7|  
  
 詳細については、「 [ODBC&#41;&#40;日付と時刻の向上](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。  
  
## <a name="sqlgetdescrec-support-for-large-clr-udts"></a>SQLGetDescRec による大きな CLR UDT のサポート  
 **大規模**な CLR ユーザー定義型 (UDT) をサポートしています。 詳細については、「 [ODBC&#41;&#40;大規模な CLR ユーザー定義型](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [をクリックします。](https://go.microsoft.com/fwlink/?LinkId=80707)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
