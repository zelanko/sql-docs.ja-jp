---
title: MSSQLSERVER_10507 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 10507 (Database Engine error)
ms.assetid: cd83fa81-ac37-4eda-a3c3-17610b051de2
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c5f69dc55a2b80a47b9d014c50fa03074a76e31d
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver10507"></a>MSSQLSERVER_10507
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|10507|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|PG_STMT_DOES_NOT_MATCH|  
|メッセージ テキスト|プラン ガイド '%.\*ls' を作成できません。**@stmt** と **@module_or_batch** または **@plan_handle** と **@statement_start_offset** で指定したステートメントが、指定したモジュールまたはバッチのステートメントと一致しません。 モジュールまたはバッチのステートメントと一致するように値を変更してください。|  
  
## <a name="explanation"></a>説明  
指定したモジュールまたはバッチのステートメントが、指定したステートメントまたはステートメントのオフセット値と一致しませんでした。  
  
## <a name="user-action"></a>ユーザーの操作  
モジュールまたはバッチのステートメントと一致するように指定のパラメーター値を変更します。  
  
## <a name="see-also"></a>参照  
[プラン ガイド](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
