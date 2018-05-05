---
title: SQLDescribeCol |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-api
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLDescribeCol function
ms.assetid: ffbf34c6-8268-434f-829a-82009a6cda59
caps.latest.revision: 40
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f456a88a4c56a1ddfb4470c71c13cb75a765c839
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqldescribecol"></a>SQLDescribeCol
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  ステートメントの実行、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは結果セット内の列を記述するサーバーを照会する必要はありません。 この場合、 **SQLDescribeCol**サーバーとのやり取りは行われません。 同様に[SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md)と[SQLNumResultCols](../../relational-databases/native-client-odbc-api/sqlnumresultcols.md)、呼び出し元**SQLDescribeCol**準備されてが実行されていないステートメントには、サーバーとのやり取りが生成されます。  
  
 1 つの [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントまたはステートメント バッチから複数の結果行セットが返される場合、別のテーブルの列を序数で参照したり、結果セット内の別の列を参照することができます。 **SQLDescribeCol**セットごとに呼び出す必要があります。 結果セットが変更されると、アプリケーションでは、行の結果をフェッチする前に、データ値を再バインドする必要があります。 セットを返す複数の結果を処理の詳細についてを参照してください[SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md)です。  
  
 準備された SQL ステートメントのバッチによって複数の結果セットが生成されるときは、最初の結果セットの列属性のみが報告されます。  
  
 大きな値データ型で返される値*DataTypePtr*は、SQL_VARCHAR、SQL_VARBINARY、SQL_NVARCHAR のいずれか。 値で SQL_SS_LENGTH_UNLIMITED *ColumnSizePtr*サイズが「無制限」であることを示します。  
  
 以降で、データベース エンジンの機能強化[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]SQLDescribeCol を期待する結果のより正確な記述を取得できるようにします。 以前のバージョンの SQLDescribeCol によって返される値からこれらのより正確な結果が異なる場合があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 詳細については、次を参照してください。[メタデータ検出](../../relational-databases/native-client/features/metadata-discovery.md)です。  
  
## <a name="sqldescribecol-support-for-enhanced-date-and-time-features"></a>SQLDescribeCol による機能強化された日付と時刻のサポート  
 日付型または時刻型に対して返される値を次に示します。  
  
||*DataTypePtr*|*ColumnSizePtr*|*DecimalDigitsPtr*|  
|-|-------------------|---------------------|------------------------|  
|datetime|SQL_TYPE_TIMESTAMP|23|3|  
|smalldatetime|SQL_TYPE_TIMESTAMP|16|0|  
|date|SQL_TYPE_DATE|10|0|  
|time|SQL_SS_TIME2|8, 10..16|0..7|  
|datetime2|SQL_TYPE_TIMESTAMP|19, 21..27|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|26, 28..34|0..7|  
  
 詳細については、次を参照してください。[日付と時刻の強化 (&) #40";"ODBC"&"#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)です。  
  
## <a name="sqldescribecol-support-for-large-clr-udts"></a>SQLDescribeCol による大きな CLR UDT のサポート  
 **SQLDescribeCol**大きなの CLR ユーザー定義型 (Udt) をサポートしています。 詳細については、次を参照してください。 [Large CLR User-Defined 型 (&) #40";"ODBC"&"#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLDescribeCol 関数](http://go.microsoft.com/fwlink/?LinkID=59338)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
