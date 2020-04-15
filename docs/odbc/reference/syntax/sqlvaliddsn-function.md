---
title: 関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLValidDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLValidDSN
helpviewer_keywords:
- SQLValidDSN [ODBC]
ms.assetid: 930d1d89-337a-4429-85a2-84ee10555ac9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6dfafca22d0b04f2147b1af24b53e787493efe67
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286972"
---
# <a name="sqlvaliddsn-function"></a>SQLValidDSN 関数
**適合 性**  
 バージョン導入: ODBC 2.0  
  
 **まとめ**  
 **SQLValidDSN は**、名前がシステム情報に追加される前に、データ・ソース名の長さと妥当性を検査します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
BOOL SQLValidDSN(  
     LPCSTR    lpszDSN);  
```  
  
## <a name="arguments"></a>引数  
 *を指定します。*  
 [入力]チェックするデータ ソース名。  
  
## <a name="returns"></a>戻り値  
 データ ソース名が有効な場合は、関数は TRUE を返します。 データ ソース名が無効な場合、または関数呼び出しが失敗した場合は、FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 **SQLValidDSN が**FALSE を返すと、関連付けられた*\*pfErrorCode*値を取得するには **、SQLInstallerError**を呼び出します。 pfErrorCode は、関数の呼び出しが失敗した場合にのみ返され、データ ソース名が無効なために FALSE が返された場合は返されません。 * \** 次の表は **、SQLInstallerError***\** によって返される可能性のある pfErrorCode 値の一覧であり、この関数のコンテキストでそれぞれについて説明します。  
  
|*\*エラーコード*|エラー|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|インストーラの一般的なエラー|特定のインストーラ エラーが発生しなかったエラーが発生しました。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|メモリ不足のため、インストーラは機能を実行できませんでした。|  
  
## <a name="comments"></a>説明  
 **SQLValidDSN**は、データ ソース名の長さとデータ ソース名の個々の文字の有効性を確認するために、ドライバーの[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)によって呼び出されます。 Sqlext.h で定義されている名前の長さがSQL_MAX_DSN_LENGTHより大きいかどうかをチェックします。 (データ ソース名の長さは[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)によってもチェックされます。**SQLValidDSN は**、次の無効な文字のいずれかがデータ・ソース名に含まれているかどうかを検査します。  
  
 [ ] { } ( ) , ; ? * = ! \@ \  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|データ ソースの追加、変更、または削除|[構成 DSN](../../../odbc/reference/syntax/configdsn-function.md) (セットアップ DLL 内)|  
|データ ソースの追加、変更、または削除|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|システム情報へのデータ・ソース名の書き込み|[を使用します。](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
