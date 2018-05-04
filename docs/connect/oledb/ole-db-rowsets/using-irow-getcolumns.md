---
title: Irow::getcolumns を使用して |Microsoft ドキュメント
description: Irow::getcolumns を使用して、行内のすべての列にアクセスするには
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
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
- fetching rows
- IRow interface
- single row fetching [OLE DB Driver for SQL Server]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- GetColumns method
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: fc82a06567e1058a1ee0f7745db153d8af96d90e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="using-irowgetcolumns"></a>IRow::GetColumns の使用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **IRow**実装により、列に順方向専用の順次アクセスされます。 1 回の呼び出しを含む行のすべての列にアクセスすることができますか、 **irow::getcolumns**呼び出したり**irow::getcolumns**行に複数の列をアクセスするたびに複数回です。  
  
 複数回呼び出す**irow::getcolumns**重ならないようにします。 たとえば、最初の呼び出し**irow::getcolumns**に列 1、2、および 3、2 番目の呼び出しが取得**irow::getcolumns**列 4、5 および 6 を呼び出す必要があります。 場合を後で呼び出す**irow::getcolumns**重なっているため、の状態フラグ (DBCOLUMNACCESS の dwstatus フィールド) が DBSTATUS_E_UNAVAILABLE に設定します。  
  
## <a name="see-also"></a>参照  
 [IRow による 1 行のフェッチ](../../oledb/ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
  
