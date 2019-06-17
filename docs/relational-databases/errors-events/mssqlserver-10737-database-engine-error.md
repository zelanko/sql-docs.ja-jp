---
title: MSSQLSERVER_10737 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10737 (Database Engine error)
ms.assetid: 208af6ed-b271-4ab8-803e-7666025385c8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f96a3849360cc0eb5d04c75187f505967b33baf3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63048266"
---
# <a name="mssqlserver10737"></a>MSSQLSERVER_10737
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
