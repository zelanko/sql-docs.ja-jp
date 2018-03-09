---
title: MSSQLSERVER_2593 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 2593 (Database Engine error)
ms.assetid: 2e25bc43-606a-40de-8b87-3b55b96f4a91
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e9c43c4216ed4b72ba1eff39a9e4e3f4f4064aac
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver2593"></a>MSSQLSERVER_2593
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|2593|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC_OBJECT_ROW_PAGE_SUMMARY|  
|メッセージ テキスト|オブジェクト 'OBJECT' の PAGECOUNT ページには ROWCOUNT 行あります。|  
  
## <a name="explanation"></a>説明  
このメッセージは、DBCC CHECKALLOC を除くすべての DBCC チェックから返される情報出力の一部であり、指定されたオブジェクトの行カウントおよびページ カウントを示しています。  
  
## <a name="user-action"></a>ユーザーの操作  
なし  
  
