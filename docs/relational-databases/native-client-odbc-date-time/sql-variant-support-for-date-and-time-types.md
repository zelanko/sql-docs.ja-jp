---
title: sql_variant による日付と時刻型向けのサポート |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- sql_variant data type
ms.assetid: 12ff1ea6-e2cc-40e6-910c-3126974a90b3
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 718fc8b9a323ca6b1575021d748afde527dfb872
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68062430"
---
# <a name="sql_variant-support-for-date-and-time-types"></a>sql_variant による日付型と時刻型のサポート
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  このトピックで説明する方法、 **sql_variant**機能強化された日付と時刻データ型をサポートしています。  
  
 SQL_CA_SS_VARIANT_TYPE 列属性は、バリアント型結果列の C 型を返すために使用されます。 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SQL_CA_SS_VARIANT_SQL_TYPE は、実装行記述子 (IRD) 内のバリアント型結果列の SQL 型を設定する、追加の属性について説明します。 SQL_SS_VARIANT 型で SQL_C_BINARY C 型を持つ SQL_SS_TIMESTAMPOFFSET パラメーターがバインドされているまたは SQL_SS_TIME2 の SQL 型を指定する実装パラメーター記述子 (IPD) で SQL_CA_SS_VARIANT_SQL_TYPE が使用こともできます。  
  
 SQLColAttribute によって SQL_SS_TIME2 および SQL_SS_TIMESTAMPOFFSET、新しい型を設定できます。 SQL_CA_SS_VARIANT_SQL_TYPE は、SQLGetDescField によって返されることができます。  
  
 結果列については、ドライバーによってバリアント型から日付型または時刻型に変換されます。 詳細については、次を参照してください。 [SQL から C への変換](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)します。SQL_C_BINARY へのバインドでは、バッファー長は、SQL 型に対応する構造体を受け取るのに十分な大きさである必要があります。  
  
 ドライバーがする C の値を変換、SQL_SS_TIME2 および SQL_SS_TIMESTAMPOFFSET パラメーターの**sql_variant**値は、次の表で説明されているとします。 パラメーターが SQL_C_BINARY としてバインドされ、かつ、サーバー型が SQL_SS_VARIANT である場合、アプリケーションで SQL_CA_SS_VARIANT_SQL_TYPE が別の SQL 型に設定されていない限り、バイナリ値として扱われます。 この場合は、SQL_CA_SS_VARIANT_SQL_TYPE が優先されます。つまり、SQL_CA_SS_VARIANT_SQL_TYPE が設定されている場合、C 型からバリアントの SQL 型を推定するという既定の動作がオーバーライドされます。  
  
|C 型|サーバーの種類|コメント|  
|------------|-----------------|--------------|  
|SQL_C_CHAR|varchar|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_WCHAR|nvarcar|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_TINYINT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_STINYINT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_SHORT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_SSHORT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_USHORT|int|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_LONG|int|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_SLONG|int|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_ULONG|BIGINT|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_SBIGINT|BIGINT|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_FLOAT|REAL|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_DOUBLE|FLOAT|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_BIT|bit|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_UTINYINT|TINYINT|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_BINARY|varbinary|SQL_CA_SS_VARIANT_SQL_TYPE は設定されません。|  
|SQL_C_BINARY|time|SQL_CA_SS_VARIANT_SQL_TYPE = SQL_SS_TIME2<br /><br /> スケール セットは SQL_DESC_PRECISION (、 *DecimalDigits*パラメーターの**SQLBindParameter**)。|  
|SQL_C_BINARY|datetimeoffset|SQL_CA_SS_VARIANT_SQL_TYPE = SQL_SS_TIMESTAMPOFFSET<br /><br /> スケール セットは SQL_DESC_PRECISION (、 *DecimalDigits*パラメーターの**SQLBindParameter**)。|  
|SQL_C_TYPE_DATE|日付|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_TYPE_TIME|time(0)|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_TYPE_TIMESTAMP|datetime2|スケール セットは SQL_DESC_PRECISION (、 *DecimalDigits*パラメーターの**SQLBindParameter**)。|  
|SQL_C_NUMERIC|Decimal|有効桁数は SQL_DESC_PRECISION に設定されます (、 *ColumnSize*パラメーターの**SQLBindParameter**)。<br /><br /> スケール セットの SQL_DESC_SCALE (、 *DecimalDigits* SQLBindParameter のパラメーター)。|  
|SQL_C_SS_TIME2|time|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
|SQL_C_SS_TIMESTAMPOFFSET|datetimeoffset|SQL_CA_SS_VARIANT_SQL_TYPE は無視されます。|  
  
## <a name="see-also"></a>参照  
 [日付と時刻の強化&#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
  
