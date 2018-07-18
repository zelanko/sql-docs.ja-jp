---
title: MSSQLSERVER_10737 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 10737 (Database Engine error)
ms.assetid: 208af6ed-b271-4ab8-803e-7666025385c8
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 14e593ef1dba6a6bed7c5d8a7a1fa42e642ee7d7
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37428371"
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
  
  
