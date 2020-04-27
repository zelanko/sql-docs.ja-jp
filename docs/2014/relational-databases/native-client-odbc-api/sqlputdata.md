---
title: SQLPutData |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLPutData function
ms.assetid: d39aaa5b-7fbc-4315-a7f2-5a7787e04f25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7e15353cd9f4c4a837fe5978d00259ad5460d50d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63046627"
---
# <a name="sqlputdata"></a>SQLPutData
  SQLPutData を使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、SQL_LONGVARCHAR (`text`)、SQL_WLONGVARCHAR (`ntext`)、または SQL_LONGVARBINARY (`image`) 列に対して65535バイトを超えるデータ 400 (SQL Server バージョン6.0 以降) を送信する場合は、次の制限が適用されます。  
  
-   参照されるパラメーターには、INSERT ステートメント内の*insert_value*を指定できます。  
  
-   参照されるパラメーターは、UPDATE ステートメントの SET 句の*式*にすることができます。  
  
 を実行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]しているサーバーにブロック内のデータを提供する sqlputdata 呼び出しのシーケンスをキャンセルすると、バージョン6.5 以前を使用しているときに列の値が部分的に更新されます。 SQLCancel `text`が`ntext`呼び出され`image`たときに参照された、、または列は、中間プレースホルダー値に設定されます。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 以前のバージョンへの接続をサポートしません。  
  
## <a name="diagnostics"></a>診断  
 SQLPutData [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]には、Native Client 固有の SQLSTATE が1つあります。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|22026|文字列データの長さが合致しません|たとえば SQL_LEN_DATA_AT_EXEC (*n*) を使用して、送信されるデータの長さ (バイト単位) がアプリケーションによって指定されている場合 ( *n*が0を超える場合)、sqlputdata を使用してアプリケーションで指定されたバイト数の合計が、指定された長さと一致している必要があります。|  
  
## <a name="sqlputdata-and-table-valued-parameters"></a>SQLPutData とテーブル値パラメーター  
 SQLPutData は、テーブル値パラメーターとの変数行バインドを使用する場合に、アプリケーションによって使用されます。 *StrLen_Or_Ind*パラメーターは、ドライバーがテーブル値パラメーターデータの次の行または行のデータを収集できる状態であること、または使用可能な行がないことを示します。  
  
-   値が 0 を超える場合は、次の行の値のセットを使用できることを示します。  
  
-   値が 0 の場合は、送信される行がなくなったことを示します。  
  
-   値が 0 未満の場合は、エラーが発生し、"文字列長またはバッファー長が正しくありません" というメッセージで SQLState HY090 の診断レコードが記録されます。  
  
 *DataPtr*パラメーターは無視されますが、NULL 以外の値に設定する必要があります。 詳細については、「バインド」の「変数 TVP 行バインド」[と「テーブル値パラメーターと列の値のデータ転送](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)」を参照してください。  
  
 *StrLen_Or_Ind*に SQL_DEFAULT_PARAM 以外の値または0と SQL_PARAMSET_SIZE (つまり、SQLBindParameter の*columnsize*パラメーター) の数値が含まれている場合、エラーになります。 このエラーが発生すると、SQLPutData は、"文字列長またはバッファー長が正しくありません" というメッセージで SQLSTATE=HY090 の SQL_ERROR を返します。  
  
 テーブル値パラメーターの詳細については、「[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。  
  
## <a name="sqlputdata-support-for-enhanced-date-and-time-features"></a>SQLPutData による機能強化された日付と時刻のサポート  
 日付型または時刻型のパラメーター値は、「 [C から SQL への変換](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)」で説明されているように変換されます。  
  
 詳細については、「[日付と時刻の機能強化 &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。  
  
## <a name="sqlputdata-support-for-large-clr-udts"></a>SQLPutData による大きな CLR UDT のサポート  
 `SQLPutData` は、大きな CLR ユーザー定義型 (UDT) をサポートしています。 詳細については、「[大容量の CLR ユーザー定義型 &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQLPutData 関数](https://go.microsoft.com/fwlink/?LinkId=59365)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  
