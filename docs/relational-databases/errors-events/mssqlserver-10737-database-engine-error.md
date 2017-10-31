---
title: MSSQLSERVER_10737 | Microsoft Docs
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
- 10737 (Database Engine error)
ms.assetid: 208af6ed-b271-4ab8-803e-7666025385c8
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 591b8634e244f472fd5051fde842f4bf9428c4d4
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver10737"></a>MSSQLSERVER_10737
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|MSSQLSERVER|  
|イベント ID|10737|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|REBUILD_PARTITION_ALL_NOT_SPECIFIED|  
|メッセージ テキスト|ALTER TABLE REBUILD ステートメントまたは ALTER INDEX REBUILD ステートメントの DATA_COMPRESSION 句でパーティションを指定する場合は、PARTITION=ALL を指定する必要があります。 PARTITION=ALL 句を使用すると、DATA_COMPRESSION 句でサブセットのみを指定した場合でも、テーブルまたはインデックスのすべてのパーティションが必ず再構築されます。|  
  
## <a name="user-action"></a>ユーザーの操作  
ALTER TABLE ステートメントまたは ALTER INDEX ステートメントに PARTITION=ALL 句を追加します。 また、特定のパーティションを再構築するには、REBUILD PARTITION = \<partition-number-expr> WITH (DATA_COMPRESSION={ON | OFF}) を使用します。  
  

