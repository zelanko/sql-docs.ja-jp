---
title: "MSpublisher_databases (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSpublisher_databases
- MSpublisher_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpublisher_databases system table
ms.assetid: 59b0166e-a64c-46b8-befc-c222fa1ccce2
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7f4edaf2e09164eb1163077cb9769a0743d445f1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mspublisherdatabases-transact-sql"></a>MSpublisher_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSpublisher_databases**テーブルには、ローカル ディストリビューターによって処理されるパブリッシャー/パブリッシャー データベースの各ペアの 1 つの行が含まれています。 このテーブルは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**publisher_id などがあります。**|**smallint**|パブリッシャーの ID。|  
|**publisher_db**|**sysname**|パブリッシャー データベースの名前。|  
|**id**|**int**|行の ID です。|  
|**publisher_engine_edition**|**int**|エディション、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーで、次のいずれかになります。<br /><br /> **10** personal Edition を =<br /><br /> **11** desktop Engine (MSDE) を =<br /><br /> **20** = 標準<br /><br /> **21**ワークグループを =<br /><br /> **30** = Enterprise (評価)<br /><br /> **31**開発者を =<br /><br /> **40** = express (Express は、パブリッシャーをすることはできません。 この値は完全性を維持するためにあります)。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
