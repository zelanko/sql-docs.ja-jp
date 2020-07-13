---
title: カーソルの使用 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC cursors, about ODBC cursors
- ODBC applications, cursors
- cursors [ODBC]
- ODBC cursors
ms.assetid: 51322f92-0d76-44c9-9c33-9223676cf1d3
author: rothja
ms.author: jroth
ms.openlocfilehash: 61afedab4f4a1e309a08d9c2421ca7889811da8a
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85020460"
---
# <a name="using-cursors-odbc"></a>カーソルの使用 (ODBC)
  ODBC では、次のことを可能にするカーソル モデルがサポートされます。  
  
-   複数種類のカーソル  
  
-   カーソル内でのスクロールと位置指定  
  
-   複数のコンカレンシー オプション。  
  
-   位置指定更新。  
  
 ODBC アプリケーションでは、カーソルを宣言して開いたり、カーソル関連の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用することはほとんどありません。 ODBC では、SQL ステートメントから返されたすべての結果セットに対して自動的にカーソルを開きます。 カーソルの特性は、SQL ステートメントが実行される前に、 [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)で設定されたステートメント属性によって制御されます。 結果セットの処理に使用する ODBC API 関数では、フェッチ、スクロール、位置指定更新など、すべてのカーソル機能がサポートされます。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトと ODBC アプリケーションのカーソル操作の比較を次に示します。  
  
|アクション|[!INCLUDE[tsql](../../includes/tsql-md.md)]|ODBC|  
|------------|------------------------|----------|  
|カーソル動作を定義する|DECLARE CURSOR パラメーターによる指定|[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)を使用してカーソルの属性を設定する|  
|カーソルを開く|カーソルを開く*cursor_name*を宣言|**SQLExecDirect**または**sqlexecute**|  
|行をフェッチする|FETCH|**Sqlfetch**または[sqlfetchscroll](../native-client-odbc-api/sqlfetchscroll.md)|  
|位置指定更新を行う|UPDATE または DELETE の WHERE CURRENT OF 句|**SQLSetPos**|  
|カーソルを閉じる|割り当て解除*CURSOR_NAME*終了|[SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md)|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に実装されているサーバー カーソルでは、ODBC カーソル モデルの機能がサポートされます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ドライバーでは、サーバー カーソルを使用して ODBC API のカーソル機能がサポートされます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [カーソルの実装方法](implementation/how-cursors-are-implemented.md)  
  
-   [カーソルの種類](cursor-types.md)  
  
-   [カーソル動作](cursor-behaviors.md)  
  
-   [カーソルのプロパティ](properties/cursor-properties.md)  
  
-   [ODBC&#41;&#40;のカーソルプログラミングの詳細](programming/cursor-programming-details-odbc.md)  
  
-   [行のスクロールとフェッチ](../native-client-ole-db-rowsets/fetching-rows.md)  
  
-   [位置指定更新 &#40;ODBC&#41;](positioned-updates-odbc.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)   
 [Transact-sql&#41;を閉じる &#40;](/sql/t-sql/language-elements/close-transact-sql)   
 [求](../../relational-databases/cursors.md)   
 [Transact-sql&#41;の割り当てを解除 &#40;](/sql/t-sql/language-elements/deallocate-transact-sql)   
 [Transact-sql&#41;&#40;カーソルの宣言](/sql/t-sql/language-elements/declare-cursor-transact-sql)   
 [Transact-sql&#41;をフェッチ &#40;](/sql/t-sql/language-elements/fetch-transact-sql)   
 [OPEN &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/open-transact-sql)  
  
  
