---
title: パラメータと結果のメタデータ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- metadata [ODBC]
ms.assetid: 1518e6e5-a6a8-4489-b779-064c5624df53
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8ba66c950f25663dabc3c0c46f83a7589df300ca
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304093"
---
# <a name="metadata---parameter-and-result"></a>メタデータ - パラメーターと結果
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  このトピックでは、日付と時刻のデータ型に対して実装パラメーター記述子 (IPD) フィールドと実装行記述子 (IRD) フィールドに返される情報について説明します。  
  
## <a name="information-returned-in-ipd-fields"></a>IPD フィールドに返される情報  
 IPD フィールドには次の情報が返されます。  
  
|パラメーターのタイプ|date|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|--------------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CONCISE_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQL_CODE_DATE|0|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|0|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|10|8,10..16|16|23|19、21..27|26、28..34|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_LENGTH|10|8,10..16|16|23|19、21..27|26、28..34|  
|SQL_DESC_OCTET_LENGTH|6|12|4|8|16|20|  
|SQL_DESC_PRECISION|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SCALE|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_TYPE|SQL_TYPE_DATE|SQL_SS_TYPE_TIME2|SQL_DATETIME|SQL_DATETIME|SQL_DATETIME|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_TYPE_NAME|**日付**|**time**|IPD の IRD、**日時 2**の**小さい日付時刻**|IPD の IRD、**日時 2**の**日時**|**datetime2**|datetimeoffset|  
|SQL_CA_SS_VARIANT_TYPE|SQL_C_TYPE_DATE|SQL_C_TYPE_BINARY|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_BINARY|  
|SQL_CA_SS_VARIANT_SQL_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_CA_SS_SERVER_TYPE|該当なし|該当なし|SQL_SS_TYPE_SMALLDATETIME|SQL_SS_TYPE_DATETIME|SQL_SS_TYPE_DEFAULT|該当なし|  
  
 値の範囲が連続しない場合があります。 たとえば、"8,10..16" には 9 がありません。 有効桁数が 0 より大きい場合は、小数点が追加されるためです。  
  
 ドライバは、すべての**SQL_TYPE_TIMESTAMP**値をサーバーに送信する際に共通の型としてこれを使用するため **、datetime2**は **、小さい日付時刻**と**日時**の型名として返されます。  
  
 SQL_CA_SS_VARIANT_SQL_TYPE は新しい記述子フィールドです。 このフィールドは、アプリケーションが**sqlvariant** (SQL_SSVARIANT) 列およびパラメーターに関連付けられた値の型を指定できるようにするために、IRD および IPD に追加されました。  
  
 SQL_CA_SS_SERVER_TYPE は新しい IPD 専用フィールドです。このフィールドによって、アプリケーションは SQL_TYPE_TYPETIMESTAMP (または C 型の SQL_C_TYPE_TIMESTAMP を持つ SQL_SS_VARIANT) としてバインドされるパラメーターの値がサーバーに送信される方法を制御できます。 SQLExecute または SQLExecDirect が呼び出されたときにSQL_DESC_CONCISE_TYPEがSQL_TYPE_TIMESTAMP (またはSQL_SS_VARIANTされ、C 型がSQL_C_TYPE_TIMESTAMP) の場合、SQL_CA_SS_SERVER_TYPEの値によって、パラメーター値の表形式データ ストリーム (TDS) 型が次のように決定されます。  
  
|SQL_CA_SS_SERVER_TYPE の値|SQL_DESC_PRECISION の有効な値|SQL_DESC_LENGTH の有効な値|TDS 型|  
|----------------------------------------|-------------------------------------------|----------------------------------------|--------------|  
|SQL_SS_TYPE_DEFAULT|0..7|19、21..27|**datetime2**|  
|SQL_SS_TYPE_SMALLDATETIME|0|19|**smalldatetime**|  
|SQL_SS_TYPE_DATETIME|3|23|**datetime**|  
  
 SQL_CA_SS_SERVER_TYPE の既定の設定は SQL_SS_TYPE_DEFAULT です。 上の表で説明したように、SQL_DESC_PRECISION および SQL_DESC_LENGTH の設定は、SQL_CA_SS_SERVER_TYPE の設定に照らし合わせて検証されます。 この検証が失敗すると、SQL_ERROR が返され、"データ型の属性に関する制限に違反しました" というメッセージで SQLState 07006 の診断レコードが記録されます。 このエラーは、SQL_CA_SS_SERVER_TYPE が SQL_SS_TYPE DEFAULT 以外の値に設定され、DESC_CONCISE_TYPE が SQL_TYPE_TIMESTAMP でない場合にも返されます。 これらの検証が実行されるのは、次のような記述子の整合性の検証が発生する場合です。  
  
-   SQL_DESC_DATA_PTR が変更されたとき  
  
-   準備時または実行時 (SQLExecute、SQLExecDirect、SQLSetPos、または SQLBulkOperations が呼び出されたとき)  
  
-   アプリケーションが、遅延準備を無効にして SQLPrepare を呼び出すか、準備が完了したが実行されていないステートメントに対して SQLNumResultCols、SQLDescribeCol、または SQLDescribeParam を呼び出すことによって、非遅延準備を強制する場合。  
  
 SQL_CA_SS_SERVER_TYPEが SQLSetDescField の呼び出しによって設定される場合、その値はSQL_SS_TYPE_DEFAULT、SQL_SS_TYPE_SMALLDATETIME、またはSQL_SS_TYPE_DATETIMEでなければなりません。 これらの値ではない場合、SQL_ERROR が返され、"無効な属性またはオプションの ID" というメッセージで SQLState HY092 の診断レコードが記録されます。  
  
 SQL_CA_SS_SERVER_TYPE属性は、 **datetime**および**smalldatetime**でサポートされる機能に依存するアプリケーションで使用できますが、 **datetime2**は使用できません。 たとえば **、datetime2**では**日付追加**関数と**dateiif**関数を使用する必要がありますが、**日時**と**小さい日付時刻**では算術演算子も使用できます。 ほとんどのアプリケーションではこの属性を使用する必要はないので、使用しないでください。  
  
## <a name="information-returned-in-ird-fields"></a>IRD フィールドに返される情報  
 IRD フィールドには次の情報が返されます。  
  
|列の型|date|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|-----------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CONCISE_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQL_CODE_DATE|0|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|0|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|10|8,10..16|16|23|19、21..27|26、28..34|  
|SQL_DESC_DISPLAY_SIZE|10|8,10..16|16|23|19、21..27|26、28..34|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_LENGTH|10|8,10..16|16|2|19、21..27|26、28..34|  
|SQL_DESC_LITERAL_PREFIX|'|'|'|'|'|'|  
|SQL_DESC_LITERAL_SUFFIX|'|'|'|'|'|'|  
|SQL_DESC_LOCAL_TYPE_NAME|**日付**|**time**|**smalldatetime**|**datetime**|**datetime2**|datetimeoffset|  
|SQL_DESC_OCTET_LENGTH|6|12|4|8|16|20|  
|SQL_DESC_PRECISION|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SCALE|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|  
|SQL_DESC_TYPE|SQL_DATETIME|SQL_SS_TIME2|SQL_DATETIME|SQL_DATETIME|SQL_DATETIME|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_TYPE_NAME|**日付**|**time**|**smalldatetime**|**datetime**|**datetime2**|datetimeoffset|  
|SQL_DESC_UNSIGNED|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;メタデータ](https://msdn.microsoft.com/library/99133efc-b1f2-46e9-8203-d90c324a8e4c)  
  
  
