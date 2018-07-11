---
title: MSSQLSERVER_10532 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 10532 (Database Engine error)
ms.assetid: 01da29ee-bf67-433f-8148-587a7e8d1d76
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: be808412900aed583450824dca873deea4697f40
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37409480"
---
# <a name="mssqlserver10532"></a>MSSQLSERVER_10532
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|10532|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|PG_NO_ELIGIBLE_STMT|  
|メッセージ テキスト|プラン ガイドを作成することはできません ' % です。\*ls' で指定されたバッチまたはモジュール`@plan_handle`はプラン ガイドに適したステートメントが含まれていません。 `@plan_handle` に別の値を指定します。|  
  
## <a name="explanation"></a>説明  
 `@plan_handle` で指定されたバッチまたはモジュールに、プラン ガイドに適したステートメントが含まれていません。  
  
## <a name="user-action"></a>ユーザーの操作  
 `@plan_handle` に別の値を指定します。  
  
## <a name="see-also"></a>参照  
 [プラン ガイド](../performance/plan-guides.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
