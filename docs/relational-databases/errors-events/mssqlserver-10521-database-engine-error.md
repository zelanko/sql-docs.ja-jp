---
title: MSSQLSERVER_10521 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10521 (Database Engine error)
ms.assetid: ba2d7e44-207c-4428-b5f0-c975ac122c0d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5e7e54dbf0728f3cc2705153f1bd9c56e9b000c1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47646100"
---
# <a name="mssqlserver10521"></a>MSSQLSERVER_10521
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
