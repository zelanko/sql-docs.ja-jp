---
title: MSSQLSERVER_8710 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 8710 (Database Engine error)
ms.assetid: 78b9f9da-5489-4be0-94df-f065d86ed18c
caps.latest.revision: "8"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f96172d7cb0ae2eddd1da57fd3caebf527270fae
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver8710"></a>MSSQLSERVER_8710
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|MSSQLSERVER|  
|イベント ID|8710|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|QUERY2_CUBE_ILLEGAL_AGG_FUNC|  
|メッセージ テキスト|CUBE、ROLLUP、または GROUPING SET クエリで使用される集計関数は、サブ集計をマージするものである必要があります。 この問題を解決するには、集計関数を削除するか、UNION ALL を GROUP BY 句で使用するクエリを記述してください。|  
  
## <a name="explanation"></a>説明  
サブ集計をマージできない集計関数が CUBE、ROLLUP、または GROUPING SET で使用されています。  
  
## <a name="user-action"></a>ユーザーの操作  
この問題を解決するには、集計関数を削除するか、UNION ALL を GROUP BY 句で使用するクエリを記述してください。  
  
