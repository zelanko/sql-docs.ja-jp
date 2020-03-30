---
title: ブックマーク | Microsoft Docs
description: OLE DB Driver for SQL Server のブックマーク
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- bookmarks [OLE DB]
- OLE DB Driver for SQL Server, bookmarks
- rowsets [OLE DB], bookmarks
- OLE DB rowsets, bookmarks
author: pmasl
ms.author: pelopes
ms.openlocfilehash: a10d8c7afb3dab1b193c82b3e6686cdad2c0651e
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "68015387"
---
# <a name="bookmarks"></a>ブックマーク
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  ブックマークを使用すると、コンシューマーは行をすばやく返すことができます。 コンシューマーはブックマークの値を基に、行にランダムにアクセスできます。 ブックマーク列は、行セットの列 0 です。 コンシューマーは、バインド構造体の dwFlag フィールド値に DBCOLUMNSINFO_ISBOOKMARK を設定して、その列がブックマークに使用されることを示します。 また、コンシューマーは行セット プロパティ DBPROP_BOOKMARKS に VARIANT_TRUE を設定します。 その結果、行セットに列 0 が存在できるようになります。 **IRowsetLocate::GetRowsAt** メソッドを使用すると、ブックマークからのオフセットで指定された行で始まる行が取り出されます。  
  
## <a name="see-also"></a>参照  
 [行セット](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
