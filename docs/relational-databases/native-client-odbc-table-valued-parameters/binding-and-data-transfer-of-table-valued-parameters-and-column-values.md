---
title: テーブル値パラメーターのデータ転送
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), binding and data transfer
ms.assetid: 0a2ea462-d613-42b6-870f-c7fa086a6b42
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3b7eecfdac3d42b7a3d8d66ffe1f8ac68652230f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304501"
---
# <a name="binding-and-data-transfer-of-table-valued-parameters-and-column-values"></a>テーブル値パラメーターおよび列の値のバインドとデータ転送
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  テーブル値パラメーターは、他のパラメーターと同様、サーバーに渡す前にバインドする必要があります。 アプリケーションは、SQLBindParameter または SQLSetDescRec への同等の呼び出しを使用して、他のパラメーターをバインドするのと同じ方法でテーブル値パラメーターをバインドします。 テーブル値パラメーター用のサーバーのデータ型は SQL_SS_TABLE です。 C 型は SQL_C_DEFAULT または SQL_C_BINARY として指定できます。  
  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降では、入力のテーブル値パラメーターのみがサポートされています。 そのため、SQL_DESC_PARAMETER_TYPE に SQL_PARAM_INPUT 以外の値を設定しようとすると、SQLSTATE = HY105 の SQL_ERROR が発生し、"パラメーターの型が無効です。" というメッセージが返されます。  
  
 属性 SQL_CA_SS_COL_HAS_DEFAULT_VALUE を使用すると、テーブル値パラメーターのすべての列に既定値を割り当てることができます。 ただし、SQLBindParameter を使用して*StrLen_or_IndPtr*でSQL_DEFAULT_PARAMを使用して、個々のテーブル値パラメーター列の値に既定値を割り当てることはできません。 テーブル値パラメーター全体を SQLBindParameter で*StrLen_or_IndPtr*でSQL_DEFAULT_PARAMを使用して、既定値に設定することはできません。 これらの規則に従わない場合は、SQL 実行または SQLExecDirect がSQL_ERRORを返します。 診断レコードは SQLSTATE=07S01 で生成され、"p>はクエリステートメントの中\<での tvP\<の序数である「 パラメーター p>のデフォルト・パラメーターの無効な使用」というメッセージが出されます。  
  
 テーブル値パラメーターをバインドしたら、アプリケーションでは、次に、テーブル値パラメーターの各列をバインドする必要があります。 これを行うには、アプリケーションはまず SQLSetStmtAttr を呼び出して、テーブル値パラメーターの序数にSQL_SOPT_SS_PARAM_FOCUSを設定します。 次に、アプリケーションは、次のルーチンを呼び出すことによって、テーブル値パラメーターの列をバインドします。 SQL_SOPT_SS_PARAM_FOCUSを 0 に設定すると、通常のトップレベル パラメーターで動作する場合の、SQLBindParameter、SQLSetDescRec、および SQLSetDescField の通常の効果が復元されます。
 
 注: unixODBC 2.3.1 から 2.3.4 の Linux および Mac ODBC ドライバーの場合、SQL_CA_SS_TYPE_NAME記述子フィールドを使用して SQLSetDescField を使用して TVP 名を設定する場合、unixODBC は、呼び出される正確な関数 (SQLSetDescFieldA / SQLSetDescFieldW) に応じて、ANSI と Unicode 文字列の間で自動的に変換されません。 TVP 名を設定するには、常に SQLBindParameter または SQLSetDescFieldW を Unicode (UTF-16) 文字列と共に使用する必要があります。
  
 テーブル値パラメーター自体の実際のデータは送受信されませんが、テーブル値パラメーターを構成する各列のデータは送受信されます。 テーブル値パラメーターは疑似列であるため、SQLBindParameter のパラメーターは、次のように、他のデータ型とは異なる属性を参照するために使用されます。  
  
|パラメーター|テーブル値以外のパラメーター型 (列を含む) の関連する属性|テーブル値パラメーターに関連する属性|  
|---------------|--------------------------------------------------------------------------------|----------------------------------------------------|  
|*InputOutputType*|IPD の SQL_DESC_PARAMETER_TYPE。<br /><br /> テーブル値パラメーターの列の場合、これはテーブル値パラメーター自体の設定と同じである必要があります。|IPD の SQL_DESC_PARAMETER_TYPE。<br /><br /> これは SQL_PARAM_INPUT である必要があります。|  
|*Valuetype*|APD の SQL_DESC_TYPE、SQL_DESC_CONCISE_TYPE。|APD の SQL_DESC_TYPE、SQL_DESC_CONCISE_TYPE。<br /><br /> これは SQL_C_DEFAULT または SQL_C_BINARY である必要があります。|  
|*パラメータータイプ*|IPD の SQL_DESC_TYPE、SQL_DESC_CONCISE_TYPE。|IPD の SQL_DESC_TYPE、SQL_DESC_CONCISE_TYPE。<br /><br /> これは SQL_SS_TABLE である必要があります。|  
|*ColumnSize*|IPD の SQL_DESC_LENGTH または SQL_DESC_PRECISION。<br /><br /> これは *、パラメーターの種類*の値によって異なります。|SQL_DESC_ARRAY_SIZE<br /><br /> テーブル値パラメーターにフォーカスが設定されている場合は SQL_ATTR_PARAM_SET_SIZE を使用して設定することもできます。<br /><br /> テーブル値パラメーターの場合、これはテーブル値パラメーターの列バッファー内の行数です。|  
|*DecimalDigits*|IPD の SQL_DESC_PRECISION または SQL_DESC_SCALE。|未使用。 これは 0 である必要があります。<br /><br /> このパラメーターが 0 でない場合、SQLBindParameter は SQL_ERRORを戻し、SQLSTATE= HY104 とメッセージ 「有効桁数または小数点以下桁数が無効です」で診断レコードが生成されます。|  
|*パラメーター値Ptr*|APD の SQL_DESC_DATA_PTR。|SQL_CA_SS_TYPE_NAME。<br /><br /> これは、ストアド プロシージャの呼び出しでは省略可能で、不要の場合は NULL を指定できます。 プロシージャの呼び出し以外の SQL ステートメントでは、指定する必要があります。<br /><br /> このパラメーターは、可変の行バインドの使用時にアプリケーションがテーブル値パラメーターを特定するための一意の値としても機能します。 詳細については、「テーブル値パラメーターの可変の行バインド」を参照してください。<br /><br /> SQLBindParameter の呼び出しでテーブル値パラメーターの型名を指定する場合は、ANSI アプリケーションとして構築されたアプリケーションであっても、その名前を Unicode 値として指定する必要があります。 パラメーター *StrLen_or_IndPtr*に使用する値は、SQL_NTSまたは名前の文字列の長さに sizeof(WCHAR) を掛けた値でなければなりません。|  
|*BufferLength*|APD の SQL_DESC_OCTET_LENGTH。|テーブル値パラメーターの型名の長さ (バイト単位)。<br /><br /> 型名が NULL 終端の場合は SQL_NTS に、テーブル値パラメーターの型名が不要の場合は 0 になります。|  
|*StrLen_or_IndPtr*|APD の SQL_DESC_OCTET_LENGTH_PTR。|APD の SQL_DESC_OCTET_LENGTH_PTR。<br /><br /> テーブル値パラメーターの場合、これはデータ長ではなく行数です。|  
||||

 テーブル値パラメーターでは、固定の行バインドと可変の行バインドという 2 つのデータ転送モードがサポートされています。  
  
## <a name="fixed-table-valued-parameter-row-binding"></a>テーブル値パラメーターの固定の行バインド  
 固定の行バインドの場合、アプリケーションでは、使用可能なすべての入力列の値に対して十分な大きさのバッファー (バッファー配列) を割り当てます。 このアプリケーションによって次の処理が行われます。  
  
1.  呼び出しを使用して、すべてのパラメーターをバインドします。  
  
    1.  SQL_DESC_ARRAY_SIZE に各テーブル値パラメーターの転送可能な最大行数を設定します。 これは、SQLBindParameter 呼び出しで行うことができます。  
  
2.  各テーブル値パラメーターの序数にSQL_SOPT_SS_PARAM_FOCUSを設定するために SQLSetStmtAttr を呼び出します。  
  
    1.  テーブル値パラメーターごとに、テーブル値パラメーター列をバインドするには、SQLBindParameter、SQLSetDescRec、または SQLSetDescField 呼び出しを使用します。  
  
    2.  デフォルト値を持つテーブル値パラメーター列ごとに、SQLSetDescField を呼び出して SQL_CA_SS_COL_HAS_DEFAULT_VALUE 1 に設定します。  
  
3.  SQL_SOPT_SS_PARAM_FOCUSを 0 に設定するために、SQLSetStmtAttr を呼び出します。 これは、SQL 実行または SQLExecDirect が呼び出される前に行う必要があります。 そうしないと、SQL_ERROR が返され、"属性値 SQL_SOPT_SS_PARAM_FOCUS が無効です (実行時に 0 である必要があります)" というメッセージを含む、SQLSTATE=HY024 の診断レコードが生成されます。  
  
4.  行のないテーブル値パラメーターにSQL_DEFAULT_PARAMStrLen_or_IndPtr*またはSQL_DESC_OCTET_LENGTH_PTR*を設定するか、テーブル値パラメーターに行がある場合は SQLExecute または SQLExecDirect の次の呼び出しで転送される行の数を設定します。 *テーブル*値パラメーターは null 許容ではないため、テーブル値パラメーターのStrLen_or_IndPtrまたはSQL_DESC_OCTET_LENGTH_PTRをSQL_NULL_DATAに設定することはできません (ただし、テーブル値パラメーターの構成要素列は null 許容である可能性があります)。 この値が無効な値に設定されている場合、SQLExecute または SQLExecDirect はSQL_ERRORを戻し、SQLSTATE=HY090 とメッセージ "パラメーター \<p>の文字列またはバッファー長が無効です" というメッセージを使用して診断レコードが生成されます。  
  
5.  を呼び出します。  
  
 StrLen_or_IndPtrが列の SQL_LEN_DATA_AT_EXEC(*length*) またはSQL_DATA_AT_EXECに*設定されている場合*、入力テーブル値パラメーター列の値を複数の値で渡すことができます。 これは、パラメーターの配列を使用するときに値を個別に渡す場合と似ています。 すべての実行時データ パラメーターと同様に、SQLParamData は、ドライバーがデータを要求している配列の行を示すものではありません。アプリケーションは、この問題を考慮する必要があります。 アプリケーションでは、ドライバーが値を要求する順序についてどのような想定も行うことができません。  
  
## <a name="variable-table-valued-parameter-row-binding"></a>テーブル値パラメーターの可変の行バインド  
 可変の行バインドの場合、行は実行時にバッチで転送され、アプリケーションは要求時に行をドライバーに渡します。 これは、各パラメーター値の実行時データに似ています。 可変の行バインドでは、アプリケーションによって次の処理が行われます。  
  
1.  前述の「テーブル値パラメーターの固定の行バインド」の手順 1. ～ 3. の説明に従って、パラメーターと、テーブル値パラメーターの列をバインドします。  
  
2.  SQL_DATA_AT_EXECに、実行時に渡されるテーブル値パラメーターの*StrLen_or_IndPtr*またはSQL_DESC_OCTET_LENGTH_PTRを設定します。 どちらも設定しない場合、前のセクションで説明したように、パラメーターが処理されます。  
  
3.  を呼び出します。 実行時データ パラメーターとして処理される SQL_PARAM_INPUT パラメーターまたは SQL_PARAM_INPUT_OUTPUT パラメーターが存在する場合は、SQL_NEED_DATA が返されます。 この場合、アプリケーションによって次の処理が行われます。  
  
    -   を呼び出します。 これにより、実行時データ パラメーターの*ParameterValuePtr*値と SQL_NEED_DATA の戻りコードが返されます。 すべてのパラメーター データがドライバーに渡されると、SQLParamData はSQL_SUCCESS、SQL_SUCCESS_WITH_INFO、またはSQL_ERRORを返します。 実行時データパラメータの場合、記述子フィールドSQL_DESC_DATA_PTRと同じ*ParameterValuePtr*は、値が必要なパラメータを一意に識別するトークンと見なすことができます。 この "トークン" は、バインド時にアプリケーションからドライバーに渡され、実行時にアプリケーションに返されます。  
  
4.  NULL テーブル値パラメーターのテーブル値パラメーターの行データを送信するには、テーブル値パラメーターに行がない場合、アプリケーションは StrLen_or_IndをSQL_DEFAULT_PARAM*に設定して*SQLPutData を呼び出します。  
  
     NULL 以外の TVP については、アプリケーションによって次の処理が行われます。  
  
    -   すべてのテーブル値パラメーター列*のStr_Len_or_Ind*を適切な値に設定し、実行時のデータ パラメーターではないテーブル値パラメーター列のデータ バッファーを設定します。 通常のパラメーターを個別にドライバーに渡すことができるように、テーブル値パラメーターの列の実行時データを使用することができます。  
  
    -   サーバーに送信する行数*Str_Len_or_Ind*設定された SQLPutData を呼び出します。 0 から SQL_DESC_ARRAY_SIZE の範囲を超える値と SQL_DEFAULT_PARAM 以外の値はエラーになります。"文字列長またはバッファー長が正しくありません。" というメッセージを含む SQLSTATE HY090 が返されます。 0 は、すべての行が送信済みで、テーブル値パラメーターのデータが存在しないことを示します (この箇条書きの 2 番目の項目参照)。 SQL_DEFAULT_PARAM を使用できるのは、ドライバーがテーブル値パラメーターのデータを最初に要求するときだけです (この箇条書きの 1 番目の項目参照)。  
  
5.  すべての行が送信されると、テーブル値パラメーターの SQLPutData を呼び出し *、Str_Len_or_Ind*値 0 を指定して、上記の手順 3a に進みます。  
  
6.  再び SQL パラムデータを呼び出します。 テーブル値パラメーター列の中に実行時のデータ パラメーターがある場合、これらは SQLParamData によって返される*ValuePtrPtr 値*によって識別されます。 すべての列値が使用可能な場合、SQLParamData はテーブル値パラメーターの*ParameterValuePtr*値を再び返し、アプリケーションが再び開始されます。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;テーブル値パラメーター](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
