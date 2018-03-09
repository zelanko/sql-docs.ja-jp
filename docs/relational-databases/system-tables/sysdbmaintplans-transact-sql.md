---
title: "sysdbmaintplans (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysdbmaintplans_TSQL
- sysdbmaintplans
dev_langs:
- TSQL
helpviewer_keywords:
- sysdbmaintplans system table
ms.assetid: 0363296a-3082-48a9-9eb5-a1020b2f541a
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6297a26f046c82b628bc65de8131bc21dd6f59fd
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdbmaintplans-transact-sql"></a>sysdbmaintplans (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  このテーブルに格納されます[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の既存の情報を保持するために、以前のバージョンからアップグレードされたインスタンス[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]このテーブルの内容は変更されません。 次の表は、 **msdb**データベース。  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  

  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**plan_id**|**uniqueidentifier**|データベース メンテナンス プランの ID|  
|**plan_name**|**sysname**|データベース メンテナンス プランの名前。|  
|**date_created**|**datetime**|データベース メンテナンス プランが作成された日付。|  
|**所有者**|**sysname**|データベース メンテナンス プランの所有者。|  
|**max_history_rows**|**int**|システム テーブル内で、データベース メンテナンス プランの履歴の記録用に割り当てられる行数の最大値。|  
|**remote_history_server**|**sysname**|履歴レポートがリモート サーバーに書き込まれる場合のサーバーの名前。|  
|**max_remote_history_rows**|**int**|履歴レポートがリモート サーバーに書き込まれる場合の、サーバー上のシステム テーブル内で割り当てられる行数の最大値。|  
|**user_defined_1**|**int**|既定値は NULL|  
|**user_defined_2**|**nvarchar(100)**|既定値は NULL|  
|**user_defined_3**|**datetime**|既定値は NULL|  
|**user_defined_4**|**uniqueidentifier**|既定値は NULL|  
|**log_shipping**|**bit**|ログ配布の状態。<br /><br /> **0** = disabled **1** = 有効になっています。|  
  
  
