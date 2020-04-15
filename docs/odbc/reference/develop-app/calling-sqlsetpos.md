---
title: を呼び出す |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], SQLSetPos
- SQLSetPos function [ODBC], calling
- upgrading applications [ODBC], SQLSetPos
- backward compatibility [ODBC], SqlSetPos
- application upgrades [ODBC], SQLSetPos
ms.assetid: 846354b8-966c-4c2c-b32f-b0c8e649cedd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 46cfbb4e2e6b60f620cd7e38272bf9308ece91bc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306243"
---
# <a name="calling-sqlsetpos"></a>SQLSetPos の呼び出し
ODBC *2.x*では、行の状態配列へのポインターは **、SQLExtendedFetch**への引数でした。 行の状態の配列は、後で**SQLSetPos**の呼び出しによって更新されました。 一部のドライバーは、この配列は**SQLExtendedFetch**と**SQLSetPos**の間で変更されないという事実に依存しています。 ODBC *3.x*では、ステータス配列へのポインタは記述子フィールドであるため、アプリケーションは簡単に別の配列を指すに変更できます。 ODBC *3.x*アプリケーションが ODBC *2.x*ドライバーを使用して作業しているが、配列の状態ポインターを設定するために**SQLSetStmtAttr**を呼び出していて、SQLFetchScroll を呼び出してデータをフェッチする場合、これは問題になる可能性があります。 **SQLFetchScroll** ドライバー マネージャーは、呼び出しのシーケンスとしてマップ**SQLExtendedFetch**. 次のコードでは、通常、ODBC *2.x*ドライバーを操作するときにドライバー マネージャーが 2 番目の**SQLSetStmtAttr**呼び出しをマップするときにエラーが発生します。  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStatus, 0);  
SQLFetchScroll(hstmt, fFetchType, iRow);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStat1, 0);  
SQLSetPos(hstmt, iRow, fOption, fLock);  
```  
  
 **SQLExtendedFetch**の呼び出しの間に ODBC *2.x*の行の状態ポインターを変更する方法がない場合、エラーが発生します。 代わりに、ドライバー マネージャーは、ODBC *2.x*ドライバーを操作するときに、次の手順を実行します。  
  
1.  内部ドライバー マネージャー フラグ*fSetPosError*を TRUE に初期化します。  
  
2.  アプリケーションが呼び出すとき**SQLFetchScroll**ドライバー マネージャーは、false に*fSetPos エラー*を設定します。  
  
3.  アプリケーションがSQL_ATTR_ROW_STATUS_PTRを設定するために**SQLSetStmtAttr**を呼び出すと、ドライバー マネージャーは*fSetPosError*を TRUE に設定します。  
  
4.  アプリケーションが**SQLSetPos**を呼び出すときに *、fSetPosError*が TRUE の場合、ドライバー マネージャーは SQLSTATE HY011 (属性を今設定できません) でSQL_ERRORを発生させるし、アプリケーションが行の状態ポインターを変更した後に**SQLFetchScroll**を呼び出す前に**SQLSetPos**を呼び出そうとしたことを示します。
