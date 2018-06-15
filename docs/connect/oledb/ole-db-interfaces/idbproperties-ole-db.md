---
title: IDBProperties (OLE DB) |Microsoft ドキュメント
description: IDBProperties インターフェイス (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 870a331b7ae15c84c2dc9cfb4abaa14ed57d5a42
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35304781"
---
# <a name="idbproperties-ole-db"></a>IDBProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  OLE DB 標準仕様では、プロバイダーが **DBPROPINFO::vValues**に VT_EMPTY を指定することを認めています。 ただし、OLE DB Driver for SQL Server の OLE DB 常に VT_EMPTY を返しますを呼び出すと **:getpropertyinfo**で**DBPROPSET_ROWSETALL**行セット プロパティを取得します。  
  
## <a name="see-also"></a>参照  
 [インターフェイス&#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md) 
  
  
