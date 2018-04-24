---
title: MSSQLSERVER_5554 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 5554 (Database Engine error)
ms.assetid: 7134bbe5-d240-4a98-85ce-b13cc8ae9b0e
caps.latest.revision: 12
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 590c9c4d9fe9182a1f07387a0e0e944a98afecd6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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
  
