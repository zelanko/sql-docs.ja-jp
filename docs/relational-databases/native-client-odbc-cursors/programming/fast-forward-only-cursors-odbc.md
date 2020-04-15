---
title: 高速転送専用カーソル (ODBC) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fast forward-only cursors
- forward-only cursors
- cursors [ODBC], fast forward-only
- ODBC cursors, fast forward-only
ms.assetid: 0707d07e-fc95-42ed-9280-b7e508ac8c62
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 50d79875e0f3f661c0a959f50ce68c4f2761d186
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298422"
---
# <a name="fast-forward-only-cursors-odbc"></a>高速順方向専用カーソル (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のインスタンスに接続すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバーは、前方の読み取り専用カーソルのパフォーマンスの最適化をサポートします。 高速順方向専用カーソルは、既定の結果セットに類似した方法で、ドライバーとサーバーによって内部的に実装されます。 高速順方向専用カーソルには、パフォーマンスが高いこと以外にも、次のような特性があります。  
  
-   [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md)はサポートされていません。 結果セットの列を、プログラム変数にバインドする必要があります。  
  
-   サーバーはカーソルの最後に達したことを検出すると、そのカーソルを自動的に閉じます。 アプリケーションは引き続き[SQLCloseCursor](../../../relational-databases/native-client-odbc-api/sqlclosecursor.md)または[SQLFreeStmt](../../../relational-databases/native-client-odbc-api/sqlfreestmt.md)(SQL_CLOSE) を呼び出す必要がありますが、ドライバーはサーバーにクローズ要求を送信する必要はありません。 この動作により、ネットワーク経由でのサーバーとのやり取りが抑えられます。  
  
 アプリケーションでは、ドライバー固有のステートメント属性 SQL_SOPT_SS_CURSOR_OPTIONS を使用して高速順方向専用カーソルを要求します。 SQL_SOPT_SS_CURSOR_OPTIONS 属性に SQL_CO_FFO を設定すると、高速順方向専用カーソルが有効になりますが、autofetch オプションは有効になりません。 SQL_CO_FFO_AF を設定すると、autofetch オプションも有効になります。 自動フェッチの詳細については[、「ODBC カーソルでの自動フェッチの使用](../../../relational-databases/native-client-odbc-cursors/programming/using-autofetch-with-odbc-cursors.md)」を参照してください。  
  
 autofetch オプションを有効にした高速順方向専用カーソルは、サーバーとのやり取りを 1 度だけ行って小さい結果セットを取得する場合に使用できます。 次の手順では *、n*は返される行数です。  
  
1.  SQL_SOPT_SS_CURSOR_OPTIONS を SQL_CO_FFO_AF に設定します。  
  
2.  SQL_ATTR_ROW_ARRAY_SIZEを*n* + 1 に設定します。  
  
3.  結果列を*n* + 1 要素の配列にバインドします *(n* + 1 行が実際にフェッチされた場合に安全です)。  
  
4.  カーソルを開くには **、SQLExecDirect**または**SQLExecute**のいずれかを指定します。  
  
5.  戻り状況がSQL_SUCCESS場合は **、SQLFreeStmt**または**SQLCloseCursor**を呼び出してカーソルをクローズします。 行のすべてのデータが、バインドされたプログラム変数に格納されます。  
  
 これらの手順では **、SQLExecDirect**または**SQLExecute は**、自動フェッチ オプションを有効にしてカーソルオープン要求を送信します。 クライアントからこの要求を 1 つ受け取ると、サーバーでは次の手順が実行されます。  
  
-   カーソルを開きます。  
  
-   結果セットを作成してクライアントに行を送信します。  
  
-   行セットのサイズを結果セットの行数よりも 1 だけ多いサイズに設定したので、サーバーでカーソルが最後まで達したことが検出され、そのカーソルが閉じられます。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;カーソル プログラミングの詳細](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
