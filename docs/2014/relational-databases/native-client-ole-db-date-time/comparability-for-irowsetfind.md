---
title: IRowsetFind での比較 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRowsetFind comparability [ODBC]
ms.assetid: 7d148b56-9bbe-4e55-b31f-43f115705402
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 991c475fee024c1e04ba1f70db3f22f56685d1ec
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085866"
---
# <a name="comparability-for-irowsetfind"></a>IRowsetFind での比較
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
 [日付と時刻の強化&#40;OLE DB&#41;](date-and-time-improvements-ole-db.md)  
  
  