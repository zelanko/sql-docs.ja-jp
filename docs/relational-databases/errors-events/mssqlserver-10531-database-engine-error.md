---
title: MSSQLSERVER_10531 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10531 (Database Engine error)
ms.assetid: bb40e994-231c-44ce-933f-8d767fb2f450
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d3eada50aff496f37cb56a65b82bc396b7e713fa
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47798160"
---
# <a name="mssqlserver10531"></a>MSSQLSERVER_10531
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|10531|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|PG_NO_ELIGIBLE_STMT|  
|メッセージ テキスト|プラン ガイド '%.*ls' をキャッシュから作成できません。ユーザーに適切な権限がありません。 プラン ガイドを作成するユーザーに VIEW SERVER STATE 権限を付与してください。|  
  
## <a name="explanation"></a>説明  
指定したプラン ガイドをプラン キャッシュから作成するための適切な権限がユーザーにありません。  
  
## <a name="user-action"></a>ユーザーの操作  
プラン ガイドを作成するユーザーに VIEW SERVER STATE 権限を付与します。  
  
## <a name="see-also"></a>参照  
[プラン ガイド](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
