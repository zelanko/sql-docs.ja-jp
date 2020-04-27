---
title: MSSQLSERVER_5554 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5554 (Database Engine error)
ms.assetid: 7134bbe5-d240-4a98-85ce-b13cc8ae9b0e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c3b8e4690b0e0c501fee26648cd9632fdcf28b1d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62913688"
---
# <a name="mssqlserver_5554"></a>MSSQLSERVER_5554
    
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
  
  
