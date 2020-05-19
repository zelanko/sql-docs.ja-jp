---
title: パラメーターと結果のメタデータ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- metadata [ODBC]
ms.assetid: 1518e6e5-a6a8-4489-b779-064c5624df53
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: fcac538ee01da719d43015408337f63a09f15d18
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705445"
---
# <a name="parameter-and-result-metadata"></a>パラメーターと結果のメタデータ
  このトピックでは、日付と時刻のデータ型に対して実装パラメーター記述子 (IPD) フィールドと実装行記述子 (IRD) フィールドに返される情報について説明します。  
  
## <a name="information-returned-in-ipd-fields"></a>IPD フィールドに返される情報  
 IPD フィールドには次の情報が返されます。  
  
|パラメーターのタイプ|date|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|--------------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CONCISE_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQL_CODE_DATE|0|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|0|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|10|8、10.. 16|16|23|19、21..27|26、28..34|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_LENGTH|10|8、10.. 16|16|23|19、21..27|26、28..34|  
|SQL_DESC_OCTET_LENGTH|6|12|4|8|16|20|  
|SQL_DESC_PRECISION|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SCALE|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_TYPE|SQL_TYPE_DATE|SQL_SS_TYPE_TIME2|SQL_DATETIME|SQL_DATETIME|SQL_DATETIME|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_TYPE_NAME|`date`|`time`|IRD では `smalldatetime`、IPD では `datetime2`|IRD では `datetime`、IPD では `datetime2`|`datetime2`|datetimeoffset|  
|SQL_CA_SS_VARIANT_TYPE|SQL_C_TYPE_DATE|SQL_C_TYPE_BINARY|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_BINARY|  
|SQL_CA_SS_VARIANT_SQL_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_CA_SS_SERVER_TYPE|N/A|N/A|SQL_SS_TYPE_SMALLDATETIME|SQL_SS_TYPE_DATETIME|SQL_SS_TYPE_DEFAULT|N/A|  
  
 値の範囲が連続しない場合があります。 たとえば、"8,10..16" には 9 がありません。 有効桁数が 0 より大きい場合は、小数点が追加されるためです。  
  
 ドライバーですべての `datetime2` 値をサーバーに送信するための共通の型として使用されるため、`smalldatetime` は、`datetime` および `SQL_TYPE_TIMESTAMP` の typename として返されます。  
  
 SQL_CA_SS_VARIANT_SQL_TYPE は新しい記述子フィールドです。 このフィールドは、アプリケーションで `sqlvariant` (SQL_SSVARIANT) 列とパラメーターに関連付けられた値の型を指定できるようにするために IRD と IPD に追加されました。  
  
 SQL_CA_SS_SERVER_TYPE は新しい IPD 専用フィールドです。このフィールドによって、アプリケーションは SQL_TYPE_TYPETIMESTAMP (または C 型の SQL_C_TYPE_TIMESTAMP を持つ SQL_SS_VARIANT) としてバインドされるパラメーターの値がサーバーに送信される方法を制御できます。 SQLExecute または SQLExecDirect が呼び出されたときに SQL_DESC_CONCISE_TYPE が SQL_TYPE_TIMESTAMP (または SQL_SS_VARIANT で C 型が SQL_C_TYPE_TIMESTAMP) の場合、次のように SQL_CA_SS_SERVER_TYPE の値によって、パラメーター値の表形式のデータストリーム (TDS) の型が決定されます。  
  
|SQL_CA_SS_SERVER_TYPE の値|SQL_DESC_PRECISION の有効な値|SQL_DESC_LENGTH の有効な値|TDS 型|  
|----------------------------------------|-------------------------------------------|----------------------------------------|--------------|  
|SQL_SS_TYPE_DEFAULT|0..7|19、21..27|`datetime2`|  
|SQL_SS_TYPE_SMALLDATETIME|0|19|`smalldatetime`|  
|SQL_SS_TYPE_DATETIME|3|23|`datetime`|  
  
 SQL_CA_SS_SERVER_TYPE の既定の設定は SQL_SS_TYPE_DEFAULT です。 上の表で説明したように、SQL_DESC_PRECISION および SQL_DESC_LENGTH の設定は、SQL_CA_SS_SERVER_TYPE の設定に照らし合わせて検証されます。 この検証が失敗すると、SQL_ERROR が返され、"データ型の属性に関する制限に違反しました" というメッセージで SQLState 07006 の診断レコードが記録されます。 このエラーは、SQL_CA_SS_SERVER_TYPE が SQL_SS_TYPE DEFAULT 以外の値に設定され、DESC_CONCISE_TYPE が SQL_TYPE_TIMESTAMP でない場合にも返されます。 これらの検証が実行されるのは、次のような記述子の整合性の検証が発生する場合です。  
  
-   SQL_DESC_DATA_PTR が変更されたとき  
  
-   準備時または実行時 (SQLExecute、SQLExecDirect、SQLSetPos、または SQLBulkOperations が呼び出されたとき)  
  
-   アプリケーションが遅延準備を無効にして SQLPrepare を呼び出すか、準備されて実行されていないステートメントに対して SQLNumResultCols、SQLDescribeCol、または SQLDescribeParam を呼び出すことによって、遅延なしの準備を強制する場合。  
  
 SQLSetDescField の呼び出しによって SQL_CA_SS_SERVER_TYPE が設定されている場合、その値は SQL_SS_TYPE_DEFAULT、SQL_SS_TYPE_SMALLDATETIME、または SQL_SS_TYPE_DATETIME である必要があります。 これらの値ではない場合、SQL_ERROR が返され、"無効な属性またはオプションの ID" というメッセージで SQLState HY092 の診断レコードが記録されます。  
  
 SQL_CA_SS_SERVER_TYPE 属性を使用できるのは、`datetime` および `smalldatetime` でサポートされ、`datetime2` ではサポートされない機能に依存するアプリケーションです。 たとえば、では、 `datetime2` `dateadd` 関数と**datediif**関数を使用する必要があります。一方、では `datetime` `smalldatetime` 算術演算子も使用できます。 ほとんどのアプリケーションではこの属性を使用する必要はないので、使用しないでください。  
  
## <a name="information-returned-in-ird-fields"></a>IRD フィールドに返される情報  
 IRD フィールドには次の情報が返されます。  
  
|列の型|date|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|-----------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CONCISE_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQL_CODE_DATE|0|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|0|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|10|8、10.. 16|16|23|19、21..27|26、28..34|  
|SQL_DESC_DISPLAY_SIZE|10|8、10.. 16|16|23|19、21..27|26、28..34|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_LENGTH|10|8、10.. 16|16|2|19、21..27|26、28..34|  
|SQL_DESC_LITERAL_PREFIX|'|'|'|'|'|'|  
|SQL_DESC_LITERAL_SUFFIX|'|'|'|'|'|'|  
|SQL_DESC_LOCAL_TYPE_NAME|`date`|`time`|`smalldatetime`|`datetime`|`datetime2`|datetimeoffset|  
|SQL_DESC_OCTET_LENGTH|6|12|4|8|16|20|  
|SQL_DESC_PRECISION|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SCALE|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|  
|SQL_DESC_TYPE|SQL_DATETIME|SQL_SS_TIME2|SQL_DATETIME|SQL_DATETIME|SQL_DATETIME|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_TYPE_NAME|`date`|`time`|`smalldatetime`|`datetime`|`datetime2`|datetimeoffset|  
|SQL_DESC_UNSIGNED|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;メタデータ](../../database-engine/dev-guide/metadata-odbc.md)  
  
  
