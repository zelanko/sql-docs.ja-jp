---
title: SQLPutData |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLPutData function
ms.assetid: d39aaa5b-7fbc-4315-a7f2-5a7787e04f25
caps.latest.revision: 49
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a15cf608a3c95cee345f4e7d3b4ba6c6690e0a19
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2018
ms.locfileid: "35697525"
---
# <a name="sqlputdata"></a>SQLPutData
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  SQLPutData を使用して、65,535 バイトを超えるデータを送信するときに、次の制限が適用されます (の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]4.21) または 400 に KB のデータ (SQL Server バージョン 6.0 以降) を SQL_LONGVARCHAR (**テキスト**)、SQL_WLONGVARCHAR(**ntext**) または SQL_LONGVARBINARY (**イメージ**) 列。  
  
-   参照先のパラメーターを指定できます、 *insert_value* INSERT ステートメントでします。  
  
-   参照先のパラメーターを指定できます、*式*UPDATE ステートメントの SET 句でします。  
  
 実行するサーバーのブロックでデータを提供する SQLPutData 呼び出しのシーケンスを取り消す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]6.5 以前のバージョンを使用する場合は、列の値を部分的に更新を発生します。 **テキスト**、 **ntext**、または**イメージ**SQLCancel が呼び出されたときに参照された列は、中間のプレース ホルダーの値に設定します。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 以前のバージョンへの接続をサポートしません。  
  
## <a name="diagnostics"></a>診断  
 1 つを使用する必要がある[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client 固有の SQLSTATE SQLPutData:  
  
|SQLSTATE|[エラー]|説明|  
|--------------|-----------|-----------------|  
|22026|文字列データの長さが合致しません|送信するバイトのデータの長さが指定されている場合、アプリケーションによってなどを SQL_LEN_DATA_AT_EXEC で (*n*)、 *n*経由でアプリケーションによって指定されたバイトの合計数、0 より大きいSQLPutData は、指定した長さと一致する必要があります。|  
  
## <a name="sqlputdata-and-table-valued-parameters"></a>SQLPutData とテーブル値パラメーター  
 テーブル値パラメーターを可変の行バインドを使用すると、SQLPutData はアプリケーションによって使用されます。 *StrLen_Or_Ind*パラメーターは、次の行またはテーブル値パラメーターのデータの行のデータを収集するドライバーの準備ができて、こと、またはそれ以上の行が使用できることを示します。  
  
-   値が 0 を超える場合は、次の行の値のセットを使用できることを示します。  
  
-   値が 0 の場合は、送信される行がなくなったことを示します。  
  
-   値が 0 未満の場合は、エラーが発生し、"文字列長またはバッファー長が正しくありません" というメッセージで SQLState HY090 の診断レコードが記録されます。  
  
 *DataPtr*パラメーターは無視されますが、NULL 以外の値に設定する必要があります。 詳細については、変数の TVP 行でのバインディング セクションを参照してください。[バインドおよび Data Transfer of Table-Valued パラメーターと列の値](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)です。  
  
 場合*StrLen_Or_Ind* SQL_DEFAULT_PARAM または 0 から SQL_PARAMSET_SIZE までの数値以外の値を持つ (つまり、 *ColumnSize* SQLBindParameter のパラメーター) はエラーです。 このエラーが発生すると、SQLPutData は、"文字列長またはバッファー長が正しくありません" というメッセージで SQLSTATE=HY090 の SQL_ERROR を返します。  
  
 テーブル値パラメーターの詳細については、次を参照してください。[テーブル値パラメーター &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)です。  
  
## <a name="sqlputdata-support-for-enhanced-date-and-time-features"></a>SQLPutData による機能強化された日付と時刻のサポート  
 」の説明に従って、日付/時刻型のパラメーターの値は変換は[C から SQL への変換](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)です。  
  
 詳細については、次を参照してください。[日付と時刻の強化&#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)です。  
  
## <a name="sqlputdata-support-for-large-clr-udts"></a>SQLPutData による大きな CLR UDT のサポート  
 **SQLPutData**大きなの CLR ユーザー定義型 (Udt) をサポートしています。 詳細については、次を参照してください。 [Large CLR User-Defined 型&#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLPutData 関数](http://go.microsoft.com/fwlink/?LinkId=59365)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
