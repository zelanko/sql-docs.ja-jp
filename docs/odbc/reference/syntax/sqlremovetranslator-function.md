---
title: "SQLRemoveTranslator 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLRemoveTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveTranslator
helpviewer_keywords:
- SQLRemoveTranslator function [ODBC]
ms.assetid: c6feda49-0359-4224-8de9-77125cf2397b
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c859eba5dc2b064c595ce57dffa2bde6aeda364e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlremovetranslator-function"></a>SQLRemoveTranslator 関数
**準拠**  
 バージョンが導入されています。 ODBC 3.0  
  
 **概要**  
 **SQLRemoveTranslator**情報を削除、トランスレーター、Odbcinst.ini のセクションからシステム情報およびデクリメント トランスレーターのコンポーネントの使用率カウントを 1 つです。  
  
## <a name="syntax"></a>構文  
  
```  
  
BOOL SQLRemoveTranslator(  
     LPCSTR    lpszTranslator,  
     LPDWORD   lpdwUsageCount);  
```  
  
## <a name="arguments"></a>引数  
 *lpszTranslator*  
 [入力]システム情報の Odbcinst.ini キーに登録されている変換プログラムの名前。  
  
 *lpdwUsageCount*  
 [出力]この関数が呼び出された後、変換プログラムの使用率カウントします。  
  
## <a name="returns"></a>返します。  
 関数は、それが成功した場合、FALSE が失敗した場合に TRUE を返します。 エントリが存在しない場合、システム情報でこの関数が呼び出されたときに、関数は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLRemoveTranslator**は FALSE を返します、関連付けられている *\*pfErrorCode*を呼び出して値を取得する**SQLInstallerError**です。 次の表、  *\*pfErrorCode*によって返される値**SQLInstallerError**とコンテキストでこの関数のいずれかを説明します。  
  
|*\*pfErrorCode*|[エラー]|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|一般的なインストーラーのエラー|エラーが発生する特定のインストーラーのエラーがなかった。|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|コンポーネントがレジストリに見つかりません|インストーラーは、次のレジストリに存在しませんでしたや、レジストリに見つかりませんだったためには変換プログラムの情報を削除できませんでした。|  
|ODBC_ERROR_INVALID_NAME|無効なドライバーまたは変換者の名前|*LpszTranslator*引数が無効です。|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|インクリメントまたはコンポーネントの使用率カウントは減少できませんでした。|ドライバーの使用率カウントをデクリメントするためにインストーラーが失敗しました。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|インストーラーは、メモリの不足のため、関数を実行できませんでした。|  
  
## <a name="comments"></a>コメント  
 **SQLRemoveTranslator**補完するもの、 [SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)コンポーネントの使用法のシステム情報のカウント関数と更新プログラム。 この関数は、セットアップ アプリケーションからのみ呼び出す必要があります。  
  
 **SQLRemoveTranslator**を 1 つのコンポーネントの使用率カウントをデクリメントします。 コンポーネントの使用率カウントが 0 になった場合は、システム情報の変換プログラムのエントリが削除されます。 トランスレーター エントリは、システムについては、変換プログラム名の下に次の場所には。  
  
 `HKEY_LOCAL_MACHINE`  
  
 `SOFTWARE`  
  
 `ODBC`  
  
 `Odbcinst.ini`  
  
 **SQLRemoveTranslator**すべてのファイルを実際に削除されません。 呼び出し元のプログラムは、ファイルを削除して、ファイルの使用率カウントを保守を担当します。 コンポーネントの使用率カウントとファイルの使用率カウントの両方に達した後にのみ、0 は、物理的に削除ファイルになります。 コンポーネントの一部のファイルを削除でき、他のユーザーは削除されません、ファイルの使用率カウントをインクリメントが他のアプリケーションでファイルを使用するかどうかによって異なります。  
  
 **SQLRemoveTranslator**アップグレード プロセスの一部としても呼ばれます。 アプリケーション検出した場合のアップグレードを実行する必要があることと、ドライバーが既にインストール、ドライバーを削除して再インストールする必要があります。 **SQLRemoveTranslator**コンポーネント使用率カウントをデクリメントするために呼び出す必要がありますはまずし**SQLInstallTranslatorEx**コンポーネントの使用率カウントをインクリメントするために呼び出す必要があります。 アプリケーションのセットアップ プログラムは、新しいファイルで古いファイルを置き換えます物理的にする必要があります。 ファイルの使用率カウントは変わりません、および古いバージョンのファイルを使用するその他のアプリケーションの新しいバージョンが使用されます。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|翻訳者をインストールします。|[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|

