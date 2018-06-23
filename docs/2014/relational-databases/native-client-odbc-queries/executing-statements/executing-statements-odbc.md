---
title: ステートメント (ODBC) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC]
- ODBC applications, statements
- statements [ODBC], executing
ms.assetid: 063fc40d-ff81-490d-9c9b-2faefb729f37
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ff5f9dcc3d8087418e3003dedc7f57e56840cba0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165550"
---
# <a name="executing-statements-odbc"></a>ステートメントの実行 (ODBC)
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーで SQL ステートメントを実行するさまざまな方法を提供する、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データベース。  
  
-   直接実行  
  
-   準備実行  
  
 直接実行は、文字を含む文字列の構築では、[!INCLUDE[tsql](../../../includes/tsql-md.md)]ステートメントと実行を使用するための送信、 **SQLExecDirect**関数。 準備実行では、[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを含む文字列を作成してから、そのステートメントを 2 段階に分けて実行します。 最初のステージを使用して、 [SQLPrepare 関数](http://go.microsoft.com/fwlink/?LinkId=59360)を解析および内のステートメントの実行プランをコンパイルする関数、[!INCLUDE[ssDE](../../../includes/ssde-md.md)]です。 2 番目の段階を使用して、 **SQLExecute**関数を事前に準備された実行プランを実行します。 この方法では、各実行にかかる解析とコンパイルのオーバーヘッドが抑制されます。 準備実行は、通常、同一のパラメーター化された SQL ステートメントを繰り返し実行するアプリケーションで使用されます。  
  
 どちらの実行方法でも、[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントまたは SQL ステートメントのバッチを 1 つ実行でき、ステートメントからストアド プロシージャを呼び出すことができます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [直接実行](direct-execution.md)  
  
-   [準備実行](prepared-execution.md)  
  
-   [手順](procedures.md)  
  
-   [ステートメントのバッチ](batches-of-statements.md)  
  
-   [ISO オプションの効果](effects-of-iso-options.md)  
  
## <a name="see-also"></a>参照  
 [クエリを実行する&#40;ODBC&#41;](../executing-queries-odbc.md)  
  
  