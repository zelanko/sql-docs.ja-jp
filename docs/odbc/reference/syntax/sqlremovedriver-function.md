---
title: ドライバ関数の削除 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRemoveDriver
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDriver
helpviewer_keywords:
- SQLRemoveDriver function [ODBC]
ms.assetid: 9a3b4f8b-982b-44b9-ade6-754ff026dc90
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 205c5b46e5f6cea195094f7a50e81d7509927d1a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303933"
---
# <a name="sqlremovedriver-function"></a>SQLRemoveDriver 関数
**適合 性**  
 バージョン導入: ODBC 3.0  
  
 **まとめ**  
 **システム情報の**Odbcinst.ini エントリからドライバーに関する情報を変更または削除します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
BOOL SQLRemoveDriver(  
     LPCSTR   lpszDriver,  
     BOOL     fRemoveDSN,  
     LPDWORD  lpdwUsageCount);  
```  
  
## <a name="arguments"></a>引数  
 *ドライバー*  
 [入力]システム情報の Odbcinst.ini キーに登録されているドライバーの名前。  
  
 *をクリックします。*  
 [入力]有効な値は次のとおりです。  
  
 TRUE: *lpszDriver*で指定されたドライバーに関連付けられている DSN を削除します。 FALSE: *lpszDriver*で指定されたドライバに関連付けられている DSN を削除しないでください。  
  
 *使用法のカウント*  
 [出力]この関数が呼び出された後のドライバーの使用カウント。  
  
## <a name="returns"></a>戻り値  
 関数は成功した場合は TRUE を返し、失敗した場合は FALSE を返します。 この関数が呼び出されたときにシステム情報にエントリが存在しない場合、この関数は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 **SQLRemoveDriver が**FALSE を返すと、関連付けられた*\*pfErrorCode*値を取得するには **、SQLInstallerError**を呼び出します。 次の表は **、SQLInstallerError***\** によって返される可能性のある pfErrorCode 値の一覧であり、この関数のコンテキストでそれぞれについて説明します。  
  
|*\*エラーコード*|エラー|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|インストーラの一般的なエラー|特定のインストーラ エラーが発生しなかったエラーが発生しました。|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|レジストリにコンポーネントが見つかりません|レジストリに存在しないか、またはレジストリに見つからなかったため、インストーラーはドライバ情報を削除できませんでした。|  
|ODBC_ERROR_INVALID_NAME|無効なドライバまたはトランスレータ名|*引数が*無効です。|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|コンポーネントの使用カウントをインクリメントまたはデクリメントできませんでした|インストーラーは、ドライバーの使用カウントを減らすに失敗しました。|  
|ODBC_ERROR_REQUEST_FAILED|要求が失敗しました|*引数*は TRUE でした。ただし、1 つ以上の DSN を削除できませんでした。 ODBC_REMOVE_DRIVER要求を伴う**SQLConfigDriver**への呼び出しが失敗しました。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|メモリ不足のため、インストーラは機能を実行できませんでした。|  
  
## <a name="comments"></a>説明  
 **関数**[を補完](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)し、システム情報のコンポーネントの使用カウントを更新します。 この関数は、セットアップ アプリケーションからのみ呼び出す必要があります。  
  
 **コンポーネントの**使用カウント値を 1 減算します。 コンポーネントの使用率が 0 になると、次の処理が行われます。  
  
1.  ODBC_REMOVE_DRIVERオプションを指定した**SQLConfigDriver**関数が呼び出されます。 *fRemoveDSN*オプションが TRUE に設定されている場合、**構成DSN**関数は**SQLRemoveDSNFromIni**を呼び出して *、lpszDriver*で指定されたドライバーに関連付けられているすべてのデータ ソースを削除します。 *fRemoveDSN*オプションが FALSE に設定されている場合、データ ソースは削除されません。  
  
2.  システム情報のドライバエントリが削除されます。 ドライバーのエントリは、ドライバー名の下に、次のシステム情報の場所にあります。  
  
     `HKEY_LOCAL_MACHINE`  
  
     `SOFTWARE`  
  
     `ODBC`  
  
     `Odbcinst.ini`  
  
 **実際**にはファイルは削除されません。 呼び出し元のプログラムは、ファイルの削除とファイル使用カウントの維持を行います。 コンポーネントの使用カウントとファイル使用量カウントがゼロに達した後にのみ、ファイルは物理的に削除されます。 コンポーネント内の一部のファイルは削除でき、その他のファイルは、ファイル使用量カウントをインクリメントした他のアプリケーションによって使用されているかどうかによって、削除されません。  
  
 **アップグレード**プロセスの一部として呼び出されます。 アプリケーションがアップグレードを実行する必要があることを検出し、以前にドライバをインストールした場合は、ドライバを削除してから再インストールする必要があります。 **まず**、コンポーネントの使用カウントを減らすために呼び出す必要があり、次に、コンポーネントの使用カウントをインクリメントするために**SQLInstallDriverEx**を呼び出す必要があります。 アプリケーションセットアッププログラムは、古いファイルを新しいファイルで置き換える必要があります。 ファイルの使用数は変わらず、古いバージョンのファイルを使用する他のアプリケーションは新しいバージョンを使用します。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|ドライバーの追加、変更、または削除|[構成ドライバー](../../../odbc/reference/syntax/configdriver-function.md) (セットアップ DLL 内)|  
|ドライバーの追加、変更、または削除|[ドライバー](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|  
|ドライバーのインストール|[ドライバのインストール](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|
