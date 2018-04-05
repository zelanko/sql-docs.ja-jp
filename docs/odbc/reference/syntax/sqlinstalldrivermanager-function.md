---
title: SQLInstallDriverManager 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7d1769b4951662f99cd50709b498891540fd4b9c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlinstalldrivermanager-function"></a>SQLInstallDriverManager 関数
**準拠**  
 バージョンの導入された: ODBC 1.0: Windows XP Service Pack 2、Windows Server 2003 Service Pack 1 以降のオペレーティング システムで推奨されなくなりました  
  
 **概要**  
 **SQLInstallDriverManager** ODBC コア コンポーネントのインストールのターゲット ディレクトリのパスを返します。 呼び出し元のプログラムは、ターゲット ディレクトリに、ドライバー マネージャーのファイルをコピーする必要があります実際にします。  
  
## <a name="syntax"></a>構文  
  
```  
  
BOOL SQLInstallDriverManager(  
     LPSTR    lpszPath,  
     WORD     cbPathMax,  
     WORD *   pcbPathOut);  
```  
  
## <a name="arguments"></a>引数  
 *lpszPath*  
 [出力]インストールのターゲット ディレクトリのパス。  
  
 *cbPathMax*  
 [入力]長さ*lpszPath*です。 これ以上でなければなりません _MAX_PATH バイトです。  
  
 *pcbPathOut*  
 [出力]合計バイト数 (null 終了バイトを除く) で返される*lpszPath*です。 場合は、使用できるバイト数を返すより大きいまたは等しい*cbPathMax*、パス*lpszPath*に切り捨てられます*cbPathMax* null 終了負符号文字があります。 *PcbPathOut*引数が null ポインターを指定できます。  
  
## <a name="returns"></a>戻り値  
 関数は、それが成功した場合、FALSE が失敗した場合に TRUE を返します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLInstallDriverManager**は FALSE を返します、関連付けられている *\*pfErrorCode*を呼び出して値を取得する**SQLInstallerError**です。 次の表、  *\*pfErrorCode*によって返される値**SQLInstallerError**とコンテキストでこの関数のいずれかを説明します。  
  
|*\*pfErrorCode*|[エラー]|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|一般的なインストーラーのエラー|エラーが発生する特定のインストーラーのエラーがなかった。|  
|ODBC_ERROR_INVALID_BUFF_LEN|無効なバッファーの長さ|*LpszPath*引数が出力パスを格納するのに十分な大きさがありません。 バッファーには、切り捨てられたパスが含まれています。<br /><br /> *CbPathMax*引数が _MAX_PATH 未満です。|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|インクリメントまたはコンポーネントの使用率カウントは減少できませんでした。|ODBC コア コンポーネントの使用率カウントをインクリメントするインストーラーが失敗しました。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|インストーラーは、メモリの不足のため、関数を実行できませんでした。|  
  
## <a name="comments"></a>コメント  
 **SQLInstallDriverManager** ODBC コア コンポーネントとコンポーネントの使用状況の増分数をシステム情報でのパスを返すために呼び出されます。 バージョンのドライバー マネージャーが既に存在する、コンポーネントの使用カウント、ドライバーが存在しない場合は、新しいコンポーネントの使用状況カウント値が 2 に設定します。  
  
 アプリケーションのセットアップ プログラムは、物理的にコア コンポーネントのファイルのコピーと、ファイルの使用状況を維持する数します。 コア コンポーネントのファイルが既にインストールされていない場合、アプリケーションのセットアップ プログラム ファイルのコピーしてファイルの使用率カウントを作成します。 ファイルが既にインストールされている場合、セットアップ プログラムは単なるファイルの使用率カウントをインクリメントします。  
  
 場合は、アプリケーションのセットアップ プログラムによっては、古いバージョンのドライバー マネージャーがインストールされていた、コア コンポーネントをアンインストールしてから再インストール、コア コンポーネントの使用率カウントは無効にできるようにする必要があります。 **SQLRemoveDriverManager**コンポーネントの使用率カウントをデクリメントするために呼び出す必要がありますはまずします。 **SQLInstallDriverManager**をコンポーネントの使用率カウントをインクリメントしと呼ばれる必要があります。 アプリケーションのセットアップ プログラムは、以前のコア コンポーネント ファイルを新しいファイルに置き換える必要があります。 ファイル使用状況カウントが、同じままになります、および古いバージョンのコア コンポーネント ファイルを使用する他のアプリケーションより新しいバージョンのファイルが使用されます。  
  
 ODBC コア コンポーネント、ドライバー、および翻訳者の新規インストールでアプリケーションのセットアップ プログラムは、シーケンスで、次の関数を呼び出す必要があります: **SQLInstallDriverManager**、 **SQLInstallDriverEx**、 **SQLConfigDriver** (で、*起こり*ODBC_INSTALL_DRIVER の)、し**SQLInstallTranslatorEx**です。 コア コンポーネント、ドライバー、および変換プログラムのアンインストールでアプリケーションのセットアップ プログラムは、シーケンスで、次の関数を呼び出す必要があります: **SQLRemoveTranslator**、 **SQLRemoveDriver**、し、**SQLRemoveDriverManager**です。 このシーケンスでは、これらの関数を呼び出す必要があります。 すべてのコンポーネントのアップグレードでは、シーケンスのすべてのアンインストール関数を呼び出す必要があり、し、シーケンスでインストールするすべての機能を呼び出す必要があります。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|追加、変更、またはドライバーを削除します。|[SQLConfigDriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|  
|ドライバーをインストールします。|[SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|  
|翻訳者をインストールします。|[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|  
|ドライバーを削除します。|[SQLRemoveDriver](../../../odbc/reference/syntax/sqlremovedriver-function.md)|  
|ドライバー マネージャーを削除します。|[SQLRemoveDriverManager](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)|  
|翻訳者を削除します。|[SQLRemoveTranslator](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|
