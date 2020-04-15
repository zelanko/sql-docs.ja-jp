---
title: 列 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLProcedureColumns function
ms.assetid: 6671e180-0072-4de5-90f5-314306d2ba9c
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1b942126a5ad73d5c41f28f60a63d22ef8584f24
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280081"
---
# <a name="sqlprocedurecolumns"></a>SQLProcedureColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **すべての**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ストアド プロシージャの戻り値属性を報告する 1 行を返します。  
  
 **値が***カタログ名*、*スキーマ名*、*プロシージャ*名、または*列名*のパラメーターに存在するかどうかをSQL_SUCCESSを返します。 **SQLFetch**は、これらのパラメーターで無効な値が使用されている場合にSQL_NO_DATAを返します。  
  
 **静的**サーバー カーソルに対して実行できます。 更新可能 (動的またはキーセット) カーソルで**SQLProcedureColumns**を実行しようとすると、カーソルの種類が変更されたことを示すSQL_SUCCESS_WITH_INFOが返されます。  
  
 次の表は、結果セットによって返される列と、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバーを介して**udt**および**xml**データ型を処理するためにどのように拡張されたかを示しています。  
  
|列名|説明|  
|-----------------|-----------------|  
|SS_UDT_CATALOG_NAME|UDT (ユーザー定義型) を含むカタログの名前を返します。|  
|SS_UDT_SCHEMA_NAME|UDT を含むスキーマの名前を返します。|  
|SS_UDT_ASSEMBLY_TYPE_NAME|UDT のアセンブリ修飾名を返します。|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|XML スキーマ コレクション名が定義されているカタログの名前を返します。 カタログ名が見つからない場合は、この変数に空文字列が含まれます。|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|XML スキーマ コレクション名が定義されているスキーマの名前を返します。 スキーマ名が見つからない場合は、この変数に空文字列が含まれます。|  
|SS_XML_SCHEMACOLLECTION_NAME|XML スキーマ コレクションの名前を返します。 名前が見つからない場合は、この変数に空文字列が含まれます。|  
  
## <a name="sqlprocedurecolumns-and-table-valued-parameters"></a>SQLProcedureColumns とテーブル値パラメーター  
 SQLProcedureColumns は、CLR ユーザー定義型と同様の方法でテーブル値パラメーターを処理します。 テーブル値パラメーターに対して返される行では、列に次の値が設定されます。  
  
|列名|説明/値|  
|-----------------|------------------------|  
|DATA_TYPE|SQL_SS_TABLE|  
|TYPE_NAME|テーブル値パラメーターのテーブル型の名前。|  
|COLUMN_SIZE|NULL|  
|BUFFER_LENGTH|0|  
|DECIMAL_DIGITS|テーブル値パラメーターの列数。|  
|NUM_PREC_RADIX|NULL|  
|NULLABLE|SQL_NULLABLE|  
|REMARKS|NULL|  
|COLUMN_DEF|NULL。 テーブル型には既定値がない場合があります。|  
|SQL_DATA_TYPE|SQL_SS_TABLE|  
|SQL_DATEIME_SUB|NULL|  
|CHAR_OCTET_LENGTH|NULL|  
|IS_NULLABLE|"YES"|  
|SS_TYPE_CATALOG_NAME|テーブル型または CLR ユーザー定義型を含むカタログの名前を返します。|  
|SS_TYPE_SCHEMA_NAME|テーブル型または CLR ユーザー定義型を含むスキーマの名前を返します。|  
  
 SS_TYPE_CATALOG_NAME 列および SS_TYPE_SCHEMA_NAME 列は [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンで利用可能であり、これらの列はそれぞれ、テーブル値パラメーターのカタログとスキーマを返します。 テーブル値パラメーターに加え CLR ユーザー定義型パラメーターに対しても、これらの列が作成されます  (CLR ユーザー定義型パラメーターの既存のスキーマ列とカタログ列は、この追加機能の影響を受けません。 これらの列は、旧バージョンとの互換性を維持するためにも作成されます)。  
  
 SS_TYPE_CATALOG_NAME および SS_TYPE_SCHEMA_NAME は、ODBC 仕様に準拠して、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で追加されたドライバー固有のすべての列の前、かつ ODBC 自体によって指定されるすべての列の後に作成されます。  
  
 テーブル値パラメーターの詳細については、「 [ODBC&#41;&#40;テーブル値パラメーター ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。  
  
## <a name="sqlprocedurecolumns-support-for-enhanced-date-and-time-features"></a>SQLProcedureColumns による機能強化された日付と時刻のサポート  
 日付/時刻型の値が返される場合は、[カタログ メタデータ](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md)を参照してください。  
  
 詳細については、「 ODBC [&#41;&#40;日付と時刻の向上](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。  
  
## <a name="sqlprocedurecolumns-support-for-large-clr-udts"></a>SQLProcedureColumns による大きな CLR UDT のサポート  
 **大規模**な CLR ユーザー定義型 (UDT) をサポートしています。 詳細については、「 [ODBC&#41;&#40;大規模な CLR ユーザー定義型](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [関数](https://go.microsoft.com/fwlink/?LinkId=59363)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
