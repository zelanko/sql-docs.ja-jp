---
title: SQLSetPos の呼び出し |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 70d574f867934af87ac7b5071b7f30bc9e89bccf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47616060"
---
# <a name="calling-sqlsetpos"></a>SQLSetPos の呼び出し
ODBC 2。*x*、行の状態配列へのポインターが引数**SQLExtendedFetch**します。 行の状態配列への呼び出しによって更新された後で**SQLSetPos**します。 一部のドライバーがこの配列の間で変更しないという事実に依存していました**SQLExtendedFetch**と**SQLSetPos**します。 ODBC 3。*x*状態配列へのポインターは、記述子フィールド、および、そのため、変えることができます簡単に別の配列を指すようにします。 これは、問題と、ODBC 3 です。*x* ODBC 2 を利用するアプリケーション *。x*ドライバーは呼び出すことが**SQLSetStmtAttr**配列状態のポインターを設定して呼び出しは**SQLFetchScroll**データをフェッチします。 ドライバー マネージャーがへの呼び出しのシーケンスとしてマップ**SQLExtendedFetch**します。 次のコードでは、エラーは通常するときに発生ドライバー マネージャーは、2 つ目のマップ**SQLSetStmtAttr** ODBC 2 を使用するときに呼び出す *.x*ドライバー。  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStatus, 0);  
SQLFetchScroll(hstmt, fFetchType, iRow);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStat1, 0);  
SQLSetPos(hstmt, iRow, fOption, fLock);  
```  
  
 ODBC 2 行の状態のポインターを変更する方法がない場合、エラーが生成されます。*x*呼び出しの間で**SQLExtendedFetch**します。 ODBC 2 を使用する場合に、ドライバー マネージャーが、次の手順を実行する代わりに、*.x*ドライバー。  
  
1.  内部のドライバー マネージャーのフラグを初期化します*fSetPosError*を TRUE にします。  
  
2.  アプリケーションを呼び出すと**SQLFetchScroll**、ドライバー マネージャーの設定*fSetPosError*を FALSE にします。  
  
3.  アプリケーションを呼び出すと**SQLSetStmtAttr**ドライバー マネージャーを設定し、SQL_ATTR_ROW_STATUS_PTR を設定する*fSetPosError*と等しい値を True です。  
  
4.  アプリケーションを呼び出すと**SQLSetPos**で*fSetPosError* true の場合、ドライバー マネージャーと等しい SQLSTATE HY011 SQL_ERROR を発生させます (属性はここで設定することはできません) ことを示すアプリケーション呼び出すしようとしています。 **SQLSetPos**行の状態のポインターを変更した後は、呼び出す前に**SQLFetchScroll**します。
