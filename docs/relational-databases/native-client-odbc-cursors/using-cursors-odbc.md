---
title: カーソルの使用 (ODBC) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: be512713462a9518856de2a16db749490ea24366
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306313"
---
# <a name="using-cursors-odbc"></a>カーソルの使用 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ODBC では、次のことを可能にするカーソル モデルがサポートされます。  
  
-   複数種類のカーソル  
  
-   カーソル内でのスクロールと位置指定  
  
-   複数のコンカレンシー オプション。  
  
-   位置指定更新。  
  
 ODBC アプリケーションでは、カーソルを宣言して開いたり、カーソル関連の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用することはほとんどありません。 ODBC では、SQL ステートメントから返されたすべての結果セットに対して自動的にカーソルを開きます。 カーソルの特性は、SQL ステートメントが実行される前に[SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)で設定されたステートメント属性によって制御されます。 結果セットの処理に使用する ODBC API 関数では、フェッチ、スクロール、位置指定更新など、すべてのカーソル機能がサポートされます。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトと ODBC アプリケーションのカーソル操作の比較を次に示します。  
  
|アクション|[!INCLUDE[tsql](../../includes/tsql-md.md)]|ODBC|  
|------------|------------------------|----------|  
|カーソル動作を定義する|DECLARE CURSOR パラメーターによる指定|カーソル属性を設定するには[、SQLSetStmtAttr を使用します。](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)|  
|カーソルを開く|カーソルを開く*cursor_name*宣言|**または**SQL**実行**|  
|行をフェッチする|FETCH|**SQL フェッチ**または[SQL フェッチスクロール](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)|  
|位置指定更新を行う|UPDATE または DELETE の WHERE CURRENT OF 句|**SQLSetPos**|  
|カーソルを閉じる|割り当て解除*cursor_name*クローズ|[SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md)|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に実装されているサーバー カーソルでは、ODBC カーソル モデルの機能がサポートされます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ドライバーでは、サーバー カーソルを使用して ODBC API のカーソル機能がサポートされます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [カーソルの実装方法](../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
-   [カーソルの種類](../../relational-databases/native-client-odbc-cursors/cursor-types.md)  
  
-   [カーソル動作](../../relational-databases/native-client-odbc-cursors/cursor-behaviors.md)  
  
-   [カーソルのプロパティ](../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
-   [ODBC&#41;&#40;カーソル プログラミングの詳細](../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
-   [行のスクロールとフェッチ](../../relational-databases/native-client-odbc-cursors/scrolling-and-fetching-rows.md)  
  
-   [ODBC&#41;&#40;位置指定更新](../../relational-databases/native-client-odbc-cursors/positioned-updates-odbc.md)  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;SQL Server ネイティブ クライアント](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [決算&#40;SQL&#41;](../../t-sql/language-elements/close-transact-sql.md)   
 [カーソル](../../relational-databases/cursors.md)   
 [トランザクション SQL&#41;&#40;割り当て解除](../../t-sql/language-elements/deallocate-transact-sql.md)   
 [カーソル&#40;の宣言&#41;](../../t-sql/language-elements/declare-cursor-transact-sql.md)   
 [トランザクション SQL&#41;&#40;フェッチ](../../t-sql/language-elements/fetch-transact-sql.md)   
 [OPEN &#40;Transact-SQL&#41;](../../t-sql/language-elements/open-transact-sql.md)  
  
  
