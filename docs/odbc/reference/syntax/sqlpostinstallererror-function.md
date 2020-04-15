---
title: エラー関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLPostInstallerError
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLPostInstallerError
helpviewer_keywords:
- SQLPostInstallerError function [ODBC]
ms.assetid: 4c60d827-b2d2-4f27-b220-daa9e1fcdd8d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cdceff5c4e175ba9f135c6e5e4405933b1a86b7c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306893"
---
# <a name="sqlpostinstallererror-function"></a>SQLPostInstallerError 関数
**適合 性**  
 バージョン導入: ODBC 3.0  
  
 **まとめ**  
 **SQLPostInstallerError は**、ドライバーまたはトランスレータセットアップ ライブラリが **、インストーラー**エラー キューに対する**エラーを報告**するメカニズムを提供します。 **ConfigTranslator** アプリケーションはこの API を使用しません。エラーを取得するのに**は、SQLInstaller エラー**を使用します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
RETCODE SQLPostInstallerError(  
     DWORD    fErrorCode,  
     LPSTR    szErrorMsg);  
```  
  
## <a name="arguments"></a>引数  
 *エラーコード*  
 [入力]インストーラのエラー コードです。  
  
 *メッセージ*  
 [入力]エラー メッセージ のテキスト。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESSまたはSQL_ERROR。  
  
## <a name="diagnostics"></a>診断  
 **エラー**値自体をポストしません。 エラーが正常にインストーラ エラー キューにポストされた場合 **(SQLInstallerError**を使用して取得可能)、SQL_SUCCESSが返されます。 SQL_ERRORは *、dwErrorCode*引数の値が指定されたインストーラー エラー コードの 1 つでない場合に返されます。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|ドライバーの追加、変更、または削除|[コンフィグドライバー](../../../odbc/reference/syntax/configdriver-function.md)|  
|データ ソースの追加、変更、または削除|[構成DSN](../../../odbc/reference/syntax/configdsn-function.md)|  
|翻訳オプションの設定|[コンフィグトランスレータ](../../../odbc/reference/syntax/configtranslator-function.md)|
