---
title: SQLBindParameter |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLBindParameter function
ms.assetid: c302c87a-e7f4-4d2b-a0a7-de42210174ac
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cba973be9b4dc2ec0da286b2d01b636f0ca4e2b4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63067818"
---
# <a name="sqlbindparameter"></a>SQLBindParameter
  `SQLBindParameter`を使用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NATIVE Client ODBC ドライバーにデータを提供するときに、データ変換の負担をなくすことができます。これにより、アプリケーションのクライアントコンポーネントとサーバーコンポーネントの両方でパフォーマンスを大幅に向上させることができます。 その他に、概数データ型を挿入または更新するときに有効桁数を失うことが少なくなるという利点もあります。  
  
> [!NOTE]  
>  `char` 型と `wchar` 型のデータを image 型の列に挿入するときは、バイナリ形式に変換後のデータのサイズではなく、渡すデータのサイズを使用します。  
  
 パラメーター配列の配列要素の 1 つで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー エラーが発生しても、残りの配列要素に対しては引き続きステートメントが実行されます。 アプリケーションがこのステートメントのパラメーター状態要素の配列をバインドした場合は、その配列を基にして、エラーが発生したパラメーター行を特定できます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーを使用する場合は、入力パラメーターのバインド時に SQL_PARAM_INPUT を指定します。 OUTPUT キーワードで定義されたストアド プロシージャ パラメーターをバインドするときは、SQL_PARAM_OUTPUT または SQL_PARAM_INPUT_OUTPUT のみを指定してください。  
  
 [SQLRowCount](sqlrowcount.md)は、バインドさ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]れたパラメーター配列の配列要素によってステートメントの実行でエラーが発生した場合に、Native Client ODBC ドライバーと互換性がありません。 また、ODBC ステートメント属性 SQL_ATTR_PARAMS_PROCESSED_PTR は、エラーが発生する前に処理された行数を報告します。 その後、必要に応じてパラメーター状態配列全体をアプリケーションで調査することにより、正常に実行されたステートメント数を検出できます。  
  
## <a name="binding-parameters-for-sql-character-types"></a>SQL 文字型のパラメーターのバインド  
 渡された SQL データ型が文字型の場合、 *Columnsize*は文字数 (バイト数ではない) のサイズになります。 データ文字列の長さが8000を超える場合、 *Columnsize*をに`SQL_SS_LENGTH_UNLIMITED`設定する必要があります。これは、SQL 型のサイズに制限がないことを示します。  
  
 たとえば、SQL データ型が`SQL_WVARCHAR`の場合、 *columnsize*を4000より大きくすることはできません。 実際のデータの長さが4000より大きい場合は、ドライバーによって使用`SQL_SS_LENGTH_UNLIMITED`される`nvarchar(max)`ように*columnsize*をに設定する必要があります。  
  
## <a name="sqlbindparameter-and-table-valued-parameters"></a>SQLBindParameter とテーブル値パラメーター  
 他のパラメーターの型と同様に、テーブル値パラメーターは SQLBindParameter によってバインドされます。  
  
 テーブル値パラメーターがバインドされた後、そのパラメーターの列もバインドされます。 列をバインドするには、 [SQLSetStmtAttr](sqlsetstmtattr.md)を呼び出して、テーブル値パラメーターの序数に SQL_SOPT_SS_PARAM_FOCUS を設定します。 次に、テーブル値パラメーターの各列に対して SQLBindParameter を呼び出します。 最上位パラメーター バインドに戻るには、SQL_SOPT_SS_PARAM_FOCUS に 0 を設定します。  
  
 テーブル値パラメーターの記述子フィールドへのパラメーターのマッピングの詳細については、「[テーブル値パラメーターと列の値のバインドとデータ転送](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)」を参照してください。  
  
 テーブル値パラメーターの詳細については、「[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。  
  
## <a name="sqlbindparameter-support-for-enhanced-date-and-time-features"></a>SQLBindParameter による機能強化された日付と時刻のサポート  
 日付型または時刻型のパラメーター値は、「 [C から SQL への変換](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)」で説明されているように変換されます。 型`time`および`datetimeoffset`型のパラメーターには、 *ValueType*をと`SQL_C_DEFAULT`し`SQL_C_BINARY`て指定するか、`SQL_SS_TIME2_STRUCT`対応`SQL_SS_TIMESTAMPOFFSET_STRUCT`する構造 (および) が使用されている必要があることに注意してください。  
  
 詳細については、「[日付と時刻の機能強化 &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。  
  
## <a name="sqlbindparameter-support-for-large-clr-udts"></a>SQLBindParameter による大きな CLR UDT のサポート  
 `SQLBindParameter` は、大きな CLR ユーザー定義型 (UDT) をサポートしています。 詳細については、「[大容量の CLR ユーザー定義型 &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ODBC API の実装の詳細](odbc-api-implementation-details.md)   
 [SQLBindParameter 関数](https://go.microsoft.com/fwlink/?LinkId=59328)  
  
  
