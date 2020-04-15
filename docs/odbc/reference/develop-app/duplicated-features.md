---
title: 複製された機能 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- duplicated functions [ODBC]
- compatibility [ODBC], duplicated functions
- ODBC drivers [ODBC], backward compatibility
- functions [ODBC], duplicated functions
- backward compatibility [ODBC], duplicated functions
ms.assetid: 641b16bc-f791-46d8-b093-31736473fe3d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 00f5529cfbfacebcad78a0a4433e84f34034694a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300482"
---
# <a name="duplicated-features"></a>重複する機能
次の ODBC *2.x*関数は、ODBC *3.x*関数によって重複しています。 その結果、ODBC *2.x*関数は ODBC *3.x*では使用されなくなりました。 ODBC *3.x*関数は置換関数と呼ばれます。  
  
 アプリケーションが非推奨の ODBC *2.x*関数を使用し、基になるドライバーが ODBC *3.x*ドライバーである場合、ドライバー マネージャーは、対応する置換関数に関数呼び出しをマップします。 このルールの唯一の例外は**SQLExtendedFetch**です。 (次の表の最後にある脚注を参照してください。これらのマッピングの詳細については、「付録 G: 下位互換性のためのドライバーのガイドライン」の[「非推奨関数のマッピング](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)」を参照してください。  
  
 アプリケーションが置換関数を使用し、基になるドライバーが ODBC *2.x*ドライバーである場合、ドライバー マネージャーは、対応する非推奨関数に関数呼び出しをマップします。  
  
|ODBC *2.x*関数|ODBC *3.x*関数|  
|-------------------------|-------------------------|  
|**コネクト**|**ハンドル**|  
|**SQLAllocEnv**|**ハンドル**|  
|**をクリックします。**|**ハンドル**|  
|**属性**|**SQLColAttribute**|  
|**エラー**|**SQLGetDiagRec**|  
|**クエリの実行**|**SQLFetchScroll**|  
|**コネクト**|**SQLFreeHandle**|  
|**を実行する**|**SQLFreeHandle**|  
|**オプションを指定します。**|**SQLGetConnectAttr**|  
|**オプションを指定します。**|**SQLGetStmtAttr**|  
|**オプション**|**を**使用**します。**|  
|**オプションを指定します。**|**SQLSetConnectAttr**|  
|**を使用する**|**SQLBindParameter**|  
|**オプションを設定します。**|**SQLSetStmtAttr**|  
|**トランスアクト**|**SQLEndTran**|  
  
 関数**SQLExtendedFetch**が重複した機能です。**SQL フェッチスクロール**は、ODBC *3.x*で同じ機能を提供します。 ただし、ドライバー マネージャーは、ODBC *3.x*ドライバーに対して行うときに**SQLExtendedFetch**を**SQLFetchScroll**にマップしません。 詳細については、「付録 G: 下位互換性[のためのドライバー](../../../odbc/reference/appendixes/what-the-driver-manager-does.md)のガイドライン」の「ドライバー マネージャーの動作」を参照してください。 ドライバー マネージャーは **、ODBC** *2.x*ドライバーに対して行くときに SQL フェッチスクロールを**SQLExtendedFetch**にマップします。  
  
> [!NOTE]
>  関数**SQLBindParam**は特殊なケースです。 **機能が**重複しています。 これは ODBC *2.x*関数ではなく、オープン グループおよび ISO 標準に存在する関数です。 この関数によって提供される機能は **、SQLBindParameter**の機能によって完全に使用されます。 その結果、ドライバー マネージャーは、基になるドライバーが ODBC *3.x*ドライバーである場合に**SQLBindParam**への呼び出しを**SQLBind パラメーター**にマップします。 ただし、基になるドライバーが ODBC *2.x*ドライバーの場合、ドライバー マネージャーは、このマッピングを実行しません。
