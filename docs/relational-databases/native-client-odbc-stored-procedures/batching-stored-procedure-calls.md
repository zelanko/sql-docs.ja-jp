---
title: ストアド プロシージャの呼び出しをバッチ処理 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], batching
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- batches [ODBC]
- ODBC CALL escape sequence
ms.assetid: b7f53e11-15f0-4602-8134-b166160888f0
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: dbb2279b3a32fd2929a7e9e626a0481ea38fefd0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32943507"
---
# <a name="batching-stored-procedure-calls"></a>ストアド プロシージャ呼び出しのバッチ化
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、ストアド プロシージャの呼び出し時に適切なサーバーを自動的にバッチ処理します。 これが行われるのは、ODBC CALL エスケープ シーケンスが使用されている場合のみです。[!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE ステートメントでは、この処理は行われません。 ストアド プロシージャ呼び出しをバッチにまとめると、サーバーとのやり取りの回数を削減できるので、パフォーマンスが大幅に向上します。  
  
 複数の ODBC CALL エスケープ シーケンスを含むバッチを実行すると、ドライバーによりサーバーへのプロシージャ呼び出しがバッチにまとめられます。 また、ODBC CALL エスケープ シーケンスでバインドされたパラメーター配列を使用するときも、プロシージャ呼び出しがバッチにまとめられます。 たとえば、5 つの要素を含む配列を ODBC CALL SQL ステートメントのパラメーターにバインドするか行方向または列方向のパラメーターのバインドを使用するときに**SQLExecute**または**SQLExecDirect**が呼び出されると、ドライバーは、サーバーに 5 つのプロシージャ呼び出しで 1 つのバッチを送信します。  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャの実行](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
