---
title: IDBProperties (OLE DB ドライバー) | Microsoft Docs
description: IDBProperties インターフェイス (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
ms.openlocfilehash: afaf7fc8e0ea60a1ee8576e0afa5b279653a2272
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87244498"
---
# <a name="idbproperties-ole-db"></a>IDBProperties (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB 標準仕様では、プロバイダーが **DBPROPINFO::vValues**に VT_EMPTY を指定することを認めています。 ただし、**DBPROPSET_ROWSETALL** を使用して **IDBProperties::GetPropertyInfo** を呼び出して行セット プロパティを取得すると、OLE DB Driver for SQL Server OLE DB は、常に VT_EMPTY を返します。  
  
## <a name="see-also"></a>参照  
 [インターフェイス &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md) 
  
  
