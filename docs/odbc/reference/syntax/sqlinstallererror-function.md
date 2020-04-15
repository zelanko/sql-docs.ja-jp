---
title: エラー関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLInstallerError
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallerError
helpviewer_keywords:
- SQLInstallerError [ODBC]
ms.assetid: e6474b79-4d55-458f-81ce-abfafe357f83
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e749237cf87c5054b8273f38531d9336d316e040
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302103"
---
# <a name="sqlinstallererror-function"></a>SQLInstallerError 関数
**適合 性**  
 バージョン導入: ODBC 3.0  
  
 **まとめ**  
 ODBC**インストーラー関数の**エラーまたは状態の情報を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
RETCODE SQLInstallerError(  
     WORD      iError,  
     DWORD *   pfErrorCode,  
     LPSTR     lpszErrorMsg,  
     WORD      cbErrorMsgMax,  
     WORD *    pcbErrorMsg);  
```  
  
## <a name="arguments"></a>引数  
 *エラー*  
 [入力]エラー レコード番号です。 有効な数値は 1 から 8 です。  
  
 *エラーコード*  
 [出力]インストーラのエラー コードです。 (詳細については、「コメント」を参照してください。  
  
 *メッセージ*  
 [出力]エラー メッセージ テキストの記憶域へのポインター。  
  
 *最大メッセージを返します。*  
 [入力]*バッファの*最大長。 これは、SQL_MAX_MESSAGE_LENGTHからヌル終了文字を引いた値以下でなければなりません。  
  
 *最大メッセージを返します。*  
 [入力]*バッファの*最大長。 これは、SQL_MAX_MESSAGE_LENGTHからヌル終了文字を引いた値以下でなければなりません。  
  
 *メッセージ*  
 [出力]*lpszErrorMsg*で戻すために使用できるバイトの総数 (NULL 終端文字を除く) へのポインタ。 戻り値として使用可能なバイト数が*cbErrorMsgMax*以上の場合、*エラー*メッセージ テキストが*cbErrorMsgMax*から null 終端文字バイトを引いた値に切り捨てられます。 引数*は*null ポインターにすることができます。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、またはSQL_ERROR。  
  
## <a name="diagnostics"></a>診断  
 **エラー**値自体をポストしません。 エラー情報を取得できない場合 (その場合は*pfErrorCode*が定義されていない) 場合は、SQL_NO_DATA**を返します**。 通常はSQL_ERRORを返すエラー値に**アクセスできない場合**は **、SQL_ERROR**が返されますが、エラー値はポストされません。 警告文字列 (*lpszErrorMsg*) の長さがわからない場合は *、lpszErrorMsg*を NULL に設定して **、SQLInstallerError**を呼び出すことができます。 次**に、** 警告文字列の長さを*返します*。 エラー メッセージのバッファーが短すぎる**場合は**、SQL_SUCCESS_WITH_INFOが返され **、SQLInstallerError**の正しい*pfErrorCode*値が返されます。  
  
 エラー メッセージで切り捨てが発生したかどうかを調べるには、アプリケーションは *、cbErrorMsgMax*引数の値を *、pcbErrorMsg*引数に書き込まれたメッセージ テキストの実際の長さと比較できます。 切り捨てが発生した場合は、適切なバッファ長を*lpszErrorMsg*に割り当てる必要があり **、SQLInstallerError**は、対応する*iError*レコードを使用して再度呼び出す必要があります。  
  
## <a name="comments"></a>説明  
 アプリケーションは、ODBC インストーラー関数への以前の呼び出しが FALSE を返すときに**SQLInstallerError**を呼び出します。 ODBC インストーラおよびドライバまたはトランスレータのセットアップ関数は、関数が失敗した場合にのみ 0 個以上のエラーをポストします (FALSE を返します)。したがって、アプリケーションは ODBC インストーラー関数が失敗した後にのみ**SQLInstallerError**を呼び出します。  
  
 ODBC インストーラーエラー キューは、新しいインストーラー関数が呼び出されるたびにフラッシュされます。 したがって、アプリケーションは、前回のインストーラー関数呼び出し以外の関数のエラーを取得することはできません。  
  
 関数呼び出しに対して複数のエラーを取得するには、アプリケーションが**SQLInstallerError を**複数回呼び出します。  
  
 追加情報がない場合 **、SQLInstallerError**はSQL_NO_DATAを返し、*引数は*未定義で、*引数は 0*に等しく、引数*lpszErrorMsg*に 1 つの NULL 終了文字が含まれます (*引数が*0 である場合を除く)。
