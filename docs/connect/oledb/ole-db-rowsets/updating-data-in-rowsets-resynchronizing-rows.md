---
title: 行の再同期 |Microsoft Docs
description: SQL Server の OLE DB ドライバーを使用して行の再同期
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
ms.author: pelopes
manager: craigg
ms.openlocfilehash: dc7d722f4d4b97cd4242195d49ff7d5290c52f24
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43017463"
---
# <a name="updating-data-in-rowsets---resynchronizing-rows"></a>行セット内のデータの更新 - 行の再同期
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server サポート**IRowsetResynch**で[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]だけ行セットをカーソルでサポートされています。 **IRowsetResynch** を、要求時に使用することはできません。 コンシューマーは、行セットを開く前にインターフェイスを要求する必要があります。  
  
## <a name="see-also"></a>参照  
 [行セット内のデータの更新](../../oledb/ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
