---
title: トレースの削除 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], deleting
- removing traces
- deleting traces
ms.assetid: a5502814-b281-42dd-b885-5c9368025ae6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1262232a7fdc42c443f624aca8334dce1e48a3f9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48055652"
---
# <a name="delete-a-trace-transact-sql"></a>トレースの削除 (Transact-SQL)
  このトピックでは、ストアド プロシージャを使用してトレースを削除する方法について説明します。  
  
 トレース ストアド プロシージャを使用した例については、「[トレースの作成 &#40;Transact-SQL&#41;](create-a-trace-transact-sql.md)」を参照してください。  
  
### <a name="to-delete-a-trace"></a>トレースを削除するには  
  
1.  **@status = 0** を指定して **sp_trace_setstatus** を実行し、トレースを停止します。  
  
2.  **@status = 2** を指定して **sp_trace_setstatus** を実行し、トレースを閉じてトレースの情報をサーバーから削除します。  
  
> [!NOTE]  
>  トレースを閉じるには、最初にそのトレースを停止する必要があります。  
  
## <a name="see-also"></a>参照  
 [sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql)   
 [SQL Server Profiler のストアド プロシージャ &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
