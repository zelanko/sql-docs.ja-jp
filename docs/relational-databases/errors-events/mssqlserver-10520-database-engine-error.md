---
title: MSSQLSERVER_10520 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 10520 (Database Engine error)
ms.assetid: cc8799f1-5b90-4248-b209-e1d5087f9529
caps.latest.revision: "9"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 05acd414289507544caa7ae5806471982768949e
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver10520"></a>MSSQLSERVER_10520
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|10520|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|PG_PARAM_NOT_ALLOWED|  
|メッセージ テキスト|プラン ガイド '%.*ls' を作成できません。'%ls' として指定した @type のパラメーター '%ls' に NULL 以外の値を指定しています。 この型のパラメーターには、NULL 値を指定する必要があります。 パラメーターに NULL を指定するか、パラメーターに NULL 以外の値を指定可能な型に変更します。|  
  
## <a name="explanation"></a>説明  
@type で指定した型のパラメーターには、NULL 値を指定する必要がありますが、NULL 以外の値を指定しました。  
  
## <a name="user-action"></a>ユーザーの操作  
パラメーターに NULL を指定するか、パラメーターに NULL 以外の値を指定可能な型に変更します。  
  
## <a name="see-also"></a>参照  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[プラン ガイド](~/relational-databases/performance/plan-guides.md)  
  
