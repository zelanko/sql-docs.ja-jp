---
title: 関数を書き込む |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLWriteDSNToIni
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLWriteDSNToIni
helpviewer_keywords:
- SQLWriteDSNToIni [ODBC]
ms.assetid: dc7018b2-18d4-4657-96d0-086479a47474
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b8bb141c8f54c49ca3a5c6fc4bc15d434f91795c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286962"
---
# <a name="sqlwritedsntoini-function"></a>SQLWriteDSNToIni 関数
**適合 性**  
 バージョン導入: ODBC 1.0  
  
 **まとめ**  
 **システム**情報にデータ ソースを追加します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
BOOL SQLWriteDSNToIni(  
     LPCSTR   lpszDSN,  
     LPCSTR   lpszDriver);  
```  
  
## <a name="arguments"></a>引数  
 *を指定します。*  
 [入力]追加するデータ ソースの名前。  
  
 *ドライバー*  
 [入力]物理ドライバ名の代わりに、ドライバの説明 (通常は関連付けられた DBMS の名前) をユーザーに表示します。  
  
## <a name="returns"></a>戻り値  
 関数は成功した場合は TRUE を返し、失敗した場合は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 **SQLWriteDSNToIni**が FALSE を返すと、SQL**インストーラ エラー**を呼び出すことによって、関連付けられた*\*pfErrorCode*値を取得できます。 次の表は **、SQLInstallerError***\** によって返される可能性のある pfErrorCode 値の一覧であり、この関数のコンテキストでそれぞれについて説明します。  
  
|*\*エラーコード*|エラー|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|インストーラの一般的なエラー|特定のインストーラ エラーが発生しなかったエラーが発生しました。|  
|ODBC_ERROR_INVALID_DSN|無効な DSN|*引数 lpszDSN*に DSN に対して無効な文字列が含まれています。|  
|ODBC_ERROR_INVALID_NAME|無効なドライバまたはトランスレータ名|*引数が*無効です。|  
|ODBC_ERROR_REQUEST_FAILED|要求が失敗しました|レジストリに DSN を作成できませんでした。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|メモリ不足のため、インストーラは機能を実行できませんでした。|  
  
## <a name="comments"></a>説明  
 **システム**情報の [ODBC データ ソース] セクションにデータ ソースが追加されます。 次に、データ ソースの仕様セクションを作成し、値としてドライバー DLL の名前を持つ単一のキーワード (**Driver**) を追加します。 データ ソース仕様セクションが既に存在する**場合は、** 新しいセクションを作成する前に、古いセクションが削除されます。  
  
 この関数の呼び出し元は、システム情報のデータ ソース仕様セクションに、ドライバー固有のキーワードと値を追加する必要があります。  
  
 データ ソースの名前が既定の場合は、**システム**情報に既定のドライバーの仕様セクションも作成します。  
  
 この関数は、セットアップ DLL からのみ呼び出してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|データ ソースの追加、変更、または削除|[構成 DSN](../../../odbc/reference/syntax/configdsn-function.md)(セットアップ DLL 内)|  
|データ ソースの追加、変更、または削除|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|システム情報からのデータ・ソース名の除去|[イニから削除します。](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|
