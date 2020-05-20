---
title: データベースメンテナンスプランのテーブル (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- database maintenance plans [SQL Server]
- maintenance plans [SQL Server], system tables
- system tables [SQL Server], database maintenance plans
ms.assetid: f264554c-5514-4df2-aadb-6dcdc2dfcfea
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 720d439449870e2b0e620f67cf0321b5c5cde043
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82807043"
---
# <a name="database-maintenance-plan-tables-transact-sql"></a>データベースメンテナンスプランのテーブル (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  このセクションのトピックでは、データベースメンテナンスプランで使用される情報を格納するシステムテーブルについて説明します。 これらのテーブルは、以前のバージョンのからアップグレードされたインスタンスの情報を保持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] します。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
## <a name="in-this-section"></a>このセクションの内容  
 [sysdbmaintplan_databases](../../relational-databases/system-tables/sysdbmaintplan-databases-transact-sql.md)  
 アップグレードされたデータベースメンテナンスプランが関連付けられているデータベースごとに1行のデータを格納します。  
  
 [sysdbmaintplan_history](../../relational-databases/system-tables/sysdbmaintplan-history-transact-sql.md)  
 アップグレードされたデータベース メンテナンス プランで実行したアクションごとに 1 行のデータを格納します。  
  
 [sysdbmaintplan_jobs](../../relational-databases/system-tables/sysdbmaintplan-jobs-transact-sql.md)  
 アップグレードされたデータベースメンテナンスプランジョブごとに1行のデータを格納します。  
  
 [sysdbmaintplans](../../relational-databases/system-tables/sysdbmaintplans-transact-sql.md)  
 アップグレードされたデータベースメンテナンスプランごとに1行のデータを格納します。  
  
## <a name="see-also"></a>参照  
 [メンテナンス プラン](../../relational-databases/maintenance-plans/maintenance-plans.md)  
  
  
