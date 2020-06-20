---
title: ストアドプロシージャ呼び出しのバッチ化 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], batching
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- batches [ODBC]
- ODBC CALL escape sequence
ms.assetid: b7f53e11-15f0-4602-8134-b166160888f0
author: rothja
ms.author: jroth
ms.openlocfilehash: a0df58ce59853ee15b863cbc7bce34041c37fee4
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85039510"
---
# <a name="batching-stored-procedure-calls"></a>ストアド プロシージャ呼び出しのバッチ化
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーでは、必要に応じてストアドプロシージャの呼び出しがサーバーに自動的にバッチ処理されます。 これが行われるのは、ODBC CALL エスケープ シーケンスが使用されている場合のみです。[!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE ステートメントでは、この処理は行われません。 ストアド プロシージャ呼び出しをバッチにまとめると、サーバーとのやり取りの回数を削減できるので、パフォーマンスが大幅に向上します。  
  
 複数の ODBC CALL エスケープ シーケンスを含むバッチを実行すると、ドライバーによりサーバーへのプロシージャ呼び出しがバッチにまとめられます。 また、ODBC CALL エスケープ シーケンスでバインドされたパラメーター配列を使用するときも、プロシージャ呼び出しがバッチにまとめられます。 たとえば、行方向または列方向のいずれかのパラメーターバインドを使用して、5つの要素を持つ配列を ODBC CALL SQL ステートメントのパラメーターにバインドする場合、 **Sqlexecute**または**SQLExecDirect**が呼び出されると、ドライバーは5つのプロシージャ呼び出しを含む単一のバッチをサーバーに送信します。  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャの実行](running-stored-procedures.md)  
  
  
