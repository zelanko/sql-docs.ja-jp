---
title: ブックマーク |Microsoft ドキュメント
description: OLE DB Driver for SQL Server 内のブックマーク
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
- bookmarks [OLE DB]
- OLE DB Driver for SQL Server, bookmarks
- rowsets [OLE DB], bookmarks
- OLE DB rowsets, bookmarks
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 50a62fda685292a22e227da72cbc1a5ff121de34
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="bookmarks"></a>ブックマーク
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ブックマークを使用すると、コンシューマーは行をすばやく返すことができます。 コンシューマーはブックマークの値を基に、行にランダムにアクセスできます。 ブックマーク列は、行セットの列 0 です。 コンシューマーは、バインド構造体の dwFlag フィールド値に DBCOLUMNSINFO_ISBOOKMARK を設定して、その列がブックマークに使用されることを示します。 また、コンシューマーは行セット プロパティ DBPROP_BOOKMARKS に VARIANT_TRUE を設定します。 その結果、行セットに列 0 が存在できるようになります。 **Irowsetlocate::getrowsat**ブックマークからのオフセットとして指定した行で始まる行をフェッチするメソッドを使用しています。  
  
## <a name="see-also"></a>参照  
 [行セット](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
