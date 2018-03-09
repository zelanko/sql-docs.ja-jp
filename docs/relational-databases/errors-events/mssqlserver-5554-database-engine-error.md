---
title: MSSQLSERVER_5554 | Microsoft Docs
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
- 5554 (Database Engine error)
ms.assetid: 7134bbe5-d240-4a98-85ce-b13cc8ae9b0e
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8f5b8dd08230e8fbb22961dafc4b469acedcac05
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver5554"></a>MSSQLSERVER_5554
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|MSSQLSERVER|  
|イベント ID|5554|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|FS_MINIVER_OVERFLOW|  
|メッセージ テキスト|1 つのファイルのバージョンの総数が、ファイル システムで設定されている上限に達しました。|  
  
## <a name="explanation"></a>説明  
複数のアクティブな結果セット (MARS) またはトリガーのシナリオでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はオペレーティング システムによって指定されたミニバージョンを使用します。  
  
## <a name="user-action"></a>ユーザーの操作  
同じトランザクション内のデータを繰り返し更新しないようにします。  
  
