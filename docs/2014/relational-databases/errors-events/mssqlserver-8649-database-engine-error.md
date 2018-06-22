---
title: MSSQLSERVER_8649 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 8649 (Database Engine error)
ms.assetid: 992dbc74-7c3a-498b-9f1b-b28387640677
caps.latest.revision: 15
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 3da65279260e142385a7b872c7234cb0f0b6bc8a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072535"
---
# <a name="mssqlserver8649"></a>MSSQLSERVER_8649
    
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
 [SET QUERY_GOVERNOR_COST_LIMIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql)  
  
  
