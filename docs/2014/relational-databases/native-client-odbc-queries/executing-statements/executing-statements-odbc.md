---
title: ステートメントの実行 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC]
- ODBC applications, statements
- statements [ODBC], executing
ms.assetid: 063fc40d-ff81-490d-9c9b-2faefb729f37
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a367d5ee7def19ffdfd40e24860ebf95f642fae9
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82700426"
---
# <a name="executing-statements-odbc"></a>ステートメントの実行 (ODBC)
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーには、データベース内で SQL ステートメントを実行するためのさまざまな方法が用意されてい [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。  
  
-   直接実行  
  
-   準備実行  
  
 直接実行では、ステートメントを含む文字列を作成 [!INCLUDE[tsql](../../../includes/tsql-md.md)] し、 **SQLExecDirect**関数を使用して実行するために送信します。 準備実行では、[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを含む文字列を作成してから、そのステートメントを 2 段階に分けて実行します。 最初の段階では、 [SQLPrepare 関数](https://go.microsoft.com/fwlink/?LinkId=59360)関数を使用して、のステートメントの実行プランを解析およびコンパイルし [!INCLUDE[ssDE](../../../includes/ssde-md.md)] ます。 2番目の段階では、 **Sqlexecute**関数を使用して、事前に準備された実行プランを実行します。 この方法では、各実行にかかる解析とコンパイルのオーバーヘッドが抑制されます。 準備実行は、通常、同一のパラメーター化された SQL ステートメントを繰り返し実行するアプリケーションで使用されます。  
  
 どちらの実行方法でも、[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントまたは SQL ステートメントのバッチを 1 つ実行でき、ステートメントからストアド プロシージャを呼び出すことができます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [直接実行](direct-execution.md)  
  
-   [準備実行](prepared-execution.md)  
  
-   [手順](procedures.md)  
  
-   [ステートメントのバッチ](batches-of-statements.md)  
  
-   [ISO オプションの効果](effects-of-iso-options.md)  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;クエリの実行](../executing-queries-odbc.md)  
  
  
