---
description: sysdbmaintplan_databases (Transact-SQL)
title: sysdbmaintplan_databases (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdbmaintplan_databases
- sysdbmaintplan_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysdbmaintplan_databases system table
ms.assetid: f8413a44-8fcc-4899-84f2-b4afe0f8ec08
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5f2f6d15d1a1d1d7780472627c32cf4b978fb0d9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88427614"
---
# <a name="sysdbmaintplan_databases-transact-sql"></a>sysdbmaintplan_databases (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  このテーブルは、以前のバージョンのからアップグレードされたインスタンスの既存の情報を保持するために含まれてい [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンでは、このテーブルの内容は変更されません。 このテーブルは、 **msdb** データベースに格納されます。  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**plan_id**|**一意**|メンテナンスプラン ID。|  
|**database_name**|**sysname**|データベースメンテナンスプランに関連付けられているデータベースの名前。|  
  
  
