---
title: MSSQLSERVER_7911 | Microsoft Docs
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
- 7911 (Database Engine error)
ms.assetid: dd8390f3-0f77-4fb2-ba94-631a56e42bc6
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: cguyer
robots: noindex,nofollow
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: a263211de746ed459a1f76c1146671bb0f746301
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver7911"></a>MSSQLSERVER_7911
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|7911|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC2_REPAIR_PAGE_DEALLOCATED|  
|メッセージ テキスト|修復 : ページ P_ID が、オブジェクト ID O_ID、インデックス ID I_ID、パーティション ID PN_ID、アロケーション ユニット ID A_ID (型 TYPE) から割り当て解除されました。|  
  
## <a name="explanation"></a>説明  
単一ページ スロット配列の IAM (Index Allocation Map) ページから 1 ページが割り当て解除されたことを示す、REPAIR からの情報メッセージです。  
  
## <a name="user-action"></a>ユーザーの操作  
なし  
  

