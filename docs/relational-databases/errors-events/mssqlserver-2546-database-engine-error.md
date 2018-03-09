---
title: MSSQLSERVER_2546 | Microsoft Docs
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
- 2546 (Database Engine error)
ms.assetid: c8f0e1b4-c7c4-45f2-9221-746714172313
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 934b03a1d07f9784e6887edc72166d712f37f3dd
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver2546"></a>MSSQLSERVER_2546
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|2546|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC_INDEX_MARKED_DISABLED|  
|メッセージ テキスト|テーブル 'OBJECT_NAME' のインデックス 'INDEX_NAME' は無効に設定されています。 オンラインにするには、インデックスを再構築してください。|  
  
## <a name="explanation"></a>説明  
指定されているインデックスは、オフラインまたは無効に設定されています。 そのため、このインデックスをチェックできません。  
  
## <a name="user-action"></a>ユーザーの操作  
ALTER INDEX を使用してインデックスを再構築します。  
  
## <a name="see-also"></a>参照  
[ALTER INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/alter-index-transact-sql.md)  
[インデックスの再編成と再構築](~/relational-databases/indexes/reorganize-and-rebuild-indexes.md)  
  
