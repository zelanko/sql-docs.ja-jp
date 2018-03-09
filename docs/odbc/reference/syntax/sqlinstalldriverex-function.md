---
title: "SQLInstallDriverEx 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLInstallDriverEx
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLInstallDriverEx
helpviewer_keywords: SQLInstallDriverEx function [ODBC]
ms.assetid: 1dd74544-f4e9-46e1-9b5f-c11d84fdab4c
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4179bf04131f256c5a37cb01c079035a569a07af
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlinstalldriverex-function"></a>SQLInstallDriverEx 関数
**準拠**  
 バージョンが導入されています。 ODBC 3.0  
  
 **概要**  
 **SQLInstallDriverEx** Odbcinst.ini のエントリに、システム情報、ドライバーに関する情報が追加され、ドライバーを大きく*UsageCount*を 1 つです。 ただし、バージョンのドライバー既に存在する場合ですが、 *UsageCount* 、ドライバーが存在しない、の値、新しい*UsageCount*値が 2 に設定します。  
  
 この関数は、すべてのファイルを実際にはコピーされません。 ドライバーのファイルを正しくターゲット ディレクトリにコピーする呼び出し元のプログラムの役割です。  
  
 機能**SQLInstallDriverEx**にアクセスすることも[ODBCCONF です。EXE](../../../odbc/odbcconf-exe.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
BOOL SQLInstallDriverEx(  
     LPCSTR    lpszDriver,  
     LPCSTR    lpszPathIn,  
     LPSTR     lpszPathOut,  
     WORD      cbPathOutMax,  
     WORD *    pcbPathOut,  
     WORD      fRequest,  
     LPDWORD   lpdwUsageCount);  
```  
  
## <a name="arguments"></a>引数  
 *lpszDriver*  
 [入力]ドライバー説明 (通常は、関連付けられた DBMS の名前)、物理ドライバー名の代わりにユーザーに表示されます。 *LpszDriver*引数は、ドライバーを記述するキーワード/値ペアの双方向の null で終わるリストを含める必要があります。 キーワードと値のペアの詳細については、次を参照してください。[ドライバー仕様サブキー](../../../odbc/reference/install/driver-specification-subkeys.md)です。 二重の null で終わる文字列の詳細については、次を参照してください。 [ConfigDSN 関数](../../../odbc/reference/syntax/configdsn-function.md)です。  
  
 *lpszPathIn*  
 [入力]インストール、または null ポインターの保存先ディレクトリの完全パス。 場合*lpszPathIn* null ポインターでは、システム ディレクトリに、ドライバーがインストールされます。  
  
 *lpszPathOut*  
 [出力]ドライバーのインストール先のターゲット ディレクトリのパス。 ドライバーが既にインストールされていない場合、 *lpszPathOut*と同じである必要があります*lpszPathIn*です。 ドライバーがインストールされていた場合*lpszPathOut*以前のインストール パスです。  
  
 *cbPathOutMax*  
 [入力]長さ*lpszPathOut*です。  
  
 *pcbPathOut*  
 [出力]\(Null 終了文字を除く) バイトの合計数で返される使用可能な*lpszPathOut*です。 場合は、使用できるバイト数を返すより大きいまたは等しい*cbPathOutMax*、出力パス*lpszPathOut*に切り捨てられます*cbPathOutMax*マイナス、null 終端文字です。 *PcbPathOut*引数が null ポインターを指定できます。  
  
 *起こり*  
 [入力]要求の種類。 *起こり*引数は、次の値のいずれかを含める必要があります。  
  
 ODBC_INSTALL_INQUIRY: ドライバーのインストール場所に関する情報を取得します。  
  
 ODBC_INSTALL_COMPLETE: は、インストール要求を完了します。  
  
 *lpdwUsageCount*  
 [出力]この関数が呼び出された後に、ドライバーの使用率カウントします。  
  
 アプリケーションでは、使用率カウントは設定しないでください。 ODBC では、この数が維持されます。  
  
## <a name="returns"></a>戻り値  
 関数は、それが成功した場合、FALSE が失敗した場合に TRUE を返します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLInstallDriverEx**は FALSE を返します、関連付けられている *\*pfErrorCode*を呼び出して値を取得する**SQLInstallerError**です。 次の表、  *\*pfErrorCode*によって返される値**SQLInstallerError**とコンテキストでこの関数のいずれかを説明します。  
  
|*\*pfErrorCode*|[エラー]|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|一般的なインストーラーのエラー|エラーが発生する特定のインストーラーのエラーがなかった。|  
|ODBC_ERROR_INVALID_BUFF_LEN|無効なバッファーの長さ|*LpszPathOut*引数が出力パスを格納するのに十分な大きさがありません。 バッファーには、切り捨てられたパスが含まれています。<br /><br /> *CbPathOutMax*引数が 0、および*起こり*ODBC_INSTALL_COMPLETE がします。|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|無効な要求の種類|*起こり*引数が、次のいずれか。<br /><br /> ODBC_INSTALL_INQUIRY ODBC_INSTALL_COMPLETE|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|無効なキーワードと値のペア|*LpszDriver*引数に構文エラーが含まれています。|  
|ODBC_ERROR_INVALID_PATH|無効なインストール パス|*LpszPathIn*引数に無効なパスが含まれています。|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|ドライバーまたはトランスレーター セットアップ ライブラリを読み込むことができませんでした。|ドライバーのセットアップ ライブラリを読み込むことができませんでした。|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|無効なパラメーターのシーケンス|*LpszDriver*引数には、キーワードと値のペアの一覧が含まれていませんでした。|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|インクリメントまたはコンポーネントの使用率カウントは減少できませんでした。|ドライバーの使用率カウントをインクリメントするインストーラーが失敗しました。|  
  
## <a name="comments"></a>コメント  
 *LpszDriver*引数は、キーワードと値のペアの形式で属性の一覧を示します。 各ペアは、null バイトで終了し、null バイトのリスト全体が終了します。 (つまり、2 つの null バイトの末尾を示す一覧です。)この一覧の形式は次のとおりです。  
  
 *ドライバー desc*  **\\** 0Driver**=***ドライバー DLL-filename*  **\\** 0 [セットアップ**=***セットアップ DLL-filename***\\**0]  
  
 [*ドライバー attr-keyword1***=***value1***\\**0] [*ドライバー attr-keyword2*  **=**  *value2***\\**0]. **\\** 0  
  
 null バイトを \0 がここでと*ドライバー attr-keywordn*ドライバー属性のキーワードです。 キーワードは、指定した順序で表示する必要があります。 たとえば、書式設定されたテキスト ファイル用のドライバーが個別のドライバーとセットアップ Dll いるとし、.txt、.csv の拡張子を持つファイルを使用できます。 *LpszDriver*このドライバーの引数を次のようにすることがあります。  
  
```  
Text\0Driver=TEXT.DLL\0Setup=TXTSETUP.DLL\0FileUsage=1\0  
FileExtns=*.txt,*.csv\0\0  
```  
  
 SQL Server 用のドライバーが別のセットアップ DLL を持たないし、ドライバー属性キーワードはありません。 *LpszDriver*このドライバーの引数を次のようにすることがあります。  
  
```  
SQL Server\0Driver=SQLSRVR.DLL\0\0  
```  
  
 後に**SQLInstallDriverEx**からドライバーに関する情報を取得、 *lpszDriver*引数、Odbcinst.ini エントリの [ODBC Drivers] セクションにドライバーの説明、システムの追加情報です。 ドライバーの説明を持つというセクションを作成し、ドライバ DLL の完全パスとセットアップ DLL を追加します。 最後に、インストールのターゲット ディレクトリのパスを返しますが、これをドライバー ファイルをコピーしません。 呼び出し元のプログラムは、ターゲット ディレクトリにドライバー ファイルをコピー実際にする必要があります。  
  
 **SQLInstallDriverEx**を 1 つインストールされているドライバーのコンポーネントの使用状況カウントをインクリメントします。 ドライバーのバージョンが既に存在する、コンポーネントの使用カウント、ドライバーが存在しない場合は、新しいコンポーネントの使用状況カウント値が 2 に設定します。  
  
 アプリケーションのセットアップ プログラムは、物理的にドライバー ファイルをコピーして、ファイルの使用率カウントを維持します。 ドライバー ファイルが既にインストールされていない場合、アプリケーションのセットアップ プログラムがでファイルをコピーする必要があります、 *lpszPathIn*パスとファイルの使用率カウントを作成します。 セットアップ プログラムがだけでファイルの使用率カウントをインクリメントし、以前のインストールでのパスを返しますファイルが既にインストールされている場合、 *lpszPathOut*引数。  
  
> [!NOTE]  
>  使用状況カウントがコンポーネントと使用状況カウントがファイルの詳細については、次を参照してください。[使用状況カウント](../../../odbc/reference/install/usage-counting.md)です。  
  
 場合は、アプリケーションでは、ドライバー ファイルの古いバージョンがインストールされていた、ドライバーをアンインストールしてから再インストール、ドライバー コンポーネントの使用率カウントは無効にできるようにする必要があります。 **SQLConfigDriver** (で、*起こり*ODBC_REMOVE_DRIVER の) する必要がありますまず呼び出され、し**SQLRemoveDriver**コンポーネントの使用率カウントをデクリメントするために呼び出す必要があります。 **SQLInstallDriverEx**コンポーネントの使用率カウントをインクリメントする、ドライバーを再インストールしと呼ばれる必要があります。 アプリケーションのセットアップ プログラムは、古いファイルを新しいファイルに置き換える必要があります。 ファイルの使用率カウントは変わりません、および古いバージョンのファイルを使用するその他のアプリケーションの新しいバージョンが使用されます。  
  
> [!NOTE]  
>  ドライバーがインストールされていた場合と**SQLInstallDriverEx**関数は TRUE、別のディレクトリにドライバーをインストールすると呼びますが、 *lpszPathOut*ディレクトリにが含まれますドライバーが既にインストールされています。 入力したディレクトリは含まれません、 *lpszDriver*引数。  
  
 パスの長さ*lpszPathOut*で**SQLInstallDriverEx**により、2 フェーズのインストール プロセスでは、どのようなアプリケーションを特定できるように*cbPathOutMax*でする必要があります呼び出す**SQLInstallDriverEx**で、*起こり*ODBC_INSTALL_INQUIRY モード。 使用できるバイト数の合計数が返されます、 *pcbPathOut*バッファー。 **SQLInstallDriverEx**で呼び出すことができますし、*起こり*ODBC_INSTALL_COMPLETE のおよび*cbPathOutMax*引数の値に設定されて、 *pcbPathOut*バッファーと null 終端文字です。  
  
 2 フェーズのモデルを使用しないことを選択するかどうかは**SQLInstallDriverEx**、設定する必要があります*cbPathOutMax*、として値 _MAX_PATH に、ターゲット ディレクトリのパスのストレージのサイズを定義します。切り捨てを防ぐために、Stdlib.h で定義されます。  
  
 ときに*起こり*ODBC_INSTALL_COMPLETE は、 **SQLInstallDriverEx**できない*lpszPathOut* NULL である (または*cbPathOutMax*にする0) です。 場合*起こり*ODBC_INSTALL_COMPLETE は、FALSE が返される、使用できるバイト数を返すはより大きいまたは等しい*cbPathOutMax*結果をその切り捨てが発生しました。  
  
 後に**SQLInstallDriverEx**が呼び出されてアプリケーションのセットアップ プログラムは、必要に応じて、ドライバー ファイルがコピーし、ドライバーのセットアップ DLL を呼び出す必要があります**SQLConfigDriver**の構成を設定する、ドライバーです。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|ドライバー マネージャーのインストール|[SQLInstallDriverManager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|
