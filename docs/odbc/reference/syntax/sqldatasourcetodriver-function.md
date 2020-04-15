---
title: 関数を使用する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDataSourceToDriver
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDataSourceToDriver
helpviewer_keywords:
- SQLDataSourceToDriver function [ODBC]
ms.assetid: 0d87fcac-30a0-4303-ad8f-a5b53f4b428d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 92df58b76a9a11d0d4ab9821756bff014ecae29a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301192"
---
# <a name="sqldatasourcetodriver-function"></a>SQLDataSourceToDriver 関数
**ODBC ドライバー**の変換をサポートしています。 この関数は、ODBC 対応アプリケーションからは呼び出されません。アプリケーションは **、SQLSetConnectAttr**を介して翻訳を要求します。 **SQLSetConnectAttr**で指定された*接続ハンドル*に関連付けられているドライバーは、データ ソースからドライバーに流れるすべてのデータの変換を実行するために指定された DLL を呼び出します。 デフォルトの変換 DLL は、ODBC 初期化ファイルで指定できます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
BOOL SQLDataSourceToDriver(  
     UDWORD     fOption,  
     SWORD      fSqlType,  
     PTR        rgbValueIn,  
     SDWORD     cbValueIn,  
     PTR        rgbValueOut,  
     SDWORD     cbValueOutMax,  
     SDWORD *   pcbValueOut,  
     UCHAR *    szErrorMsg,  
     SWORD      cbErrorMsgMax,  
     SWORD *    pcbErrorMsg);  
```  
  
## <a name="arguments"></a>引数  
 *オプション*  
 [入力]オプション値。  
  
 *を使用します。*  
 [入力]SQL データ型。 この引数は、*ドライバーに、rgbValueIn*をアプリケーションで許容できる形式に変換する方法を指示します。 有効な SQL データ型の一覧については、「付録 D:[データ型」の「SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)」セクションを参照してください。  
  
 *値下げイン*  
 [入力]翻訳する値。  
  
 *を使用する*  
 [入力]*の*長さ。  
  
 *値を設定します。*  
 [出力]翻訳の結果。  
  
> [!NOTE]  
>  変換 DLL では、この値は null で終わるわけではありません。  
  
 *最大値を設定します。*  
 [入力]*の*長さ。  
  
 *pcb 値を引き出す*  
 [出力]*rgbValueOut*で返されるバイト数 (null 終了バイトを除く) の総数。  
  
 文字データまたはバイナリ データの場合、これが*cbValueOutMax*以上の場合 *、rgbValueOut*のデータは*cbValueOutMax*バイトに切り捨てられます。  
  
 その他のすべてのデータ型の場合 *、cbValueOutMax*の値は無視され、変換 DLL は *、fSqlType*で指定された SQL データ型の既定の C データ型のサイズであると仮定*します*。  
  
 *引数は*null ポインターにすることができます。  
  
 *メッセージ*  
 [出力]エラー メッセージの記憶域へのポインター。 変換に失敗しない限り、これは空の文字列です。  
  
 *最大メッセージを返します。*  
 [入力]の長*さ。*  
  
 *メッセージ*  
 [出力]*szErrorMsg*で返されるバイトの総数 (null 終了バイトを除く) へのポインタ。 これが*cbErrorMsg*より大きいか等しい場合 *、szErrorMsg*のデータは *、cbErrorMsgMax*から NULL 終了文字を引いた値に切り捨てられます。 引数*は*null ポインターにすることができます。  
  
## <a name="returns"></a>戻り値  
 TRUE は、変換が成功した場合は FALSE、変換が失敗した場合は FALSE。  
  
## <a name="comments"></a>説明  
 ドライバーは、すべてのデータ (結果セット データ、テーブル名、行数、エラー メッセージなど) を変換する**SQLDataSourceToDriver**を呼び出し、データ ソースからドライバーに渡します。 変換 DLL は、データの種類と変換 DLL の目的によっては、一部のデータを変換しない場合があります。たとえば、あるコード ページから別のコード ページに文字データを変換する DLL では、すべての数値データとバイナリ データが無視されます。  
  
 *fOption*の値は、SQL_ATTR_TRANSLATE_OPTION属性を指定して**SQLSetConnectAttr**を呼び出すことによって指定された*vParam*の値に設定されます。 これは、特定の翻訳 DLL に対して特定の意味を持つ 32 ビット値です。 たとえば、特定の文字セットの変換を指定できます。  
  
 同じバッファーが*rgbValueIn*と*rgbValueOut*に指定されている場合、バッファー内のデータの変換は所定の位置で実行されます。  
  
 *cbValueIn* *、cbValueOutMax*、および*pcbValueOut*はタイプが SDWORD ですが **、SQLDataSourceToDriver**は必ずしも巨大なポインターをサポートするとは限りません。  
  
 **FALSE を返す**場合、変換中にデータの切り捨てが発生した可能性があります。 *pcbValueOut* (出力バッファーに戻すために使用可能なバイト数) が*cbValueOutMax* (出力バッファーの長さ) より大きい場合、切り捨てが発生しました。 ドライバーは、切り捨てが許容されたかどうかを判断する必要があります。 切り捨てが発生しなかった場合は、**別のエラー**が原因で FALSE を返しました。 どちらの場合も *、szErrorMsg*に特定のエラー メッセージが返されます。  
  
 データの変換の詳細については、「変換[DLL 」を](../../../odbc/reference/develop-app/translation-dlls.md)参照してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|データ ソースに送信されるデータの変換|[データ ソース](../../../odbc/reference/syntax/sqldrivertodatasource-function.md)|  
|接続属性の設定を返す|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|接続属性の設定|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
