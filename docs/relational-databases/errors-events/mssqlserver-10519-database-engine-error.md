---
title: MSSQLSERVER_10519 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10519 (Database Engine error)
ms.assetid: 3be393a1-b186-41ae-afb9-a3d07ff354bb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1b57f8a7985c9fb092209bc5a80b9d0c3294d98c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85781495"
---
# <a name="mssqlserver_10519"></a>MSSQLSERVER_10519
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細  
  
| 属性 | 値 |  
| :-------- | :---- |  
|製品名|SQL Server|  
|イベント ID|10519|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|PG_INCOMPATIBLE_STMT_AND_HINTS|  
|メッセージ テキスト|プラン ガイド '%.\*ls' を作成できません。 **\@hints** で指定されたヒントを、 **\@stmt** または **\@statement_start_offset** のいずれかで指定されたステートメントに適用できません。 ヒントがステートメントに適用可能であることを確認してください。|  
  
## <a name="explanation"></a>説明  
**\@hints** で指定されたヒントを、 **\@stmt** または **\@statement_start_offset** のいずれかで指定されたステートメントに適用できません。  
  
## <a name="user-action"></a>ユーザーの操作  
ステートメントに適用できるヒントを指定します。  
  
## <a name="see-also"></a>参照  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[プラン ガイド](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
