---
title: 関数を削除する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRemoveDSNFromIni
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDSNFromIni
helpviewer_keywords:
- SQLRemoveDSNFromIni function [ODBC]
ms.assetid: bb2e8273-7b61-4113-bfc8-f7ccc607c811
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 848e82741954ab24941d5d519699292727ca25d6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301801"
---
# <a name="sqlremovedsnfromini-function"></a>SQLRemoveDSNFromIni 関数
**適合 性**  
 バージョン導入: ODBC 1.0  
  
 **まとめ**  
 システム情報からデータ ソース**を削除します**。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
BOOL SQLRemoveDSNFromIni(  
     LPCSTR   lpszDSN);  
```  
  
## <a name="arguments"></a>引数  
 *を指定します。*  
 [入力]削除するデータ ソースの名前。  
  
## <a name="returns"></a>戻り値  
 データ ソースを削除した場合、または Odbc.ini ファイルにデータ ソースが含まれていない場合、この関数は TRUE を返します。 データ ソースの削除に失敗した場合は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 **SQLRemoveDSNFromIni**が FALSE を返すと **、SQL インストーラ エラー**を呼び出すことによって関連付けられた*\*pfErrorCode*値を取得できます。 次の表は **、SQLInstallerError***\** によって返される可能性のある pfErrorCode 値の一覧であり、この関数のコンテキストでそれぞれについて説明します。  
  
|*\*エラーコード*|エラー|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|インストーラの一般的なエラー|特定のインストーラ エラーが発生しなかったエラーが発生しました。|  
|ODBC_ERROR_INVALID_DSN|無効な DSN|*引数が無効*です。|  
|ODBC_ERROR_REQUEST_FAILED|要求が失敗しました|インストーラーは、レジストリから DSN 情報を削除できませんでした。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|メモリ不足のため、インストーラは機能を実行できませんでした。|  
  
## <a name="comments"></a>説明  
 **システム**情報の [ODBC データ ソース] セクションからデータ ソース名を削除します。 また、システム情報からデータ ソース仕様セクションも削除されます。  
  
 この関数は、ドライバセットアップライブラリからのみ呼び出してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|データ ソースの追加、変更、または削除|[構成DSN](../../../odbc/reference/syntax/configdsn-function.md)|  
|データ ソースの追加、変更、または削除|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|既定のデータ ソースを削除する|[データ ソースを削除します。](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|  
|システム情報へのデータ・ソース名の追加|[を使用します。](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
