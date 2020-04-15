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
- SQLInstallDriverEx
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallDriverEx
helpviewer_keywords:
- SQLInstallDriverEx function [ODBC]
ms.assetid: 1dd74544-f4e9-46e1-9b5f-c11d84fdab4c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 054e8b6b9eae26bd5f973f3d46d7ef37363a8e79
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302124"
---
# <a name="sqlinstalldriverex-function"></a>SQLInstallDriverEx 関数
**適合 性**  
 バージョン導入: ODBC 3.0  
  
 **まとめ**  
 **SQLInstallDriverEx**は、システム情報の Odbcinst.ini エントリにドライバーに関する情報を追加し、ドライバーの*使用カウント*を 1 ずつインクリメントします。 ただし、ドライバーのバージョンが既に存在するが *、ドライバーの UsageCount*値が存在しない場合は、新しい*UsageCount*値は 2 に設定されます。  
  
 この関数は、実際にはファイルをコピーしません。 ドライバーのファイルをターゲット ディレクトリに適切にコピーするのは、呼び出し元のプログラムの責任です。  
  
 **SQL インストールドライバーエクスックス**の機能には、ODBCCONF を使用してアクセスすることもできます[。EXE](../../../odbc/odbcconf-exe.md).  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
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
 *ドライバー*  
 [入力]物理ドライバ名の代わりに、ユーザーに提示されるドライバの説明 (通常は関連付けられた DBMS の名前)。 *lpszDriver*引数には、ドライバーを記述するキーワードと値のペアの二重の null で終わるリストが含まれている必要があります。 キーワードと値のペアの詳細については、「[ドライバ仕様サブキー](../../../odbc/reference/install/driver-specification-subkeys.md)」を参照してください。 二重に NULL で終わる文字列の詳細については、 [ConfigDSN 関数](../../../odbc/reference/syntax/configdsn-function.md)を参照してください。  
  
 *を使用します。*  
 [入力]インストール先ディレクトリの完全パス、または null ポインタ。 *lpszPathIn*が null ポインタの場合、ドライバはシステム ディレクトリにインストールされます。  
  
 *を使用します。*  
 [出力]ドライバーをインストールするターゲット ディレクトリのパス。 ドライバが以前にインストールされていない場合は *、lpszPathOut*は*lpszPathIn*と同じである必要があります。 ドライバが以前にインストールされている場合 *、lpszPathOut*は以前のインストールのパスです。  
  
 *最大のパス*  
 [入力]*の*長さ。  
  
 *pcb パスアウト*  
 [出力]*lpszPathOut*で戻すために使用可能なバイトの総数 (NULL 終了文字を除く)。 戻されるバイト数が*cbPathOutMax*以上の場合 *、lpszPathOut*の出力パスは *、cbPathOutMax*から NULL 終了文字を引いた値まで切り捨てられます。 *引数 pcbPathOut*は、ヌル・ポインターにすることができます。  
  
 *リクエスト*  
 [入力]要求の種類。 *fRequest*引数には、次のいずれかの値を指定する必要があります。  
  
 ODBC_INSTALL_INQUIRY: ドライバのインストール先を問い合わせ  
  
 ODBC_INSTALL_COMPLETE: インストール要求を完了します。  
  
 *使用法のカウント*  
 [出力]この関数が呼び出された後のドライバーの使用カウント。  
  
 アプリケーションでは、使用カウントを設定しないでください。 ODBC はこのカウントを維持します。  
  
## <a name="returns"></a>戻り値  
 関数は成功した場合は TRUE を返し、失敗した場合は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 **SQL インストールドライバーExが**FALSE を返すとき、関連付けられた*\*pfErrorCode*値を取得するには **、SQL インストーラエラー**を呼び出します。 次の表は **、SQLInstallerError***\** によって返される可能性のある pfErrorCode 値の一覧であり、この関数のコンテキストでそれぞれについて説明します。  
  
|*\*エラーコード*|エラー|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|インストーラの一般的なエラー|特定のインストーラ エラーが発生しなかったエラーが発生しました。|  
|ODBC_ERROR_INVALID_BUFF_LEN|バッファ長が無効です|*引数 lpszPathOut*が出力パスを格納するのに十分な大きさではありませんでした。 バッファーには、切り捨てられたパスが含まれています。<br /><br /> *引数*は 0 で *、fRequest*はODBC_INSTALL_COMPLETE。|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|無効な種類の要求|*fRequest*引数は、次の引数の 1 つではありません。<br /><br /> ODBC_INSTALL_INQUIRY ODBC_INSTALL_COMPLETE|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|無効なキーワードと値のペア|*引数 lpszDriver*に構文エラーが含まれていました。|  
|ODBC_ERROR_INVALID_PATH|インストール パスが無効です|*引数に*無効なパスが含まれています。|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|ドライバまたはトランスレータセットアップライブラリを読み込めませんでした|ドライバ セットアップ ライブラリを読み込めませんでした。|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|無効なパラメータ シーケンス|*引数 lpszDriver*にキーワードと値のペアのリストが含まれていませんでした。|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|コンポーネントの使用カウントをインクリメントまたはデクリメントできませんでした|インストーラーは、ドライバーの使用カウントをインクリメントできませんでした。|  
  
## <a name="comments"></a>説明  
 *引数 lpszDriver*は、キーワードと値のペアの形式の属性のリストです。 各ペアはヌルバイトで終了し、リスト全体がヌルバイトで終了します。 (つまり、2 つの null バイトがリストの末尾をマークします。このリストの形式は次のとおりです。  
  
 _ドライバー-desc_ **\\**0**=** ドライバー_ドライバー DLL-ファイル名_**\\**0[**=**_セットアップ-DLL-ファイル名_<b>\\</b>0]  
  
 [_ドライバー -attr-キーワード1_**=**_値1_<b>\\</b>0]ドライバー _-attr-キーワード2_**=**_値2_<b>\\</b>0]。<b>\\</b>0  
  
 \0 は null バイト、*ドライバ attr-keywordn*は任意のドライバ属性キーワードです。 キーワードは指定された順序で指定する必要があります。 たとえば、フォーマットされたテキスト ファイルのドライバーが別のドライバーとセットアップ DLL を持っており、.txt と .csv 拡張子を持つファイルを使用できるとします。 このドライバの*引数は、* 次のようになります。  
  
```  
Text\0Driver=TEXT.DLL\0Setup=TXTSETUP.DLL\0FileUsage=1\0  
FileExtns=*.txt,*.csv\0\0  
```  
  
 SQL Server 用のドライバーが別のセットアップ DLL を持っていないと、ドライバー属性キーワードを持っていないとします。 このドライバの*引数は、* 次のようになります。  
  
```  
SQL Server\0Driver=SQLSRVR.DLL\0\0  
```  
  
 **引数** *lpszDriver*からドライバーに関する情報を取得した後、システム情報の Odbcinst.ini エントリの [ODBC ドライバー] セクションにドライバーの説明を追加します。 次に、ドライバーの説明を含むセクションを作成し、ドライバー DLL とセットアップ DLL の完全なパスを追加します。 最後に、インストール先ディレクトリのパスを返しますが、ドライバファイルはコピーされません。 呼び出し側のプログラムは、実際にドライバファイルをターゲットディレクトリにコピーする必要があります。  
  
 **インストールされている**ドライバーのコンポーネントの使用カウントを 1 インクリメントします。 ドライバのバージョンが既に存在するが、そのドライバのコンポーネントの使用カウントが存在しない場合、新しいコンポーネントの使用カウント値は 2 に設定されます。  
  
 アプリケーションセットアッププログラムは、ドライバファイルを物理的にコピーし、ファイルの使用数を維持します。 ドライバ ファイルが以前にインストールされていない場合、アプリケーション セットアップ プログラムは*lpszPathIn*パスにファイルをコピーし、ファイルの使用率カウントを作成する必要があります。 ファイルが既にインストールされている場合、セットアップ プログラムはファイルの使用カウントをインクリメントし *、lpszPathOut*引数に以前のインストールのパスを返します。  
  
> [!NOTE]  
>  コンポーネントの使用率カウントとファイル使用量カウントの詳細については、「[使用状況カウント](../../../odbc/reference/install/usage-counting.md)」を参照してください。  
  
 以前にアプリケーションによってインストールされたドライバ ファイルの古いバージョンの場合は、ドライバコンポーネントの使用率が有効になるように、ドライバをアンインストールしてから再インストールする必要があります。 *(ODBC_REMOVE_DRIVERの fRequest*を持つ) **SQLConfigDriver**は、まず呼び出**す必要があります**。 **次に、コンポーネントの**使用カウントをインクリメントして、ドライバーを再インストールするために呼び出す必要があります。 アプリケーションセットアッププログラムは、古いファイルを新しいファイルで置き換える必要があります。 ファイルの使用カウントは同じままになり、古いバージョンのファイルを使用していた他のアプリケーションは新しいバージョンを使用します。  
  
> [!NOTE]  
>  ドライバが以前にインストールされ、別のディレクトリにドライバをインストールするために**SQLInstallDriverEx**が呼び出された場合、関数はTRUEを返しますが *、lpszPathOut*にはドライバが既にインストールされているディレクトリが含まれます。 *引数 lpszDriver*に入力されたディレクトリは含まれません。  
  
 **SQLInstallDriverEx**の*lpszPathOut*のパスの長さは、2 フェーズのインストール プロセスを可能にするため、アプリケーションは、ODBC_INSTALL_INQUIRY モードの*fRequest*を使用して**SQLInstallDriverEx**を呼び出すことによって *、cbPathOutMax*が必要なを決定できます。 これは *、pcbPathOut*バッファーで使用可能なバイトの合計数を返します。 その**後、ODBC_INSTALL_COMPLETE**の*fRequest*と、引数*cbPathOut*バッファーの値に設定された null 終了*pcbPathOut*文字を指定して呼び出すことができます。  
  
 **SQLInstallDriverEx**の 2 フェーズ モデルを使用しない場合は、stdlib.h で定義されている値 _MAX_PATHに対して、ターゲット ディレクトリのパスのストレージのサイズを定義する*cbPathOutMax*を Stdlib.h で定義されている値に設定する必要があります。  
  
 *fRequest*がODBC_INSTALL_COMPLETEされると **、SQLInstallDriverEx**は *、lpszPathOut*を NULL (または*cbPathOutMax*を 0 にする) を許可しません。 *fRequest*がODBC_INSTALL_COMPLETE場合、返されるバイト数が*cbPathOutMax*以上の場合に FALSE が返され、切り捨てが発生します。  
  
 **SQLInstallDriverEx**が呼び出され、アプリケーションセットアップ プログラムが (必要な場合) ドライバー ファイルをコピーした後、ドライバーセットアップ DLL は、ドライバーの構成を設定する**SQLConfigDriver**を呼び出す必要があります。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|ドライバー マネージャーのインストール|[ドライバー マネージャー](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|
