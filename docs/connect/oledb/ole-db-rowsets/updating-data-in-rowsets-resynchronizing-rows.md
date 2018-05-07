---
title: 行の再同期 |Microsoft ドキュメント
description: SQL Server の OLE DB Driver を使用して行を再同期
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-rowsets
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
ms.openlocfilehash: cda60f254d200e6e8c23235bdeb9988b2dd80309
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="updating-data-in-rowsets---resynchronizing-rows"></a>行セットの行の再同期のデータの更新
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  SQL Server の OLE DB ドライバーをサポートしている**IRowsetResynch**で[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]カーソルでサポートされている行セットのみです。 **IRowsetResynch**は要求時に使用できません。 コンシューマーは、行セットを開く前にインターフェイスを要求する必要があります。  
  
## <a name="see-also"></a>参照  
 [行セットのデータの更新](../../oledb/ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
