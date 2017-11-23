---
title: "バインドとデータの転送のテーブル値パラメーターと列の値 |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-table-valued-parameters
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: table-valued parameters (ODBC), binding and data transfer
ms.assetid: 0a2ea462-d613-42b6-870f-c7fa086a6b42
caps.latest.revision: "28"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0c5b8e9036bc51db5c2dddc6ee76c7117a92adb7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="binding-and-data-transfer-of-table-valued-parameters-and-column-values"></a>テーブル値パラメーターおよび列の値のバインドとデータ転送
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  テーブル値パラメーターは、他のパラメーターと同様、サーバーに渡す前にバインドする必要があります。 アプリケーションはテーブル値パラメーターを他のパラメーターがバインドされているのと同様にバインド: SQLBindParameter または SQLSetDescField または SQLSetDescRec と同等の呼び出しを使用しています。 テーブル値パラメーター用のサーバーのデータ型は SQL_SS_TABLE です。 C 型は SQL_C_DEFAULT または SQL_C_BINARY として指定できます。  
  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降では、入力のテーブル値パラメーターのみがサポートされています。 そのため、SQL_DESC_PARAMETER_TYPE に SQL_PARAM_INPUT 以外の値を設定しようとすると、SQLSTATE = HY105 の SQL_ERROR が発生し、"パラメーターの型が無効です。" というメッセージが返されます。  
  
 属性 SQL_CA_SS_COL_HAS_DEFAULT_VALUE を使用すると、テーブル値パラメーターのすべての列に既定値を割り当てることができます。 個々 のテーブル値パラメーター列の値、ただし、割り当てることができません既定値に SQL_DEFAULT_PARAM を使用して*StrLen_or_IndPtr* SQLBindParameter にします。 全体としてテーブル値パラメーターに SQL_DEFAULT_PARAM を使用して、既定値に設定できません*StrLen_or_IndPtr* SQLBindParameter にします。 これらの規則が続かない場合は、SQLExecute または SQLExecDirect と SQL_ERROR が返されます。 Sqlstate 診断レコードが生成されます = 07S01 メッセージ"パラメーターの既定のパラメーターが正しく使用\<p >"ここで、 \<p > クエリ ステートメントにおける TVP の序数します。  
  
 テーブル値パラメーターをバインドしたら、アプリケーションでは、次に、テーブル値パラメーターの各列をバインドする必要があります。 これを行うには、アプリケーションはまず、テーブル値パラメーターの序数に SQL_SOPT_SS_PARAM_FOCUS を設定する SQLSetStmtAttr を呼び出します。 次のルーチンへの呼び出しによって、テーブル値パラメーターの列をバインド: SQLBindParameter、SQLSetDescRec、および SQLSetDescField です。 設定する SQL_SOPT_SS_PARAM_FOCUS 0 復元 SQLBindParameter、SQLSetDescRec、および SQLSetDescField の通常の効果で正規の最上位パラメーターで動作しています。
 
 注: Linux、Mac の ODBC ドライバーの unixODBC 2.3.1 に 2.3.4、SQL_CA_SS_TYPE_NAME 記述子フィールドで SQLSetDescField を通じて TVP 名前を設定するときに、unixODBC 自動的に変換しません ANSI と Unicode の間で正確なに応じて文字列呼び出される関数 (SQLSetDescFieldA/SQLSetDescFieldW)。 これは、常にまたは使用する場合は、SQLBindParameter SQLSetDescFieldW Unicode (utf-16) 文字列で TVP 名を設定する必要があります。
  
 テーブル値パラメーター自体の実際のデータは送受信されませんが、テーブル値パラメーターを構成する各列のデータは送受信されます。 テーブル値パラメーターは擬似列は、SQLBindParameter のパラメーターを使用して次のように他のデータ型とは異なる属性を参照します。  
  
|パラメーター|テーブル値パラメーター以外のパラメーター (列など) に関連する属性|テーブル値パラメーターに関連する属性|  
|---------------|--------------------------------------------------------------------------------|----------------------------------------------------|  
|*InputOutputType*|IPD の SQL_DESC_PARAMETER_TYPE。<br /><br /> テーブル値パラメーターの列の場合、これはテーブル値パラメーター自体の設定と同じである必要があります。|IPD の SQL_DESC_PARAMETER_TYPE。<br /><br /> これは SQL_PARAM_INPUT である必要があります。|  
|*ValueType*|APD の SQL_DESC_TYPE、SQL_DESC_CONCISE_TYPE。|APD の SQL_DESC_TYPE、SQL_DESC_CONCISE_TYPE。<br /><br /> これは SQL_C_DEFAULT または SQL_C_BINARY である必要があります。|  
|*ParameterType*|IPD の SQL_DESC_TYPE、SQL_DESC_CONCISE_TYPE。|IPD の SQL_DESC_TYPE、SQL_DESC_CONCISE_TYPE。<br /><br /> これは SQL_SS_TABLE である必要があります。|  
|*ColumnSize*|IPD の SQL_DESC_LENGTH または SQL_DESC_PRECISION。<br /><br /> 値に依存*ParameterType*です。|SQL_DESC_ARRAY_SIZE<br /><br /> テーブル値パラメーターにフォーカスが設定されている場合は SQL_ATTR_PARAM_SET_SIZE を使用して設定することもできます。<br /><br /> テーブル値パラメーターの場合、これはテーブル値パラメーターの列バッファー内の行数です。|  
|*DecimalDigits*|IPD の SQL_DESC_PRECISION または SQL_DESC_SCALE。|未使用。 これは 0 である必要があります。<br /><br /> このパラメーターはありません、SQLBindParameter は SQLSTATE で戻り値 SQL_ERROR、および診断レコードが生成されます = HY104、「無効な有効桁数または小数点以下桁数」メッセージ。|  
|*ParameterValuePtr*|APD の SQL_DESC_DATA_PTR。|SQL_CA_SS_TYPE_NAME。<br /><br /> これは、ストアド プロシージャの呼び出しでは省略可能で、不要の場合は NULL を指定できます。 プロシージャの呼び出し以外の SQL ステートメントでは、指定する必要があります。<br /><br /> このパラメーターは、可変の行バインドの使用時にアプリケーションがテーブル値パラメーターを特定するための一意の値としても機能します。 詳細については、「テーブル値パラメーターの可変の行バインド」を参照してください。<br /><br /> SQLBindParameter への呼び出しで、テーブル値パラメーターの型名を指定するは、ANSI アプリケーションとしてビルドされているアプリケーションも Unicode 値として指定する必要があります。 パラメーターに使用される値*StrLen_or_IndPtr* SQL_NTS または sizeof (wchar) を掛けた値名の文字列の長さのいずれかにする必要があります。|  
|*BufferLength*|APD の SQL_DESC_OCTET_LENGTH。|テーブル値パラメーターの型名の長さ (バイト単位)。<br /><br /> 型名が NULL 終端の場合は SQL_NTS に、テーブル値パラメーターの型名が不要の場合は 0 になります。|  
|*StrLen_or_IndPtr*|APD の SQL_DESC_OCTET_LENGTH_PTR。|APD の SQL_DESC_OCTET_LENGTH_PTR。<br /><br /> テーブル値パラメーターの場合、これはデータ長ではなく行数です。|  
  
 テーブル値パラメーターでは、固定の行バインドと可変の行バインドという 2 つのデータ転送モードがサポートされています。  
  
## <a name="fixed-table-valued-parameter-row-binding"></a>テーブル値パラメーターの固定の行バインド  
 固定の行バインドの場合、アプリケーションでは、使用可能なすべての入力列の値に対して十分な大きさのバッファー (バッファー配列) を割り当てます。 このアプリケーションによって次の処理が行われます。  
  
1.  SQLBindParameter、SQLSetDescRec、または sqlsetdescfield による呼び出しを使用してすべてのパラメーターをバインドします。  
  
    1.  SQL_DESC_ARRAY_SIZE に各テーブル値パラメーターの転送可能な最大行数を設定します。 これを行う場合は、SQLBindParameter の呼び出しで。  
  
2.  各テーブル値パラメーターの序数に SQL_SOPT_SS_PARAM_FOCUS を設定する SQLSetStmtAttr を呼び出します。  
  
    1.  各テーブル値パラメーターの場合は、SQLBindParameter、SQLSetDescRec、または sqlsetdescfield による呼び出しを使用してテーブル値パラメーターの列をバインドします。  
  
    2.  既定値は、各テーブル値パラメーター列、呼び出し、SQLSetDescField SQL_CA_SS_COL_HAS_DEFAULT_VALUE を 1 に設定します。  
  
3.  SQL_SOPT_SS_PARAM_FOCUS を 0 に設定する SQLSetStmtAttr を呼び出します。 これは、SQLExecute する前に行う必要があります。 または SQLExecDirect が呼び出されます。 そうしないと、SQL_ERROR が返され、"属性値 SQL_SOPT_SS_PARAM_FOCUS が無効です (実行時に 0 である必要があります)" というメッセージを含む、SQLSTATE=HY024 の診断レコードが生成されます。  
  
4.  セット*StrLen_or_IndPtr*場合 SQLExecute、SQLExecDirect の次の呼び出しで転送するテーブル値パラメーターのない行または行の数に SQL_DEFAULT_PARAM を SQL_DESC_OCTET_LENGTH_PTR またはテーブル値パラメーターには、行があります。 *StrLen_or_IndPtr*または SQL_DESC_OCTET_LENGTH_PTR に設定できません SQL_NULL_DATA に、テーブル値パラメーターのテーブル値パラメーターは null を許容できません (ただし、テーブル値パラメーターを構成する列を null 許容にすることがあります)。 無効な値に設定されているこの、SQLExecute、SQLExecDirect または SQL_ERROR を返し sqlstate の診断レコードが生成場合、= HY090 およびメッセージ"無効な文字列長またはバッファー長パラメーターの\<p >"パラメーター番号である場合、します。  
  
5.  SQLExecute または SQLExecDirect を呼び出します。  
  
 場合、テーブル値パラメーター列の値が個別に渡される入力*StrLen_or_IndPtr* SQL_LEN_DATA_AT_EXEC に設定されている (*長さ*) または列の SQL_DATA_AT_EXEC です。 これは、パラメーターの配列を使用するときに値を個別に渡す場合と似ています。 ドライバーが対象となるデータを要求するようにすべての実行時データ パラメーターを持つ SQLParamData 示しませんのどの行の配列アプリケーションは、この注意する必要があります。 アプリケーションでは、ドライバーが値を要求する順序についてどのような想定も行うことができません。  
  
## <a name="variable-table-valued-parameter-row-binding"></a>テーブル値パラメーターの可変の行バインド  
 可変の行バインドの場合、行は実行時にバッチで転送され、アプリケーションは要求時に行をドライバーに渡します。 これは、各パラメーター値の実行時データに似ています。 可変の行バインドでは、アプリケーションによって次の処理が行われます。  
  
1.  前述の「テーブル値パラメーターの固定の行バインド」の手順 1. ～ 3. の説明に従って、パラメーターと、テーブル値パラメーターの列をバインドします。  
  
2.  セット*StrLen_or_IndPtr*または SQL_DATA_AT_EXEC に実行時に渡されるが、テーブル値パラメーターの SQL_DESC_OCTET_LENGTH_PTR。 どちらも設定しない場合、前のセクションで説明したように、パラメーターが処理されます。  
  
3.  SQLExecute または SQLExecDirect を呼び出します。 実行時データ パラメーターとして処理される SQL_PARAM_INPUT パラメーターまたは SQL_PARAM_INPUT_OUTPUT パラメーターが存在する場合は、SQL_NEED_DATA が返されます。 この場合、アプリケーションによって次の処理が行われます。  
  
    -   SQLParamData を呼び出します。 これを返します、 *ParameterValuePtr*実行時データ パラメーターとリターン コード SQL_NEED_DATA の値。 すべてのパラメーターのデータがドライバーに渡されたときに、SQLParamData は SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、または SQL_ERROR を返します。 実行時データ パラメーターの*ParameterValuePtr*、これは、記述子と同じフィールド SQL_DESC_DATA_PTR、値が必要なパラメーターを一意に識別するためのトークンとして見なすことができます。 この "トークン" は、バインド時にアプリケーションからドライバーに渡され、実行時にアプリケーションに返されます。  
  
4.  アプリケーションと SQLPutData を呼び出す、テーブル値パラメーターの行があるない場合は、null のテーブル値パラメーターのテーブル値パラメーター行のデータを送信、 *StrLen_or_Ind*を SQL_DEFAULT_PARAM に設定します。  
  
     NULL 以外の TVP については、アプリケーションによって次の処理が行われます。  
  
    -   セット*Str_Len_or_Ind*を適切な値は、すべてのテーブル値パラメーター列のし、実行時データ パラメーターには、テーブル値パラメーター列のデータ バッファーを設定します。 通常のパラメーターを個別にドライバーに渡すことができるように、テーブル値パラメーターの列の実行時データを使用することができます。  
  
    -   SQLPutData を呼び出して*Str_Len_or_Ind*サーバーに送信される行の数を設定します。 0 から SQL_DESC_ARRAY_SIZE の範囲を超える値と SQL_DEFAULT_PARAM 以外の値はエラーになります。"文字列長またはバッファー長が正しくありません。" というメッセージを含む SQLSTATE HY090 が返されます。 0 は、すべての行が送信済みで、テーブル値パラメーターのデータが存在しないことを示します (この箇条書きの 2 番目の項目参照)。 SQL_DEFAULT_PARAM を使用できるのは、ドライバーがテーブル値パラメーターのデータを最初に要求するときだけです (この箇条書きの 1 番目の項目参照)。  
  
5.  すべての行が送信されると、テーブル値パラメーターに SQLPutData を呼び出し、 *Str_Len_or_Ind*値 0 の場合、手順 3 a. に進みます。  
  
6.  SQLParamData を再度呼び出します。 テーブル値パラメーター列間のすべての実行時データ パラメーターがある場合、値によって識別されます*ValuePtrPtr* SQLParamData によって返されます。 すべての列値が使用できる場合は、SQLParamData が再び返さ、 *ParameterValuePtr*テーブル値パラメーター、およびアプリケーションの値がもう一度開始します。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40; ODBC &#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
