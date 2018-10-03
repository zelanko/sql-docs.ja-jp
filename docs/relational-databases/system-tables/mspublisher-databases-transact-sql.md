---
title: MSpublisher_databases (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSpublisher_databases
- MSpublisher_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpublisher_databases system table
ms.assetid: 59b0166e-a64c-46b8-befc-c222fa1ccce2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7904bd3b6d629daf65d97bf88bba26cbb02bd93f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47620750"
---
# <a name="mspublisherdatabases-transact-sql"></a>MSpublisher_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSpublisher_databases**テーブルには、ローカル ディストリビューターによって処理されるパブリッシャー/パブリッシャー データベースの各ペアの 1 つの行が含まれています。 このテーブルは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|パブリッシャーの ID。|  
|**publisher_db**|**sysname**|パブリッシャー データベースの名前。|  
|**id**|**int**|行の ID です。|  
|**publisher_engine_edition**|**int**|エディション、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]発行元は、次のいずれかを指定できます。<br /><br /> **10** personal Edition を =<br /><br /> **11** desktop Engine (MSDE) を =<br /><br /> **20** = 標準<br /><br /> **21**ワークグループを =<br /><br /> **30** = Enterprise (評価)<br /><br /> **31**開発者を =<br /><br /> **40** = express (Express は、パブリッシャーをすることはできません。 この値は完全性を維持するためにあります)。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
