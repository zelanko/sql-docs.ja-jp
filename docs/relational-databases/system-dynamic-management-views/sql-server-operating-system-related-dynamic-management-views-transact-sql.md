---
title: SQL Server オペレーティングシステム関連の動的管理ビュー (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 04/17/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- operating systems [SQL Server], dynamic management objects
- SQL Operating System dynamic management objects [SQL Server]
- SQL OS dynamic management objects [SQL Server]
- dynamic management objects [SQL Server], SQL OS
ms.assetid: 3030c86a-0a74-4fed-ac0f-392e244cb965
author: stevestein
ms.author: sstein
ms.openlocfilehash: 862f54351eb67d2170d8e9806347eb8608178c23
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "71342040"
---
# <a name="sql-server-operating-system-related-dynamic-management-views-transact-sql"></a>SQL Server オペレーティングシステム関連の動的管理ビュー (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

このセクションでは、オペレーティングシステム (SQLOS) に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]関連付けられている動的管理ビュー (DMV) について説明します。 SQLOS は、に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]固有のオペレーティングシステムリソースの管理を担当します。

SQLOS Dmv が目次に一覧表示されます。 これらのほとんどは、と`sys.dm_os_<description>`いう名前です。

 次[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のオペレーティングシステム関連の動的管理ビューは[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]です。  
  
|||  
|-|-|  
|**sys.dm_os_function_symbolic_name**|**sys.dm_os_ring_buffers**|  
|**dm_os_memory_allocations**|**dm_os_sublatches**|  
|**dm_os_worker_local_storage**||  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

