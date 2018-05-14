---
title: MSSQLSERVER_8649 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 8649 (Database Engine error)
ms.assetid: 992dbc74-7c3a-498b-9f1b-b28387640677
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e87c496b60ce000ec148b79e7556a5cd15edfcdf
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver8649"></a>MSSQLSERVER_8649
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|8649|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|COST_TOO_HIGH|  
|メッセージ テキスト|このクエリの見積コスト (%d) が設定されたしきい値 %d を超えたので、クエリは取り消されました。 システム管理者に連絡してください。|  
  
## <a name="explanation"></a>説明  
このクエリの見積コストは、QUERY_GOVERNOR_COST_LIMIT に対して設定されているしきい値を超えたので、クエリが取り消されました。  
  
## <a name="user-action"></a>ユーザーの操作  
QUERY_GOVERNOR_COST_LIMIT オプションの設定値を大きくします。  
  
## <a name="see-also"></a>参照  
[SET QUERY_GOVERNOR_COST_LIMIT &#40;Transact-SQL&#41;](~/t-sql/statements/set-query-governor-cost-limit-transact-sql.md)  
  
