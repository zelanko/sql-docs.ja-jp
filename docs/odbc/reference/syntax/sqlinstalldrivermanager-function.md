---
title: 機能 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLInstallDriverManager
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallDriverManager
helpviewer_keywords:
- SQLInstallDriverManager function [ODBC]
ms.assetid: aebc439b-fffd-4d98-907a-0163f79aee8d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0788de0493439a360c0446733b31606a02e12422
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302113"
---
# <a name="sqlinstalldrivermanager-function"></a>SQLInstallDriverManager 関数
**適合 性**  
 バージョンの導入: ODBC 1.0: Windows XP サービス パック 2、Windows Server 2003 サービス パック 1、および以降のオペレーティング システムで非推奨  
  
 **まとめ**  
 **ODBC**コア コンポーネントのインストール先ディレクトリのパスを返します。 呼び出し元のプログラムは、実際にドライバー マネージャーのファイルをターゲット ディレクトリにコピーする必要があります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
BOOL SQLInstallDriverManager(  
     LPSTR    lpszPath,  
     WORD     cbPathMax,  
     WORD *   pcbPathOut);  
```  
  
## <a name="arguments"></a>引数  
 *パス*  
 [出力]インストールのターゲット ディレクトリのパス。  
  
 *cbパスマックス*  
 [入力]*lpszPath の*長さ 。 これは少なくとも_MAX_PATHバイトでなければなりません。  
  
 *pcb パスアウト*  
 [出力]*lpszPath*で返されるバイトの総数 (ヌル終了バイトを除く)。 戻されるバイト数が*cbPathMax*以上の場合 *、lpszPath*のパスは*cbPathMax*からヌル終了文字を引いた値まで切り捨てられます。 *引数 pcbPathOut*は、ヌル・ポインターにすることができます。  
  
## <a name="returns"></a>戻り値  
 関数は成功した場合は TRUE を返し、失敗した場合は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 **FALSE を**返すと、関連付けられた*\*pfErrorCode*値を取得**できます。** 次の表は **、SQLInstallerError***\** によって返される可能性のある pfErrorCode 値の一覧であり、この関数のコンテキストでそれぞれについて説明します。  
  
|*\*エラーコード*|エラー|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|インストーラの一般的なエラー|特定のインストーラ エラーが発生しなかったエラーが発生しました。|  
|ODBC_ERROR_INVALID_BUFF_LEN|バッファ長が無効です|*lpszPath*引数は、出力パスを格納するのに十分な大きさではありませんでした。 バッファーには、切り捨てられたパスが含まれています。<br /><br /> *引数が*_MAX_PATH未満でした。|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|コンポーネントの使用カウントをインクリメントまたはデクリメントできませんでした|インストーラーは、ODBC コア コンポーネントの使用率カウントをインクリメントできませんでした。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|メモリ不足のため、インストーラは機能を実行できませんでした。|  
  
## <a name="comments"></a>説明  
 **ODBC**コア コンポーネントのパスを返し、システム情報のコンポーネントの使用カウントをインクリメントするために呼び出されます。 ドライバー マネージャーのバージョンが既に存在するが、ドライバーのコンポーネントの使用カウントが存在しない場合は、新しいコンポーネントの使用カウントの値は 2 に設定されます。  
  
 アプリケーションセットアッププログラムは、コアコンポーネントファイルを物理的にコピーし、ファイルの使用数を維持します。 コア コンポーネント ファイルがインストールされていない場合、アプリケーション セットアップ プログラムはファイルをコピーし、ファイルの使用カウントを作成する必要があります。 ファイルが既にインストールされている場合、セットアップ プログラムはファイルの使用カウントをインクリメントするだけです。  
  
 以前のバージョンの Driver Manager がアプリケーションセットアップ プログラムによってインストールされている場合は、コア コンポーネントの使用率が有効になるように、コア コンポーネントをアンインストールしてから再インストールする必要があります。 最初**に呼**び出して、コンポーネントの使用カウントを減らす必要があります。 次に、コンポーネント**の**使用カウントをインクリメントするために呼び出す必要があります。 アプリケーションセットアッププログラムは、古いコアコンポーネントファイルを新しいファイルで置き換える必要があります。 ファイル使用量カウントは同じままで、古いバージョンのコア コンポーネント ファイルを使用していた他のアプリケーションは新しいバージョンのファイルを使用します。  
  
 ODBC コア コンポーネント、ドライバー、および変換プログラムの新規インストールでは、アプリケーション セットアップ プログラムは、次 ODBC_INSTALL_DRIVERの関数を順番に呼び出**SQLInstallDriverEx**す**SQLInstallTranslatorEx**必要*fRequest***があります。** **SQLConfigDriver** コア コンポーネント、ドライバー、および変換プログラムのアンインストールでは、アプリケーション セットアップ プログラムは、次の関数を順番に呼び出す必要**SQLRemoveDriver****があります。** **SQLRemoveDriverManager** これらの関数は、このシーケンスで呼び出す必要があります。 すべてのコンポーネントのアップグレードでは、すべてのアンインストール関数を順番に呼び出し、すべてのインストール関数を順番に呼び出す必要があります。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|ドライバーの追加、変更、または削除|[ドライバー](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|  
|ドライバーのインストール|[ドライバのインストール](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|  
|変換プログラムのインストール|[トランスレータ](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|  
|ドライバの削除|[ドライバーの削除](../../../odbc/reference/syntax/sqlremovedriver-function.md)|  
|ドライバ マネージャを削除する|[をクリックします。](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)|  
|トランスレーターの削除|[トランスレータを削除します。](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|
