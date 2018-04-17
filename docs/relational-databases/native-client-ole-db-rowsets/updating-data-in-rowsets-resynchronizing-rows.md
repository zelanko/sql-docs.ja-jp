---
title: 行の再同期 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- synchronization [OLE DB]
- IRowsetResynch interface
- resynchronizing rows
- data updates [SQL Server], OLE DB
ms.assetid: d2d30505-a878-4aa9-b821-53d8118a45a5
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 73d2efb0b3ac3d942cbcb87ab97e2840b26d3f39
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="updating-data-in-rowsets---resynchronizing-rows"></a>行セットの行の再同期のデータの更新
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのサポート**IRowsetResynch**で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]カーソルでサポートされている行セットのみです。 **IRowsetResynch**は要求時に使用できません。 コンシューマーは、行セットを開く前にインターフェイスを要求する必要があります。  
  
## <a name="see-also"></a>参照  
 [行セットのデータの更新](../../relational-databases/native-client-ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
