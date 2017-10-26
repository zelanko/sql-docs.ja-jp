---
title: MSSQLSERVER_10521 | Microsoft Docs
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
- 10521 (Database Engine error)
ms.assetid: ba2d7e44-207c-4428-b5f0-c975ac122c0d
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: e6060201dd4211266a0dcbf874826f6c8ef18d70
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver10521"></a>MSSQLSERVER_10521
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|10521|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|PG_PARAM_NEEDED|  
|メッセージ テキスト|プラン ガイド '%.\*ls' を作成できません。'%ls' として指定した **@type** のパラメーターが NULL です。 この型のパラメーターには、NULL 以外の値を指定する必要があります。 NULL 以外の値をパラメーターに指定するか、パラメーターに NULL 値を指定可能な型に変更します。|  
  
## <a name="explanation"></a>説明  
**@type** で指定した型のパラメーターには、NULL 以外の値を指定する必要がありますが、NULL 値を指定しました。  
  
## <a name="user-action"></a>ユーザーの操作  
NULL 以外の値をパラメーターに指定するか、パラメーターに NULL 値を指定可能な型に変更します。  
  
## <a name="see-also"></a>参照  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[プラン ガイド](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  

