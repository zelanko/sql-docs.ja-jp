---
title: ブックマーク |Microsoft ドキュメント
description: OLE DB Driver for SQL Server 内のブックマーク
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bookmarks [OLE DB]
- OLE DB Driver for SQL Server, bookmarks
- rowsets [OLE DB], bookmarks
- OLE DB rowsets, bookmarks
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bfca58f2db78257921f9f6864a7b8325f86c7705
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="bookmarks"></a>ブックマーク
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ブックマークを使用すると、コンシューマーは行をすばやく返すことができます。 コンシューマーはブックマークの値を基に、行にランダムにアクセスできます。 ブックマーク列は、行セットの列 0 です。 コンシューマーは、バインド構造体の dwFlag フィールド値に DBCOLUMNSINFO_ISBOOKMARK を設定して、その列がブックマークに使用されることを示します。 また、コンシューマーは行セット プロパティ DBPROP_BOOKMARKS に VARIANT_TRUE を設定します。 その結果、行セットに列 0 が存在できるようになります。 **Irowsetlocate::getrowsat**ブックマークからのオフセットとして指定した行で始まる行をフェッチするメソッドを使用しています。  
  
## <a name="see-also"></a>参照  
 [行セット](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
