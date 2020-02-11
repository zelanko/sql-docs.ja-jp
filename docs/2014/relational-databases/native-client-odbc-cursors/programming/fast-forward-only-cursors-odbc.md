---
title: 高速順方向専用カーソル (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fast forward-only cursors
- forward-only cursors
- cursors [ODBC], fast forward-only
- ODBC cursors, fast forward-only
ms.assetid: 0707d07e-fc95-42ed-9280-b7e508ac8c62
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: df3cea50a8800cdca7fe0a5c846bc32556299e0c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63209788"
---
# <a name="fast-forward-only-cursors-odbc"></a>高速順方向専用カーソル (ODBC)
  Native Client ODBC ドライバーは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のインスタンス[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]に接続されている場合、順方向専用の読み取り専用カーソルのパフォーマンスの最適化をサポートしています。 高速順方向専用カーソルは、既定の結果セットに類似した方法で、ドライバーとサーバーによって内部的に実装されます。 高速順方向専用カーソルには、パフォーマンスが高いこと以外にも、次のような特性があります。  
  
-   [SQLGetData](../../native-client-odbc-api/sqlgetdata.md)はサポートされていません。 結果セットの列を、プログラム変数にバインドする必要があります。  
  
-   サーバーはカーソルの最後に達したことを検出すると、そのカーソルを自動的に閉じます。 アプリケーションは引き続き[SqlcloSQLFreeStmt](../../native-client-odbc-api/sqlclosecursor.md)または[](../../native-client-odbc-api/sqlfreestmt.md)(SQL_CLOSE) を呼び出す必要がありますが、ドライバーからサーバーにクローズ要求を送信する必要はありません。 この動作により、ネットワーク経由でのサーバーとのやり取りが抑えられます。  
  
 アプリケーションでは、ドライバー固有のステートメント属性 SQL_SOPT_SS_CURSOR_OPTIONS を使用して高速順方向専用カーソルを要求します。 SQL_SOPT_SS_CURSOR_OPTIONS 属性に SQL_CO_FFO を設定すると、高速順方向専用カーソルが有効になりますが、autofetch オプションは有効になりません。 SQL_CO_FFO_AF を設定すると、autofetch オプションも有効になります。 Autofetch の詳細については、「 [Using autofetch WITH ODBC](using-autofetch-with-odbc-cursors.md)cursor」を参照してください。  
  
 autofetch オプションを有効にした高速順方向専用カーソルは、サーバーとのやり取りを 1 度だけ行って小さい結果セットを取得する場合に使用できます。 次の手順では、 *n*が返される行の数を示します。  
  
1.  SQL_SOPT_SS_CURSOR_OPTIONS を SQL_CO_FFO_AF に設定します。  
  
2.  SQL_ATTR_ROW_ARRAY_SIZE を*n* + 1 に設定します。  
  
3.  結果列を*n* + 1 個の要素の配列にバインドします ( *n* + 1 行が実際にフェッチされた場合は安全です)。  
  
4.  **SQLExecDirect**または**sqlexecute**のいずれかを使用してカーソルを開きます。  
  
5.  返された状態が SQL_SUCCESS の場合は、 **SQLFreeStmt**または**sqlcloを**呼び出してカーソルを閉じます。 行のすべてのデータが、バインドされたプログラム変数に格納されます。  
  
 これらの手順で、 **SQLExecDirect**または**sqlexecute**は、autofetch オプションが有効になっている状態で、cursor open 要求を送信します。 クライアントからこの要求を 1 つ受け取ると、サーバーでは次の手順が実行されます。  
  
-   カーソルを開きます。  
  
-   結果セットを作成してクライアントに行を送信します。  
  
-   行セットのサイズを結果セットの行数よりも 1 だけ多いサイズに設定したので、サーバーでカーソルが最後まで達したことが検出され、そのカーソルが閉じられます。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;のカーソルプログラミングの詳細](cursor-programming-details-odbc.md)  
  
  
