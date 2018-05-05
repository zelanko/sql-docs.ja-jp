---
title: SQLInstallerError 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
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
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c76d89a69ade4aca9c915db8d960cc749f8ca2a7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlinstallererror-function"></a>SQLInstallerError 関数
**準拠**  
 バージョンが導入されています。 ODBC 3.0  
  
 **概要**  
 **SQLInstallerError** ODBC インストーラーの関数のエラー状態や状態の情報を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE SQLInstallerError(  
     WORD      iError,  
     DWORD *   pfErrorCode,  
     LPSTR     lpszErrorMsg,  
     WORD      cbErrorMsgMax,  
     WORD *    pcbErrorMsg);  
```  
  
## <a name="arguments"></a>引数  
 *i エラー*  
 [入力]エラー レコードの数です。 有効な番号は 1 ~ 8 です。  
  
 *pfErrorCode*  
 [出力]インストーラーのエラー コード。 (詳細については、「コメント」を参照してください)  
  
 *lpszErrorMsg*  
 [出力]エラー メッセージのテキストの記憶域へのポインター。  
  
 *cbErrorMsgMax*  
 [入力]最大長、*後*バッファー。 以下 SQL_MAX_MESSAGE_LENGTH をマイナスした null 終端文字があります。  
  
 *cbErrorMsgMax*  
 [入力]最大長、*後*バッファー。 以下 SQL_MAX_MESSAGE_LENGTH をマイナスした null 終端文字があります。  
  
 *pcbErrorMsg*  
 [出力]\(Null 終了文字を除く) バイトの総数へのポインターで返される使用可能な*lpszErrorMsg*です。 場合は、使用できるバイト数を返すより大きいまたは等しい*cbErrorMsgMax*、エラー メッセージ テキスト*lpszErrorMsg*に切り捨てられます*cbErrorMsgMax*マイナス、null 終端文字のバイト数です。 *PcbErrorMsg*引数が null ポインターを指定できます。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、または SQL_ERROR です。  
  
## <a name="diagnostics"></a>診断  
 **SQLInstallerError**自体のエラー値が通知されません。 **SQLInstallerError** SQL_NO_DATA が返されますが、エラー情報を取得できない場合 (後者*pfErrorCode*が定義されていません)。 場合**SQLInstallerError** SQL_ERROR を返します通常何らかの理由でエラーの値にアクセスできません**SQLInstallerError** SQL_ERROR を返しますが、エラー値が通知されません。 警告文字列の長さがわからないかどうかは (*lpszErrorMsg*) を設定することができます*lpszErrorMsg*を NULL に、呼び出し**SQLInstallerError**です。 **SQLInstallerError**で警告文字列の長さを戻り値には*cbErrorMsgMax*です。 エラー メッセージのバッファーが短すぎる場合**SQLInstallerError** SQL_SUCCESS_WITH_INFO が返され、正しい*pfErrorCode*値**SQLInstallerError**.  
  
 アプリケーションがの値の比較時に、エラー メッセージに切り捨てが発生したかどうかを判断するのには*cbErrorMsgMax*に書き込まれたメッセージのテキストの実際の長さへの引数、 *pcbErrorMsg*引数。 適切なバッファーの長さを割り当てる必要がある場合は切り捨てが発生すると*lpszErrorMsg*と**SQLInstallerError** 、対応すると共に、もう一度呼び出されなければなりません*iError*レコード。  
  
## <a name="comments"></a>コメント  
 アプリケーションが呼び出す**SQLInstallerError** ODBC インストーラー関数を前回呼び出したときに FALSE が返されるときにします。 ODBC インストーラーとドライバーまたはトランスレーター セットアップの機能が、関数が失敗した場合にのみ、0 個以上のエラーを投稿 (FALSE を返します)。そのため、アプリケーションが呼び出す**SQLInstallerError** ODBC インストーラー関数が失敗した後のみです。  
  
 ODBC インストーラーのエラーのキューは、新しいインストーラー関数が呼び出されるたびにフラッシュされます。 そのため、アプリケーションは、インストーラーの最後の関数呼び出しからエラー以外の関数を取得することはできません。  
  
 アプリケーションが呼び出す関数の呼び出しを複数のエラーを取得する**SQLInstallerError**複数回です。  
  
 詳細についてがない場合に**SQLInstallerError** 、SQL_NO_DATA が返される、 *pfErrorCode*引数が定義されていない、 *pcbErrorMsg*引数が 0 に等しいと*lpszErrorMsg*引数には、1 つの null 終了文字が含まれています (しない限り、 *cbErrorMsgMax*引数が 0 に等しい)。
