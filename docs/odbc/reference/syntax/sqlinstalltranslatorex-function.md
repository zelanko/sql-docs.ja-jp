---
title: SQLInstallTranslatorEx 関数 |Microsoft ドキュメント
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
- SQLInstallTranslatorEx
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallTranslatorEx
helpviewer_keywords:
- SQLInstallTranslatorEx function [ODBC]
ms.assetid: a0630602-53c1-4db0-98ce-70d160aedf8d
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2bf6eda5909aa7cec78a2c23e35126c90f566117
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlinstalltranslatorex-function"></a>SQLInstallTranslatorEx 関数
**準拠**  
 バージョンが導入されています。 ODBC 3.0  
  
 **概要**  
 **SQLInstallTranslatorEx**翻訳者に関する情報、Odbcinst.ini のセクションに追加システム情報 (見つかりました。INI\ODBC トランスレーター レジストリ キー)。  
  
 機能**SQLInstallTranslatorEx**にアクセスすることも[ODBCCONF です。EXE](../../../odbc/odbcconf-exe.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
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
 *lpszTranslator*  
 [入力]二重の null で終わる変換プログラムを記述するキーワード/値ペアの一覧を含むこの必要があります。 キーワードと値のペアの構文の詳細については、次を参照してください。[トランスレーター仕様サブキー](../../../odbc/reference/install/translator-specification-subkeys.md)です。  
  
 **トランスレーター**と**セットアップ**でキーワードを含める必要がある、 *lpszTranslator*文字列。 DLL が記載されている翻訳、**トランスレーター**キーワード、および DLL が記載されている変換プログラムのセットアップ、**セットアップ**キーワード。 各ペアは、NULL バイトで終了し、全体の一覧は、NULL バイトで終了します。 (つまり、2 つの NULL バイトの末尾を示す一覧です。)形式*lpszTranslator*のとおりです。  
  
 \0Translator=*トランスレーター DLL-filename*\0[Setup=*セットアップ DLL-filename*\0]\0  
  
 *lpszPathIn*  
 [入力]変換プログラムがインストールされるか、null ポインターの完全パス。 場合*lpszPath* null ポインターでは、翻訳者は、システムのディレクトリにインストールされます。  
  
 *lpszPathOut*  
 [出力]変換プログラムのインストール先となるターゲット ディレクトリのパス。 場合は、変換プログラムがインストールされていない、 *lpszPathOut*と同じ*lpszPathIn*です。 場合は、このトランスレータの以前のインストールが存在する*lpszPathOut*以前のインストールのパスです。  
  
 *cbPathOutMax*  
 [入力]長さ*lpszPathOut です。*  
  
 *pcbPathOut*  
 [出力]返される使用可能なバイトの合計数*lpszPathOut*です。 場合は、使用できるバイト数を返すより大きいまたは等しい*cbPathOutMax*、出力パス*lpszPathOut*に切り捨てられます*pcbPathOutMax*マイナス、null 終端文字です。 *PcbPathOut*引数が null ポインターを指定できます。  
  
 *起こり*  
 [入力]要求の種類。 *起こり*値は次のいずれかを含める必要があります。  
  
 ODBC_INSTALL_INQUIRY: を調査、変換プログラムをインストールできます。  
  
 ODBC_INSTALL_COMPLETE: は、インストール要求を完了します。  
  
 *lpdwUsageCount*  
 [出力]この関数が呼び出された後、変換プログラムの使用率カウントします。  
  
 アプリケーションでは、使用率カウントは設定しないでください。 ODBC では、この数が維持されます。  
  
## <a name="returns"></a>返します。  
 関数は、それが成功した場合、FALSE が失敗した場合に TRUE を返します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLInstallTranslatorEx**は FALSE を返します、関連付けられている *\*pfErrorCode*を呼び出して値を取得する**SQLInstallerError**です。 次の表、  *\*pfErrorCode*によって返される値**SQLInstallerError**とコンテキストでこの関数のいずれかを説明します。  
  
|*\*pfErrorCode*|[エラー]|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|一般的なインストーラーのエラー|エラーが発生する特定のインストーラーのエラーがなかった。|  
|ODBC_ERROR_INVALID_BUFF_LEN|無効なバッファーの長さ|*LpszPathOut*引数が出力パスを格納するのに十分な大きさがありません。 バッファーには、切り捨てられたパスが含まれています。<br /><br /> *CbPathOutMax*引数が 0 の場合、*起こり*引数が ODBC_INSTALL_COMPLETE です。|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|無効な要求の種類|*起こり*引数が、次のいずれか。<br /><br /> ODBC_INSTALL_INQUIRY ODBC_INSTALL_COMPLETE|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|無効なキーワードと値のペア|*LpszTranslator*引数に構文エラーが含まれています。|  
|ODBC_ERROR_INVALID_PATH|無効なインストール パス|*LpszPathIn*引数に無効なパスが含まれています。|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|無効なパラメーターのシーケンス|*LpszTranslator*引数には、キーワードと値のペアの一覧が含まれていませんでした。|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|インクリメントまたはレジストリのコンポーネントの使用率カウントは減少できませんでした。|変換プログラムの使用率カウントをインクリメントするインストーラーが失敗しました。|  
  
## <a name="comments"></a>コメント  
 **SQLInstallTranslatorEx**変換プログラムをインストールするメカニズムを提供します。 この関数は、すべてのファイルを実際にはコピーされません。 呼び出し元のプログラムは、変換プログラム ファイルをコピーします。  
  
 **SQLInstallTranslatorEx**を 1 つインストールされている翻訳ツールのコンポーネントの使用率カウントをインクリメントします。 変換プログラムのバージョンが既に存在する、コンポーネントの使用カウント変換が存在しない場合は、新しいコンポーネントの使用状況カウント値が 2 に設定します。  
  
 アプリケーションのセットアップ プログラムは、物理的に翻訳ファイルをコピーして、ファイルの使用率カウントを維持します。 変換プログラム ファイルが以前インストールされていない場合、アプリケーションのセットアップ プログラム必要がありますファイルまたはファイルをコピーし、ファイルまたはファイルの使用率カウントを作成します。 ファイルが既にインストールされている場合、セットアップ プログラムは単にファイルの使用率カウントをインクリメントします。  
  
 場合は、アプリケーションでは、変換プログラムの古いバージョンがインストールされていた、トランスレーターをアンインストールしてから再インストール、変換プログラム コンポーネントの使用率カウントは無効にできるようにする必要があります。 **SQLRemoveTranslator**コンポーネント使用率カウントをデクリメントするために呼び出す必要があり、 **SQLInstallTranslatorEx**コンポーネントの使用率カウントをインクリメントするために呼び出す必要があります。 アプリケーションのセットアップ プログラムでは、新しいファイルに、古いファイルまたはファイルを置き換える必要があります。 ファイルの使用率カウントは変わりません、および以前のバージョンのファイルを使用する他のアプリケーションの新しいバージョンが使用されます。  
  
 パスの長さ*lpszPathOut*で**SQLInstallTranslatorEx**により、2 フェーズのインストール プロセスでは、どのようなアプリケーションを特定できるように*cbPathOutMax*必要があります呼び出してする**SQLInstallTranslatorEx**で、*起こり*ODBC_INSTALL_INQUIRY モード。 使用できるバイト数の合計数が返されます、 *pcbPathOut*バッファー。 **SQLInstallTranslatorEx**で呼び出すことができますし、*起こり*ODBC_INSTALL_COMPLETE のおよび*cbPathOutMax*引数の値に設定されて、 *pcbPathOut*バッファーと null 終端文字です。  
  
 2 フェーズのモデルを使用しないことを選択するかどうかは**SQLInstallTranslatorEx**、設定する必要があります*cbPathOutMax*、として値 _MAX_PATH に、ターゲット ディレクトリのパスのストレージのサイズを定義します。切り捨てを防ぐために、Stdlib.h で定義されます。  
  
 ときに*起こり*は ODBC_INSTALL_COMPLETE、 **SQLInstallTranslatorEx**許可しない*lpszPathOut* NULL である (または*cbPathOutMax*0 になります)。 場合*起こり*ODBC_INSTALL_COMPLETE は、FALSE が返される、使用できるバイト数を返すはより大きいまたは等しい*cbPathOutMax*結果をその切り捨てが発生しました。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|既定の変換オプションを返す|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|  
|翻訳者を選択します。|[SQLGetTranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|  
|翻訳者を削除します。|[SQLRemoveTranslator](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|
