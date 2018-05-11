---
title: MSSQLSERVER_10519 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 10519 (Database Engine error)
ms.assetid: 3be393a1-b186-41ae-afb9-a3d07ff354bb
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a7169ed83c3f602a17994e023d1da8ba5c17f94b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver10519"></a>MSSQLSERVER_10519
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|10519|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|PG_INCOMPATIBLE_STMT_AND_HINTS|  
|メッセージ テキスト|プラン ガイド '%.\*ls' を作成できません。**@hints** で指定されたヒントを、**@stmt** または **@statement_start_offset** のいずれかで指定されたステートメントに適用できません。 ヒントがステートメントに適用可能であることを確認してください。|  
  
## <a name="explanation"></a>説明  
**@hints** で指定されたヒントを、**@stmt** または **@statement_start_offset** のいずれかで指定されたステートメントに適用できません。  
  
## <a name="user-action"></a>ユーザーの操作  
ステートメントに適用できるヒントを指定します。  
  
## <a name="see-also"></a>参照  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[プラン ガイド](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
