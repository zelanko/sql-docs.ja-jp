---
title: 関数をインストールする |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLInstallTranslatorEx
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallTranslatorEx
helpviewer_keywords:
- SQLInstallTranslatorEx function [ODBC]
ms.assetid: a0630602-53c1-4db0-98ce-70d160aedf8d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5cf52c26bf9e4a26f13a27a0e763fbaa30bd18ec
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302093"
---
# <a name="sqlinstalltranslatorex-function"></a>SQLInstallTranslatorEx 関数
**適合 性**  
 バージョン導入: ODBC 3.0  
  
 **まとめ**  
 トランス**レータ**に関する情報をシステム情報の Odbcinst.ini セクションに追加します (HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCINST)。INI\ODBC トランスレータレジストリキー)。  
  
 **SQL インストールトランスレータの**機能には、ODBCCONF を使用してアクセスすることもできます[。EXE](../../../odbc/odbcconf-exe.md).  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
BOOL SQLInstallTranslatorEx(  
     LPCSTR    lpszTranslator,  
     LPCSTR    lpszPathIn,  
     LPSTR     lpszPathOut,  
     WORD      cbPathOutMax,  
     WORD *    pcbPathOut,  
     WORD      fRequest,  
     LPDWORD   lpdwUsageCount);  
```  
  
## <a name="arguments"></a>引数  
 *lpszトランスレータ*  
 [入力]このリストには、変換プログラムを記述するキーワードと値のペアの、二重に NULL で終わるリストが含まれている必要があります。 キーワードと値のペア構文の詳細については、「[変換プログラム仕様サブキー](../../../odbc/reference/install/translator-specification-subkeys.md)」を参照してください。  
  
 **トランスレータ**と**セットアップ**キーワードは *、lpsz トランスレータ*文字列に含める必要があります。 トランス**レータ**キーワードと共に変換 DLL が一覧表示され、トランスレータ セットアップ DLL が**Setup**キーワードと共に一覧表示されます。 各ペアは NULL バイトで終了し、リスト全体が NULL バイトで終了します。 (つまり、2 つの NULL バイトがリストの末尾をマークします。*lpszトランスレータ*の形式は次のとおりです。  
  
 \0トランスレータ=*トランスレータ DLL-ファイル名*\0[セットアップ=*セットアップ DLL-ファイル名*\0]\0  
  
 *を使用します。*  
 [入力]トランスレーターがインストールされる場所の完全パスまたは null ポインター。 *lpszPath*がヌル ポインタの場合、トランスレータはシステム ディレクトリにインストールされます。  
  
 *を使用します。*  
 [出力]トランスレータをインストールするターゲット ディレクトリのパス。 トランスレータがインストールされていない場合は *、lpszPathOut*は*lpszPathIn*と同じです。 トランスレータのインストールが以前に存在する場合 *、lpszPathOut*は以前のインストールのパスです。  
  
 *最大のパス*  
 [入力]の長さ*です。*  
  
 *pcb パスアウト*  
 [出力]*lpszPathOut*で返されるバイト数の合計。 戻されるバイト数が*cbPathOutMax*以上の場合 *、lpszPathOut*の出力パスは *、pcbPathOutMax*から NULL 終了文字を引いた値に切り捨てられます。 *引数 pcbPathOut*は、ヌル・ポインターにすることができます。  
  
 *リクエスト*  
 [入力]要求の種類。 *fRequest には*、次のいずれかの値が含まれている必要があります。  
  
 ODBC_INSTALL_INQUIRY: トランスレータのインストール先を問い合わせ  
  
 ODBC_INSTALL_COMPLETE: インストール要求を完了します。  
  
 *使用法のカウント*  
 [出力]この関数が呼び出された後の変換プログラムの使用回数。  
  
 アプリケーションでは、使用カウントを設定しないでください。 ODBC はこのカウントを維持します。  
  
## <a name="returns"></a>戻り値  
 関数は成功した場合は TRUE を返し、失敗した場合は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 **SQL インストールトランスレータが**FALSE を返すと、SQL**インストーラエラー**を呼び出すことによって、関連付けられた*\*pfErrorCode*値を取得できます。 次の表は **、SQLInstallerError***\** によって返される可能性のある pfErrorCode 値の一覧であり、この関数のコンテキストでそれぞれについて説明します。  
  
|*\*エラーコード*|エラー|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|インストーラの一般的なエラー|特定のインストーラ エラーが発生しなかったエラーが発生しました。|  
|ODBC_ERROR_INVALID_BUFF_LEN|バッファ長が無効です|*引数 lpszPathOut*が出力パスを格納するのに十分な大きさではありませんでした。 バッファーには、切り捨てられたパスが含まれています。<br /><br /> *引数*が 0 で *、fRequest*引数がODBC_INSTALL_COMPLETE。|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|無効な種類の要求|*fRequest*引数は、次の引数の 1 つではありません。<br /><br /> ODBC_INSTALL_INQUIRY ODBC_INSTALL_COMPLETE|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|無効なキーワードと値のペア|*lpsz トランスレータ*引数に構文エラーが含まれていました。|  
|ODBC_ERROR_INVALID_PATH|インストール パスが無効です|*引数に*無効なパスが含まれています。|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|無効なパラメータ シーケンス|*lpszTranslator*引数にキーワード値ペアのリストが含まれていませんでした。|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|レジストリのコンポーネントの使用率カウントを増減できませんでした|インストーラは、トランスレータの使用回数を増やすことができませんでした。|  
  
## <a name="comments"></a>説明  
 **トランスレータのみを**インストールするメカニズムを提供します。 この関数は、実際にはファイルをコピーしません。 呼び出し側プログラムは、変換プログラム・ファイルのコピーを担当します。  
  
 **インストールされているトランスレーター**のコンポーネント使用量カウントを 1 ずつ増やします。 トランスレータのバージョンが既に存在するが、トランスレータのコンポーネント使用カウントが存在しない場合、新しいコンポーネント使用カウント値は 2 に設定されます。  
  
 アプリケーションセットアッププログラムは、トランスレータファイルを物理的にコピーし、ファイルの使用回数を維持する役割を担います。 トランスレータ ファイルがインストールされていない場合、アプリケーションセットアップ プログラムはファイルをコピーし、ファイルの使用回数を作成する必要があります。 ファイルが既にインストールされている場合、セットアップ プログラムはファイルの使用カウントを単純にインクリメントします。  
  
 以前にアプリケーションによって古いバージョンのトランスレータがインストールされている場合は、トランスレータコンポーネントの使用カウントが有効になるように、トランスレータをアンインストールしてから再インストールする必要があります。 **コンポーネントの**使用カウントを減らすために呼び出**す必要があります**。 アプリケーションセットアッププログラムは、古いファイルを新しいファイルで置き換える必要があります。 ファイルの使用数は変わらず、古いバージョンのファイルを使用していた他のアプリケーションは新しいバージョンを使用します。  
  
 **SQLInstallTranslatorEx**の*lpszPathOut*のパスの長さは、2 フェーズのインストール プロセスを可能にするため、アプリケーションは、ODBC_INSTALL_INQUIRY モードの*fRequest*を指定して**SQLInstallTranslatorEx**を呼び出すことによって *、cbPathOutMax*が必要なを決定できます。 これは *、pcbPathOut*バッファーで使用可能なバイトの合計数を返します。 **SQLInstallTranslatorEx**その後、fRequest ODBC_INSTALL_COMPLETE、引数*fRequest**cbPathOut*バッファーの値に NULL 終了文字を加えた値*pcbPathOut*を指定して呼び出すことができます。  
  
 **SQLInstallTranslatorEx**の 2 フェーズ モデルを使用しない場合は、stdlib.h で定義されている値 _MAX_PATHに対して、ターゲット ディレクトリのパスのストレージのサイズを定義する*cbPathOutMax*を Stdlib.h で定義されている値に設定する必要があります。  
  
 *fRequest*がODBC_INSTALL_COMPLETEされると **、SQLInstall トランスレータエクスフェス**は *、lpszPathOut*を NULL (または*cbPathOutMax*を 0 にする) を許可しません。 *fRequest*がODBC_INSTALL_COMPLETE場合、返されるバイト数が*cbPathOutMax*以上の場合に FALSE が返され、切り捨てが発生します。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|デフォルトの翻訳オプションを返す|[コンフィグトランスレータ](../../../odbc/reference/syntax/configtranslator-function.md)|  
|翻訳者の選択|[トランスレータを取得します。](../../../odbc/reference/syntax/sqlgettranslator-function.md)|  
|翻訳者の削除|[トランスレータを削除します。](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|
