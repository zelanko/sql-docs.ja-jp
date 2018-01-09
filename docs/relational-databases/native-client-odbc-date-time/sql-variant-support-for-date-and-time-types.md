---
title: "sql_variant 型の日付と時刻型のサポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-date-time
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: sql_variant data type
ms.assetid: 12ff1ea6-e2cc-40e6-910c-3126974a90b3
caps.latest.revision: "19"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2636d11a4d25a1c53c22a172020f67b90fa0df15
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="sqlvariant-support-for-date-and-time-types"></a>sql_variant 型の日付と時刻型のサポート
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  このトピックの内容について説明しますが、どのように**sql_variant**機能強化された日付と時刻データ型をサポートしています。  
  
 SQL_CA_SS_VARIANT_TYPE 列属性は、バリアント型結果列の C 型を返すために使用されます。 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]SQL_CA_SS_VARIANT_SQL_TYPE は、実装行記述子 (IRD) 内のバリアント型結果列の SQL 型を設定する、追加の属性について説明します。 SQL_SS_VARIANT 型で SQL_C_BINARY C 型 SQL_SS_TIMESTAMPOFFSET パラメーターがバインドされているまたは SQL_SS_TIME2 の SQL 型を指定する、SQL_CA_SS_VARIANT_SQL_TYPE 実装パラメーター記述子 (IPD) での使用することができますも。  
  
 SQLColAttribute によって sql_ss_time2 型および SQL_SS_TIMESTAMPOFFSET、新しい型を設定できます。 SQL_CA_SS_VARIANT_SQL_TYPE は、SQLGetDescField によって返されることができます。  
  
 結果列については、ドライバーによってバリアント型から日付型または時刻型に変換されます。 詳細については、次を参照してください。 [SQL から C への変換](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)です。SQL_C_BINARY へのバインドでは、バッファー長は、SQL 型に対応する構造体を受け取るのに十分な大きさである必要があります。  
  
 ドライバーに C の値を変換、sql_ss_time2 型および SQL_SS_TIMESTAMPOFFSET パラメーターの**sql_variant**値は、次の表で説明します。 パラメーターが SQL_C_BINARY としてバインドされ、かつ、サーバー型が SQL_SS_VARIANT である場合、アプリケーションで SQL_CA_SS_VARIANT_SQL_TYPE が別の SQL 型に設定されていない限り、バイナリ値として扱われます。 この場合は、SQL_CA_SS_VARIANT_SQL_TYPE が優先されます。つまり、SQL_CA_SS_VARIANT_SQL_TYPE が設定されている場合、C 型からバリアントの SQL 型を推定するという既定の動作がオーバーライドされます。  
  
|C 型|サーバーの種類|コメント|  
|------------|-----------------|--------------|  
|SQL_C_CHAR|varchar|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_WCHAR|nvarcar|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_TINYINT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_STINYINT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_SHORT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_SSHORT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_USHORT|ssNoversion|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_LONG|ssNoversion|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_SLONG|ssNoversion|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_ULONG|BIGINT|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_SBIGINT|BIGINT|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_FLOAT|REAL|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_DOUBLE|FLOAT|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_BIT|bit|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_UTINYINT|TINYINT|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_BINARY|varbinary|SQL_CA_SS_VARIANT_SQL_TYPE は設定されません。|  
|SQL_C_BINARY|time|SQL_CA_SS_VARIANT_SQL_TYPE = SQL_SS_TIME2<br /><br /> 小数点以下桁数は SQL_DESC_PRECISION に設定 (、 *DecimalDigits*のパラメーター **SQLBindParameter**)。|  
|SQL_C_BINARY|datetimeoffset|SQL_CA_SS_VARIANT_SQL_TYPE = SQL_SS_TIMESTAMPOFFSET<br /><br /> 小数点以下桁数は SQL_DESC_PRECISION に設定 (、 *DecimalDigits*のパラメーター **SQLBindParameter**)。|  
|SQL_C_TYPE_DATE|日付|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_TYPE_TIME|time(0)|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_TYPE_TIMESTAMP|datetime2|小数点以下桁数は SQL_DESC_PRECISION に設定 (、 *DecimalDigits*のパラメーター **SQLBindParameter**)。|  
|SQL_C_NUMERIC|Decimal|有効桁数は SQL_DESC_PRECISION に設定 (、 *ColumnSize*のパラメーター **SQLBindParameter**)。<br /><br /> 小数点以下桁数は SQL_DESC_SCALE に設定 (、 *DecimalDigits* SQLBindParameter のパラメーター)。|  
|SQL_C_SS_TIME2|time|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_SS_TIMESTAMPOFFSET|datetimeoffset|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
  
## <a name="see-also"></a>参照  
 [日付と時刻の強化 &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
  
