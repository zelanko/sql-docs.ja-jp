---
title: ストアド プロシージャの呼び出しをバッチ処理 |Microsoft ドキュメント
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
- stored procedures [ODBC], batching
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- batches [ODBC]
- ODBC CALL escape sequence
ms.assetid: b7f53e11-15f0-4602-8134-b166160888f0
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fd3d7fca3dc22d20c9aeadfc3b60fa41fa64f895
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083408"
---
# <a name="batching-stored-procedure-calls"></a>ストアド プロシージャ呼び出しのバッチ化
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、ストアド プロシージャの呼び出し時に適切なサーバーを自動的にバッチ処理します。 これが行われるのは、ODBC CALL エスケープ シーケンスが使用されている場合のみです。[!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE ステートメントでは、この処理は行われません。 ストアド プロシージャ呼び出しをバッチにまとめると、サーバーとのやり取りの回数を削減できるので、パフォーマンスが大幅に向上します。  
  
 複数の ODBC CALL エスケープ シーケンスを含むバッチを実行すると、ドライバーによりサーバーへのプロシージャ呼び出しがバッチにまとめられます。 また、ODBC CALL エスケープ シーケンスでバインドされたパラメーター配列を使用するときも、プロシージャ呼び出しがバッチにまとめられます。 たとえば、5 つの要素を含む配列を ODBC CALL SQL ステートメントのパラメーターにバインドするか行方向または列方向のパラメーターのバインドを使用するときに**SQLExecute**または**SQLExecDirect**が呼び出されると、ドライバーは、サーバーに 5 つのプロシージャ呼び出しで 1 つのバッチを送信します。  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャの実行](running-stored-procedures.md)  
  
  