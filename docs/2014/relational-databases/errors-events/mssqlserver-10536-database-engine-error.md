---
title: MSSQLSERVER_10536 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10536 (Database Engine error)
ms.assetid: 9f97b41f-0ef8-4ad2-aec0-906a5d7522ba
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b8c4e7237aa7ea39673b62543d77f9796c5bc46a
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86554107"
---
# <a name="mssqlserver_10536"></a>MSSQLSERVER_10536
    
## <a name="details"></a>詳細  
  
|属性|値|  
|-|-|  
|製品名|SQL Server|  
|イベント ID|10536|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|PG_TOO_MANY_STMTS|  
|メッセージ テキスト|プラン ガイド '%.\*ls' を作成できません。指定された `@plan_handle` に対応するバッチまたはモジュールに含まれるステートメントが 1000 個を超えています。 バッチまたはモジュールの各ステートメントに対して `statement_start_offset` 値を指定して、ステートメントごとにプラン ガイドを作成します。|  
  
## <a name="explanation"></a>説明  
 指定した `@plan_handle` に対応するバッチまたはモジュールに、条件を満たすステートメントが 1000 以上含まれています。  
  
## <a name="user-action"></a>ユーザーの操作  
 バッチまたはモジュールの各ステートメントに対して `statement_start_offset` 値を指定して、ステートメントごとにプラン ガイドを作成します。  
  
## <a name="see-also"></a>参照  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [プランガイド](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
