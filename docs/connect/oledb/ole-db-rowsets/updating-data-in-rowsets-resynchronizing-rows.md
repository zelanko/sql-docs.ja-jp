---
title: 行の再同期 |Microsoft ドキュメント
description: SQL Server の OLE DB Driver を使用して行を再同期
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- synchronization [OLE DB]
- IRowsetResynch interface
- resynchronizing rows
- data updates [SQL Server], OLE DB
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 99e355ded49f480a6ac0f27dc700d96c8ced9e87
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2018
ms.locfileid: "35690245"
---
# <a name="updating-data-in-rowsets---resynchronizing-rows"></a>行セットの行の再同期のデータの更新
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  SQL Server の OLE DB ドライバーをサポートしている**IRowsetResynch**で[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]カーソルでサポートされている行セットのみです。 **IRowsetResynch**は要求時に使用できません。 コンシューマーは、行セットを開く前にインターフェイスを要求する必要があります。  
  
## <a name="see-also"></a>参照  
 [行セット内のデータの更新](../../oledb/ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
