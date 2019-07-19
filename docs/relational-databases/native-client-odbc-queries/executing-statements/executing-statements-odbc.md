---
title: ステートメントの実行 (ODBC) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC]
- ODBC applications, statements
- statements [ODBC], executing
ms.assetid: 063fc40d-ff81-490d-9c9b-2faefb729f37
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e1c4d892ca25aa2c3bff62ddb5f133f11b952d1d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67937187"
---
# <a name="executing-statements-odbc"></a>ステートメントの実行 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーで SQL ステートメントを実行するさまざまな方法を提供する、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データベース。  
  
-   直接実行  
  
-   準備実行  
  
 直接実行は、含む文字列の構築では、[!INCLUDE[tsql](../../../includes/tsql-md.md)]ステートメントと実行を使用するための送信、 **SQLExecDirect**関数。 準備実行では、[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを含む文字列を作成してから、そのステートメントを 2 段階に分けて実行します。 最初のステージを使用して、 [SQLPrepare 関数](https://go.microsoft.com/fwlink/?LinkId=59360)を解析およびコンパイルでステートメントの実行プランの関数、[!INCLUDE[ssDE](../../../includes/ssde-md.md)]します。 2 番目の段階を使用して、 **SQLExecute**関数を事前に準備された実行プランを実行します。 この方法では、各実行にかかる解析とコンパイルのオーバーヘッドが抑制されます。 準備実行は、通常、同一のパラメーター化された SQL ステートメントを繰り返し実行するアプリケーションで使用されます。  
  
 どちらの実行方法でも、[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントまたは SQL ステートメントのバッチを 1 つ実行でき、ステートメントからストアド プロシージャを呼び出すことができます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [直接実行](../../../relational-databases/native-client-odbc-queries/executing-statements/direct-execution.md)  
  
-   [準備実行](../../../relational-databases/native-client-odbc-queries/executing-statements/prepared-execution.md)  
  
-   [手順](../../../relational-databases/native-client-odbc-queries/executing-statements/procedures.md)  
  
-   [ステートメントのバッチ](../../../relational-databases/native-client-odbc-queries/executing-statements/batches-of-statements.md)  
  
-   [ISO オプションの効果](../../../relational-databases/native-client-odbc-queries/executing-statements/effects-of-iso-options.md)  
  
## <a name="see-also"></a>関連項目  
 [クエリの実行&#40;ODBC&#41;](../../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
