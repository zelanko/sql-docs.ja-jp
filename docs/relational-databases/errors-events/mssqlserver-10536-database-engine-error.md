---
title: MSSQLSERVER_10536 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10536 (Database Engine error)
ms.assetid: 9f97b41f-0ef8-4ad2-aec0-906a5d7522ba
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c0051be2c84fe9444d034dec87d77bde95178d2f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85781416"
---
# <a name="mssqlserver_10536"></a>MSSQLSERVER_10536
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細  
  
| 属性 | 値 |  
| :-------- | :---- |  
|製品名|SQL Server|  
|イベント ID|10536|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|PG_TOO_MANY_STMTS|  
|メッセージ テキスト|プラン ガイド '%.\*ls' を作成できません。指定された **\@plan_handle** に対応するバッチまたはモジュールに含まれるステートメントが 1000 個を超えています。 バッチまたはモジュール内の各ステートメントに **statement_start_offset** 値を指定して、各ステートメントにプラン ガイドを作成してください。|  
  
## <a name="explanation"></a>説明  
指定した **\@plan_handle** に対応するバッチまたはモジュールに、条件を満たすステートメントが 1000 以上含まれています。  
  
## <a name="user-action"></a>ユーザーの操作  
バッチまたはモジュール内の各ステートメントに **statement_start_offset** 値を指定して、各ステートメントにプラン ガイドを作成してください。  
  
## <a name="see-also"></a>参照  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[プラン ガイド](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
