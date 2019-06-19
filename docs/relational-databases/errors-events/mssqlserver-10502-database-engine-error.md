---
title: MSSQLSERVER_10502 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10502 (Database Engine error)
ms.assetid: 26d9b64d-4299-4b55-92d0-0a32a3688c0a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a507b0d28f57869096877b00cadf4f15d70783aa
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62985858"
---
# <a name="mssqlserver10502"></a>MSSQLSERVER_10502
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
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
[プラン ガイド](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
