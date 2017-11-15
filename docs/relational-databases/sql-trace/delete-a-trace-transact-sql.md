---
title: "トレースの削除 (Transact-SQL) | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- traces [SQL Server], deleting
- removing traces
- deleting traces
ms.assetid: a5502814-b281-42dd-b885-5c9368025ae6
caps.latest.revision: "22"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 452a97ef67be15e2551ce238a3ea37c08998798e
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="delete-a-trace-transact-sql"></a>トレースの削除 (Transact-SQL)
  このトピックでは、ストアド プロシージャを使用してトレースを削除する方法について説明します。  
  
 トレース ストアド プロシージャを使用した例については、「[トレースの作成 &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)」を参照してください。  
  
### <a name="to-delete-a-trace"></a>トレースを削除するには  
  
1.  **@status = 0** を指定して **sp_trace_setstatus** を実行し、トレースを停止します。  
  
2.  **@status = 2** を指定して **sp_trace_setstatus** を実行し、トレースを閉じてトレースの情報をサーバーから削除します。  
  
> [!NOTE]  
>  トレースを閉じるには、最初にそのトレースを停止する必要があります。  
  
## <a name="see-also"></a>参照  
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [SQL Server Profiler のストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)  
  
  
