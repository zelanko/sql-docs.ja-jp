---
title: MSSQLSERVER_10532 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 10532 (Database Engine error)
ms.assetid: 01da29ee-bf67-433f-8148-587a7e8d1d76
caps.latest.revision: "9"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: c7160413790d9bc783aac1eb517cb9afd1fa297b
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver10532"></a>MSSQLSERVER_10532
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|10532|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|PG_NO_ELIGIBLE_STMT|  
|メッセージ テキスト|プラン ガイド '%.\*ls' を作成できません。**@plan_handle** で指定されたバッチまたはモジュールに、プラン ガイドに適したステートメントが含まれていません。 **@plan_handle** に別の値を指定します。|  
  
## <a name="explanation"></a>説明  
**@plan_handle** で指定されたバッチまたはモジュールに、プラン ガイドに適したステートメントが含まれていません。  
  
## <a name="user-action"></a>ユーザーの操作  
**@plan_handle** に別の値を指定します。  
  
## <a name="see-also"></a>参照  
[プラン ガイド](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
