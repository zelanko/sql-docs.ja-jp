---
title: MSSQLSERVER_10532 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10532 (Database Engine error)
ms.assetid: 01da29ee-bf67-433f-8148-587a7e8d1d76
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0c92e077135491a87687fbb765affc4642e064ea
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86554147"
---
# <a name="mssqlserver_10532"></a>MSSQLSERVER_10532
    
## <a name="details"></a>詳細  
  
|属性|値|  
|-|-|  
|製品名|SQL Server|  
|イベント ID|10532|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|PG_NO_ELIGIBLE_STMT|  
|メッセージ テキスト|プラン ガイド '%.\*ls' を作成できません。`@plan_handle` で指定されたバッチまたはモジュールに、プラン ガイドに適したステートメントが含まれていません。 `@plan_handle` に別の値を指定します。|  
  
## <a name="explanation"></a>説明  
 `@plan_handle` で指定されたバッチまたはモジュールに、プラン ガイドに適したステートメントが含まれていません。  
  
## <a name="user-action"></a>ユーザーの操作  
 `@plan_handle` に別の値を指定します。  
  
## <a name="see-also"></a>参照  
 [プランガイド](../performance/plan-guides.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
