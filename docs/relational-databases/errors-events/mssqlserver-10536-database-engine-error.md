---
title: MSSQLSERVER_10536 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 10536 (Database Engine error)
ms.assetid: 9f97b41f-0ef8-4ad2-aec0-906a5d7522ba
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b00f374672490cf9823a3c7700d4ae0e53e18c3f
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver10536"></a>MSSQLSERVER_10536
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|10536|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|PG_TOO_MANY_STMTS|  
|メッセージ テキスト|プラン ガイド '%.\*ls' を作成できません。指定された **@plan_handle** に対応するバッチまたはモジュールに含まれるステートメントが 1000 個を超えています。 バッチまたはモジュール内の各ステートメントに **statement_start_offset** 値を指定して、各ステートメントにプラン ガイドを作成してください。|  
  
## <a name="explanation"></a>説明  
指定された **@plan_handle** に対応するバッチまたはモジュールに含まれるステートメントが 1000 個を超えています。  
  
## <a name="user-action"></a>ユーザーの操作  
バッチまたはモジュール内の各ステートメントに **statement_start_offset** 値を指定して、各ステートメントにプラン ガイドを作成してください。  
  
## <a name="see-also"></a>参照  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[プラン ガイド](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  

