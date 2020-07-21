---
title: MSSQLSERVER_10534 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10534 (Database Engine error)
ms.assetid: e65bb118-99d5-4fdb-b1d5-0ec70f0a677b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 021ef5c5c7980115f5eb25792f4090774d968cef
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86554127"
---
# <a name="mssqlserver_10534"></a>MSSQLSERVER_10534
    
## <a name="details"></a>詳細  
  
|属性|値|  
|-|-|  
|製品名|SQL Server|  
|イベント ID|10534|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|PG_INVALID_PARAMS|  
|メッセージ テキスト|プラン ガイド '%.\*ls' を作成できません。`@params` に指定した値が無効です。 *parameter_name parameter_type* 形式の値を指定するか、NULL を指定してください。|  
  
## <a name="explanation"></a>説明  
 `@params` に指定した値が無効です。  
  
## <a name="user-action"></a>ユーザーの操作  
 *parameter_name parameter_type* 形式の値を指定するか、NULL を指定してください。  
  
## <a name="see-also"></a>参照  
 [プランガイド](../performance/plan-guides.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
