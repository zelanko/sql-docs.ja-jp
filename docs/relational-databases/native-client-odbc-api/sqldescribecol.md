---
title: SQL コガライコル |マイクロソフトドキュメント
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e0e9a03b2e8635618afbdc615a6f77dfe05c533e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302585"
---
# <a name="sqldescribecol"></a>SQLDescribeCol
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  実行されたステートメントの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]場合、ネイティブ クライアント ODBC ドライバーは、結果セット内の列を記述するためにサーバーにクエリを実行する必要はありません。 この場合 **、SQLDescribeCol**はサーバーのラウンドトリップを発生しません。 [SQLCol 属性](../../relational-databases/native-client-odbc-api/sqlcolattribute.md)と[SQLNumResultCols](../../relational-databases/native-client-odbc-api/sqlnumresultcols.md)と同様に、準備されたステートメントではなく実行されたステートメントで**SQLDescribeCol**を呼び出すと、サーバーラウンドトリップが生成されます。  
  
 1 つの [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントまたはステートメント バッチから複数の結果行セットが返される場合、別のテーブルの列を序数で参照したり、結果セット内の別の列を参照することができます。 **SQLDescribeCol**は、各セットに対して呼び出す必要があります。 結果セットが変更されると、アプリケーションでは、行の結果をフェッチする前に、データ値を再バインドする必要があります。 複数の結果セットの戻り値の処理の詳細については、 [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md)を参照してください。  
  
 準備された SQL ステートメントのバッチによって複数の結果セットが生成されるときは、最初の結果セットの列属性のみが報告されます。  
  
 大きな値のデータ型の場合 *、DataTypePtr*で返される値は、SQL_VARCHAR、SQL_VARBINARY、またはSQL_NVARCHARです。 *ColumnSizePtr*の値がSQL_SS_LENGTH_UNLIMITEDの場合、サイズは 「無制限」であることを示します。  
  
 データベース エンジンの機能強化の開始[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]により、SQLDescribeCol は期待される結果のより正確な説明を取得できます。 これらのより正確な結果は、以前のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQLDescribeCol によって返される値とは異なる場合があります。 詳細については、「[メタデータの検出](../../relational-databases/native-client/features/metadata-discovery.md)」を参照してください。  
  
## <a name="sqldescribecol-support-for-enhanced-date-and-time-features"></a>SQLDescribeCol による機能強化された日付と時刻のサポート  
 日付型または時刻型に対して返される値を次に示します。  
  
||*データ型Ptr*|*サイズ変更*|*10 進数の桁数Ptr*|  
|-|-------------------|---------------------|------------------------|  
|DATETIME|SQL_TYPE_TIMESTAMP|23|3|  
|smalldatetime|SQL_TYPE_TIMESTAMP|16|0|  
|date|SQL_TYPE_DATE|10|0|  
|time|SQL_SS_TIME2|8、10..16|0..7|  
|datetime2|SQL_TYPE_TIMESTAMP|19、21..27|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|26、28..34|0..7|  
  
 詳細については、「 [ODBC&#41;&#40;日付と時刻の向上](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。  
  
## <a name="sqldescribecol-support-for-large-clr-udts"></a>SQLDescribeCol による大きな CLR UDT のサポート  
 **大規模**な CLR ユーザー定義型 (UDT) をサポートしています。 詳細については、「 [ODBC&#41;&#40;大規模な CLR ユーザー定義型](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [関数の記述](https://go.microsoft.com/fwlink/?LinkID=59338)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
