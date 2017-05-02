---
title: MSSQLSERVER_5554 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 5554 (Database Engine error)
ms.assetid: 7134bbe5-d240-4a98-85ce-b13cc8ae9b0e
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 45d6f39467c40af5da0a959e427aacdc30f9d4bb
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver5554"></a>MSSQLSERVER_5554
  
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
  

