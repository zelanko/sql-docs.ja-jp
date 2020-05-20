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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5ea0bbe308e3b0e49f6250dd02d2c6c1f636751c
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830923"
---
# <a name="sql-server-operating-system-related-dynamic-management-views-transact-sql"></a>SQL Server オペレーティングシステム関連の動的管理ビュー (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

このセクションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オペレーティングシステム (SQLOS) に関連付けられている動的管理ビュー (DMV) について説明します。 SQLOS は、に固有のオペレーティングシステムリソースの管理を担当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] します。

SQLOS Dmv が目次に一覧表示されます。 これらのほとんどは、という名前 `sys.dm_os_<description>` です。

 次の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オペレーティングシステム関連の動的管理ビューは [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] です。  
  
|||  
|-|-|  
|**sys.dm_os_function_symbolic_name**|**sys.dm_os_ring_buffers**|  
|**dm_os_memory_allocations**|**dm_os_sublatches**|  
|**dm_os_worker_local_storage**||  
  
## <a name="see-also"></a>参照  
 [動的管理ビューおよび関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

