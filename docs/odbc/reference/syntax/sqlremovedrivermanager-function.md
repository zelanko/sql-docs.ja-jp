---
title: SQLRemoveDriverManager 関数 |Microsoft ドキュメント
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
- SQLRemoveDriverManager
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDriverManager
helpviewer_keywords:
- SQLRemoveDriverManager function function [ODBC]
ms.assetid: 3a41511f-6603-4b81-a815-7883874023c4
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8d74b3b3eda914210f8d69d6089eb9a474416318
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlremovedrivermanager-function"></a>SQLRemoveDriverManager 関数
**準拠**  
 バージョンの導入された: ODBC 3.0: Windows XP Service Pack 2、Windows Server 2003 Service Pack 1 以降のオペレーティング システムで推奨されなくなりました。  
  
 **概要**  
 **SQLRemoveDriverManager**システム情報の Odbcinst.ini エントリから ODBC コア コンポーネントに関する情報を削除または変更します。  
  
## <a name="syntax"></a>構文  
  
```  
  
BOOL SQLRemoveDriverManager(  
     LPDWORD     pdwUsageCount);  
```  
  
## <a name="arguments"></a>引数  
 *pdwUsageCount*  
 [出力]使用率カウントのドライバー マネージャーがこの関数が呼び出された後にします。  
  
## <a name="returns"></a>戻り値  
 関数は、それが成功した場合、FALSE が失敗した場合に TRUE を返します。 エントリが存在しない場合、システム情報でこの関数が呼び出されたときに、関数は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLRemoveDriverManager**は FALSE を返します、関連付けられている *\*pfErrorCode*を呼び出して値を取得する**SQLInstallerError**です。 次の表、  *\*pfErrorCode*によって返される値**SQLInstallerError**とコンテキストでこの関数のいずれかを説明します。  
  
|*\*pfErrorCode*|[エラー]|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|一般的なインストーラーのエラー|エラーが発生する特定のインストーラーのエラーがなかった。|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|コンポーネントがレジストリに見つかりません|インストーラーは、レジストリに存在しませんでしたや、レジストリに見つかりませんでしたので、ドライバー マネージャーの情報を削除できませんでした。|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|インクリメントまたはコンポーネントの使用率カウントは減少できませんでした。|ドライバー マネージャーの使用率カウントをデクリメントするためにインストーラーが失敗しました。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|インストーラーは、メモリの不足のため、関数を実行できませんでした。|  
  
## <a name="comments"></a>コメント  
 **SQLRemoveDriverManager**補完するもの、 **SQLInstallDriverManager**関数、およびコンポーネントの使用カウントはシステム情報に更新します。 この関数は、セットアップ アプリケーションからのみ呼び出す必要があります。  
  
 **SQLRemoveDriverManager**コア コンポーネントの使用率カウントは 1 減ります。 コンポーネントの使用率カウントが 0 になった場合は、エントリのシステム情報が削除されます。 コア コンポーネントのエントリは、システムについては、"ODBC Core"というタイトルの下に次の場所には。  
  
 `HKEY_LOCAL_MACHINE`  
  
 `SOFTWARE`  
  
 `ODBC`  
  
 `Odbcinst.ini`  
  
> [!CAUTION]  
>  アプリケーションに物理的に削除しないでドライバー マネージャーのファイル コンポーネントの使用率カウントとファイルの使用率カウントは 0 に達した場合。  
  
 **SQLRemoveDriverManager**すべてのファイルを実際に削除されません。 呼び出し元のプログラムは、ファイルを削除して、ファイルの使用状況を維持する数します。 ドライバー マネージャーのファイルは、しないで、ただし、これらのファイルは、ファイルの使用率カウントはインクリメントされませんが他のアプリケーションで使用される可能性がありますので、達するコンポーネントの使用率カウントとファイルの使用率カウントの両方が 0、削除されます。  
  
 **SQLRemoveDriverManager**アンインストール プロセスの一部として呼び出されます。 ODBC コア コンポーネントが含まれるドライバー マネージャー、カーソル ライブラリ、インストーラー、言語ライブラリ、管理者、サンク ファイル、およびなど) は、全体としてアンインストールします。 次のファイルがない場合に削除**SQLRemoveDriverManager**がアンインストール プロセスの一部として呼び出されて。  
  
|||  
|-|-|  
|ODBC32DLL|ODBCCP32 です。DLL|  
|ODBCCR32 です。DLL|ODBC16GT です。DLL|  
|ODBCCU32 です。DLL|ODBC32GT です。DLL|  
|ODBCINT です。DLL|DS16GT です。DLL|  
|ODBCTRAC です。DLL|DS32GT です。DLL|  
|MSVCRT40 です。DLL|ODBCAD32 です。EXE|  
|ODBCCP32 です。CPL||  
  
 **SQLRemoveDriverManager**アップグレード プロセスの一部としても呼ばれます。 アプリケーション検出した場合のアップグレードを実行する必要があることと、ドライバーが既にインストール、ドライバーを削除して再インストールする必要があります。  
  
 **SQLRemoveDriverManager**コンポーネントの使用率カウントをデクリメントするために呼び出す必要がありますはまずします。 **SQLInstallDriverEx**をコンポーネントの使用率カウントをインクリメントしと呼ばれる必要があります。 アプリケーションのセットアップ プログラムは、以前のコア コンポーネント ファイルを新しいファイルに置き換える必要があります。 ファイル使用状況カウントが、同じままになります、および古いバージョンのコア コンポーネント ファイルを使用するその他のアプリケーションより新しいバージョンのファイルが使用されます。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|ドライバー マネージャーのインストール|[SQLInstallDriverManager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|
