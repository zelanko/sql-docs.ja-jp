---
title: "SQLSetPos を呼び出して |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- compatibility [ODBC], SQLSetPos
- SQLSetPos function [ODBC], calling
- upgrading applications [ODBC], SQLSetPos
- backward compatibility [ODBC], SqlSetPos
- application upgrades [ODBC], SQLSetPos
ms.assetid: 846354b8-966c-4c2c-b32f-b0c8e649cedd
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 434031a496faae19ee37b8273341cc0ede6d0313
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="calling-sqlsetpos"></a>SQLSetPos を呼び出す
ODBC 2 です。*x*、行の状態配列へのポインターが引数**SQLExtendedFetch**です。 行の状態配列への呼び出しによって更新された後で**SQLSetPos**です。 一部のドライバーがこの配列は間変更されないという事実に依存していました**SQLExtendedFetch**と**SQLSetPos**です。 ODBC 3 です。*x*状態配列へのポインターが記述子フィールド、および、したがってアプリケーション簡単に変更し、別の配列を指すようにします。 これは、とき、ODBC 3 問題となることができます。*x* ODBC 2 を利用するアプリケーション*。x*ドライバーを呼び出すが、 **SQLSetStmtAttr**配列状態のポインターを設定して呼び出しは**SQLFetchScroll**データをフェッチします。 ドライバー マネージャーがへの呼び出しのシーケンスとしてマップ**SQLExtendedFetch**です。 次のコードでは、エラーは通常と発生ドライバー マネージャーは、2 つ目のマップ**SQLSetStmtAttr** ODBC 2 を操作するときに呼び出す*.x*ドライバー。  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStatus, 0);  
SQLFetchScroll(hstmt, fFetchType, iRow);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStat1, 0);  
SQLSetPos(hstmt, iRow, fOption, fLock);  
```  
  
 エラーは ODBC 2 行の状態のポインターを変更する方法がない場合に生成されます。*x*呼び出しの間**SQLExtendedFetch**です。 ODBC 2 を使用する場合に、ドライバー マネージャーが、次の手順を実行する代わりに、*.x*ドライバー。  
  
1.  内部のドライバー マネージャーのフラグを初期化します*fSetPosError* TRUE に設定します。  
  
2.  アプリケーションを呼び出すと**SQLFetchScroll**、ドライバー マネージャーの設定*fSetPosError*を FALSE にします。  
  
3.  アプリケーションを呼び出すと**SQLSetStmtAttr**ドライバー マネージャーの設定を SQL_ATTR_ROW_STATUS_PTR を設定するには、 *fSetPosError*と等しい値を True です。  
  
4.  アプリケーションを呼び出すと**SQLSetPos**で*fSetPosError* SQLSTATE HY011 の SQL_ERROR が true の場合、ドライバー マネージャーに等しいかどうかを発生させます (属性はここで設定することはできません) ことを示すアプリケーション呼び出そうとしました**SQLSetPos**行の状態のポインターを変更した後、呼び出しの前に**SQLFetchScroll**です。

