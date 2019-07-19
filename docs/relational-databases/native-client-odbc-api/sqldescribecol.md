---
title: SQLDescribeCol |Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLDescribeCol function
ms.assetid: ffbf34c6-8268-434f-829a-82009a6cda59
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c17441f8e3fa538280ef350200126d0ad14eeb1d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68035660"
---
# <a name="sqldescribecol"></a>SQLDescribeCol
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  実行されるステートメントを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client ODBC ドライバーは結果セット内の列を示すサーバー クエリを実行する必要はありません。 この場合、 **SQLDescribeCol**サーバーとのやり取りは行われません。 ような[SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md)と[SQLNumResultCols](../../relational-databases/native-client-odbc-api/sqlnumresultcols.md)を呼び出すと、 **SQLDescribeCol**準備されていても実行されていないステートメントには、サーバーとのやり取りが生成されます。  
  
 1 つの [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントまたはステートメント バッチから複数の結果行セットが返される場合、別のテーブルの列を序数で参照したり、結果セット内の別の列を参照することができます。 **SQLDescribeCol**セットごとに呼び出す必要があります。 結果セットが変更されると、アプリケーションでは、行の結果をフェッチする前に、データ値を再バインドする必要があります。 セットを返す複数の結果の処理の詳細についてを参照してください[SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md)します。  
  
 準備された SQL ステートメントのバッチによって複数の結果セットが生成されるときは、最初の結果セットの列属性のみが報告されます。  
  
 大きな値のデータ型で返される値*DataTypePtr* SQL_VARCHAR、SQL_VARBINARY、SQL_NVARCHAR のいずれかです。 値で SQL_SS_LENGTH_UNLIMITED *ColumnSizePtr*サイズが「無制限」であることを示します。  
  
 以降では、データベース エンジンの機能強化[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]期待どおりの結果のより正確な記述を取得する SQLDescribeCol を許可します。 これらのより正確な結果の以前のバージョンの SQLDescribeCol によって返される値が異なる場合があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 詳細については、次を参照してください。[メタデータ検出](../../relational-databases/native-client/features/metadata-discovery.md)します。  
  
## <a name="sqldescribecol-support-for-enhanced-date-and-time-features"></a>SQLDescribeCol による機能強化された日付と時刻のサポート  
 日付型または時刻型に対して返される値を次に示します。  
  
||*DataTypePtr*|*ColumnSizePtr*|*DecimalDigitsPtr*|  
|-|-------------------|---------------------|------------------------|  
|DATETIME|SQL_TYPE_TIMESTAMP|23|3|  
|smalldatetime|SQL_TYPE_TIMESTAMP|16|0|  
|日付|SQL_TYPE_DATE|10|0|  
|time|SQL_SS_TIME2|8, 10..16|0..7|  
|datetime2|SQL_TYPE_TIMESTAMP|19, 21..27|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|26, 28..34|0..7|  
  
 詳細については、次を参照してください。[日付と時刻の強化&#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)します。  
  
## <a name="sqldescribecol-support-for-large-clr-udts"></a>SQLDescribeCol による大きな CLR UDT のサポート  
 **SQLDescribeCol**大きなの CLR ユーザー定義型 (Udt) をサポートしています。 詳細については、次を参照してください。 [Large CLR User-Defined 型&#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)します。  
  
## <a name="see-also"></a>参照  
 [SQLDescribeCol 関数](https://go.microsoft.com/fwlink/?LinkID=59338)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
