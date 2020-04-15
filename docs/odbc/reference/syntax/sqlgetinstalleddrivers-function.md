---
title: ドライバ関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetInstalledDrivers
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetInstalledDrivers
helpviewer_keywords:
- SQLGetInstalledDrivers function [ODBC]
ms.assetid: a1983a2e-0edf-422e-bd1b-ec5db40a34bc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 24793473bf4f25253ac11673df852d10cfb2c558
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303329"
---
# <a name="sqlgetinstalleddrivers-function"></a>SQLGetInstalledDrivers 関数
**適合 性**  
 バージョン導入: ODBC 1.0  
  
 **まとめ**  
 **システム**情報の [ODBC ドライバー] セクションを読み取り、インストールされているドライバーの説明の一覧を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
BOOL SQLGetInstalledDrivers(  
     LPSTR   lpszBuf,  
     WORD    cbBufMax,  
     WORD *  pcbBufOut);  
```  
  
## <a name="arguments"></a>引数  
 *lpszBuf*  
 [出力]インストールされているドライバの説明の一覧です。 リスト構造の詳細については、「コメント」を参照してください。  
  
 *cbBufMax*  
 [入力]*lpszBuf*の長さ 。  
  
 *pcbBufOut*  
 [出力]*lpszBuf*で戻されるバイトの総数 (ヌル終了バイトを除く)。 戻り値のバイト数が*cbBufMax*以上の場合 *、lpszBuf*のドライバー記述のリストは *、cbBufMax*からヌル終了文字を引いた値に切り捨てられます。 *引数は*null ポインターにすることができます。  
  
## <a name="returns"></a>戻り値  
 関数は成功した場合は TRUE を返し、失敗した場合は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 **SQLGet インストール ドライバーが**FALSE を返すときは、SQLInstallerError を呼び出すことによって関連付けられた*\*pfErrorCode*値**を**取得できます。 次の表は **、SQLInstallerError***\** によって返される可能性のある pfErrorCode 値の一覧であり、この関数のコンテキストでそれぞれについて説明します。  
  
|*\*エラーコード*|エラー|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|インストーラの一般的なエラー|特定のインストーラ エラーが発生しなかったエラーが発生しました。|  
|ODBC_ERROR_INVALID_BUFF_LEN|バッファ長が無効です|*引数が*NULL であるか、または無効であったか、または*cbBufMax*引数が 0 以下であったか、または等しい。|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|レジストリにコンポーネントが見つかりません|レジストリに [ODBC ドライバ] セクションが見つかりませんでした。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|メモリ不足のため、インストーラは機能を実行できませんでした。|  
  
## <a name="comments"></a>説明  
 各ドライバーの説明は、NULL バイトで終了し、リスト全体が NULL バイトで終了します。 (つまり、2 つの null バイトがリストの末尾をマークします。割り当てられたバッファがリスト全体を保持するのに十分な大きさでない場合、リストはエラーなしで切り捨てられます。 null ポインターが*lpszBuf*として渡された場合は、エラーが返されます。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|ドライバーの説明と属性を返す|[SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|
