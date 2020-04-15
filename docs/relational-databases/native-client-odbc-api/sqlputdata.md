---
title: データの変換 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLPutData function
ms.assetid: d39aaa5b-7fbc-4315-a7f2-5a7787e04f25
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e063d1053d8a6e5e10a1234d33893adf27fbc3ad
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302355"
---
# <a name="sqlputdata"></a>SQLPutData
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  SQLPutData を使用して、SQL_LONGVARCHAR ( text ) 、 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ntext**) または SQL_LONGVARBINARY (**イメージ**) 列に対して、65,535 バイトを超えるデータ (**text**バージョン 4.21a の場合) または 400 KB のデータ (SQL Server バージョン 6.0 以降) を送信する場合 SQL_WLONGVARCHARは、次の制限が適用されます。  
  
-   参照されるパラメーターは、INSERT ステートメントの*insert_value*にすることができます。  
  
-   参照されるパラメーターは、UPDATE ステートメントの SET 文節内の*式*にすることができます。  
  
 ブロック内のデータをブロック内で提供する一連の SQLPutData[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]呼び出しを、バージョン 6.5 以前のバージョンを使用する場合に、列の値が部分的に更新されます。 SQLCancel が呼び出されたときに参照されていた**テキスト** **、ntext、** または**image**列は、中間のプレースホルダー値に設定されます。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 以前のバージョンへの接続をサポートしません。  
  
## <a name="diagnostics"></a>診断  
 SQLPutData[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]には、ネイティブ クライアント固有の SQLSTATE が 1 つあります。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|22026|文字列データの長さが合致しません|送信するデータの長さがアプリケーションによって指定されている場合 (例えば、SQL_LEN_DATA_AT_EXEC(*n*) *(n)* が 0 より大きい場合、 SQLPutData を介してアプリケーションが指定したバイトの総数は、指定された長さと一致する必要があります。|  
  
## <a name="sqlputdata-and-table-valued-parameters"></a>SQLPutData とテーブル値パラメーター  
 SQLPutData は、テーブル値パラメーターを持つ変数行バインディングを使用する場合にアプリケーションで使用されます。 *StrLen_Or_Ind*パラメーターは、次の行またはテーブル値パラメーター データの行のデータを収集するドライバーの準備ができているか、それ以上の行が利用できることを示します。  
  
-   値が 0 を超える場合は、次の行の値のセットを使用できることを示します。  
  
-   値が 0 の場合は、送信される行がなくなったことを示します。  
  
-   値が 0 未満の場合は、エラーが発生し、"文字列長またはバッファー長が正しくありません" というメッセージで SQLState HY090 の診断レコードが記録されます。  
  
 *DataPtr*パラメーターは無視されますが、NULL 以外の値に設定する必要があります。 詳細については、「[テーブル値パラメーターおよび列値のバインドとデータ転送](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)」の「可変 TVP 行のバインド」のセクションを参照してください。  
  
 *StrLen_Or_Ind*がSQL_DEFAULT_PARAM以外の値、または 0 から SQL_PARAMSET_SIZEまでの間の値 (つまり、SQLBindParameter の*ColumnSize*パラメーター) を持つ場合は、エラーになります。 このエラーが発生すると、SQLPutData は、"文字列長またはバッファー長が正しくありません" というメッセージで SQLSTATE=HY090 の SQL_ERROR を返します。  
  
 テーブル値パラメーターの詳細については、「 [ODBC&#41;&#40;テーブル値パラメーター ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。  
  
## <a name="sqlputdata-support-for-enhanced-date-and-time-features"></a>SQLPutData による機能強化された日付と時刻のサポート  
 日付/時刻型のパラメーター値は、 C[から SQL への変換](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)で説明されているように変換されます。  
  
 詳細については、「 [ODBC&#41;&#40;日付と時刻の向上](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。  
  
## <a name="sqlputdata-support-for-large-clr-udts"></a>SQLPutData による大きな CLR UDT のサポート  
 **SQLPutData は**、大規模な CLR ユーザー定義型 (UDT) をサポートします。 詳細については、「 [ODBC&#41;&#40;大規模な CLR ユーザー定義型](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [関数](https://go.microsoft.com/fwlink/?LinkId=59365)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
