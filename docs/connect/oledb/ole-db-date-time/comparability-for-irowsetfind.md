---
title: IRowsetFind での比較 |Microsoft ドキュメント
description: IRowsetFind での比較
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRowsetFind comparability
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 1226a3e1a0177056bc38ce69cf03206be941c932
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35304811"
---
# <a name="comparability-for-irowsetfind"></a>IRowsetFind での比較
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  日付型または時刻型の場合のみ、IRowsetFind では、次の比較がサポートされます。  
  
-   LT  
  
-   LE  
  
-   EQ  
  
-   GE  
  
-   GT  
  
-   NE  
  
-   IGNORE  
  
 その他の比較が実行されると、DB_E_BADCOMPAREOP が返されます。 これは OLE DB 仕様に従っています。  
  
## <a name="see-also"></a>参照  
 [日付と時刻の強化&#40;OLE DB&#41;](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
