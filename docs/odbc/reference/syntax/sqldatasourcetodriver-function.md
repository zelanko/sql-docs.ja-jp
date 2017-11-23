---
title: "SQLDataSourceToDriver 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLDataSourceToDriver
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLDataSourceToDriver
helpviewer_keywords: SQLDataSourceToDriver function [ODBC]
ms.assetid: 0d87fcac-30a0-4303-ad8f-a5b53f4b428d
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0594551a7bc82eb96208ecb5d8840db0477c4f3a
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqldatasourcetodriver-function"></a>SQLDataSourceToDriver 関数
**SQLDataSourceToDriver** supportstranslations ODBC ドライバー用です。 この関数は、ODBC 対応のアプリケーションでは呼び出されませんアプリケーション要求経由で翻訳**SQLSetConnectAttr**です。 関連付けられたドライバ、 *ConnectionHandle*で指定された**SQLSetConnectAttr**すべてのデータがドライバーに、データ ソースからフローの変換を実行する指定された DLL を呼び出します。 既定トランスレーター DLL は、ODBC の初期化ファイルで指定できます。  
  
## <a name="syntax"></a>構文  
  
```  
  
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
 *fOption*  
 [入力]オプションの値。  
  
 *fSqlType*  
 [入力]SQL データ型です。 この引数に変換する方法をドライバーに指示*rgbValueIn*をアプリケーションで許容される形式にします。 有効な SQL データ型の一覧は、次を参照してください。、 [SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)付録 d: データ型」セクション。  
  
 *rgbValueIn*  
 [入力]変換する値。  
  
 *cbValueIn*  
 [入力]長さ*rgbValueIn*です。  
  
 *rgbValueOut*  
 [出力]変換の結果です。  
  
> [!NOTE]  
>  トランスレーター DLL は null で終了しない値です。  
  
 *cbValueOutMax*  
 [入力]長さ*rgbValueOut*です。  
  
 *pcbValueOut*  
 [出力]\(Null 終了バイトを除く) バイトの合計数で返される使用可能な*rgbValueOut*です。  
  
 文字またはバイナリ データ、これより大きいまたは等しい場合の*cbValueOutMax*、内のデータ*rgbValueOut*に切り捨てられます*cbValueOutMax*バイトです。  
  
 他のすべてのデータ型、値の*cbValueOutMax*は無視されますトランスレーター DLL が想定して、サイズの*rgbValueOut* で指定したSQLデータ型の既定のCデータ型のサイズは、*fSqlType*です。  
  
 *PcbValueOut*引数が null ポインターを指定できます。  
  
 *後*  
 [出力]エラー メッセージの記憶域へのポインター。 これは、変換が失敗しない限り、空の文字列です。  
  
 *cbErrorMsgMax*  
 [入力]長さ*後*です。  
  
 *pcbErrorMsg*  
 [出力]\(Null 終了バイトを除く) バイトの総数へのポインターで返される使用可能な*後*です。 これより大きいまたは等しい場合*cbErrorMsg*、内のデータ*後*に切り捨てられます*cbErrorMsgMax*マイナス、null 終端文字です。 *PcbErrorMsg*引数が null ポインターを指定できます。  
  
## <a name="returns"></a>返します。  
 変換が成功した場合、false の場合、変換に失敗した場合は TRUE。  
  
## <a name="comments"></a>コメント  
 ドライバー呼び出し**SQLDataSourceToDriver**ドライバーにソースのデータから渡す alldata (結果セットのデータ、テーブル名、行数、エラー メッセージ、およびなど) を変換します。 トランスレーター DLL は、データの型と翻訳 DLL の目的に応じて、一部のデータを変換されない可能性があります。たとえば、1 つのコード ページから別の文字データを変換する DLL は、すべての数値とバイナリ データを無視します。  
  
 値*fOption*の値に設定されている*vParam*を呼び出して指定**SQLSetConnectAttr** SQL_ATTR_TRANSLATE_OPTION 属性を持つ。 これを指定した平行移動の DLL に固有の意味を持つ 32 ビット値です。 たとえば、特定の文字セットの変換を指定します。  
  
 同じバッファーが指定されている場合*rgbValueIn*と*rgbValueOut*バッファー内のデータの翻訳は、配置で実行されます。  
  
 *CbValueIn*、 *cbValueOutMax*、および*pcbValueOut*の種類、SDWORD **SQLDataSourceToDriver**必要はありません巨大なポインターをサポートします。  
  
 場合**SQLDataSourceToDriver**変換中に発生したデータの切り捨ては FALSE を返します。 場合*pcbValueOut* (出力バッファーに返される使用可能なバイト数) がより大きい*cbValueOutMax* (出力バッファーの長さ)、切り捨てが発生しました。 ドライバーでは、切り捨てが許容されるかどうかを決定する必要があります。 切り捨てが発生しなかった場合、 **SQLDataSourceToDriver**別のエラーにより FALSE が返されます。 どちらの場合、特定のエラー メッセージが返される*後*です。  
  
 データの翻訳の詳細については、次を参照してください。[翻訳 Dll](../../../odbc/reference/develop-app/translation-dlls.md)です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|データ ソースに送信されるデータを変換します。|[SQLDriverToDataSource](../../../odbc/reference/syntax/sqldrivertodatasource-function.md)|  
|接続属性の設定値を返す|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|接続属性の設定|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
