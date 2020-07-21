---
title: MSSQLSERVER_10502 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10502 (Database Engine error)
ms.assetid: 26d9b64d-4299-4b55-92d0-0a32a3688c0a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ac0209030531f0c56a1a071ba54282f10d4b7db9
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86552407"
---
# <a name="mssqlserver_10502"></a>MSSQLSERVER_10502
    
## <a name="details"></a>詳細  
  
|属性|値|  
|-|-|  
|製品名|SQL Server|  
|イベント ID|10502|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|PG_DUP_FOUND|  
|メッセージ テキスト|プラン ガイド '%.*ls' を作成できません。@stmt と @module_or_batch または @plan_handle と @statement_start_offset で指定したステートメントがデータベース内の既存のプラン ガイド '%.\*ls' と一致しています。 新しいプラン ガイドを作成する前に、既存のプラン ガイドを削除します。|  
  
## <a name="explanation"></a>説明  
 指定したステートメントのプラン ガイドが存在します。  
  
## <a name="user-action"></a>ユーザーの操作  
 新しいプラン ガイドを作成する前に、既存のプラン ガイドを削除します。  
  
## <a name="see-also"></a>参照  
 [プランガイド](../performance/plan-guides.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
