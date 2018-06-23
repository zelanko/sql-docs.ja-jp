---
title: Irow::getcolumns を使用して |Microsoft ドキュメント
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
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- GetColumns method
ms.assetid: 1f5d2e03-e6fe-4ea1-b71d-55d02b5d59ae
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 37c7895a888852a8acb0b73a4b44e297e1ea3318
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085646"
---
# <a name="using-irowgetcolumns"></a>IRow::GetColumns の使用
  **IRow**実装により、列に順方向専用の順次アクセスされます。 1 回の呼び出しを含む行のすべての列にアクセスすることができますか、 **irow::getcolumns**呼び出したり**irow::getcolumns**行に複数の列をアクセスするたびに複数回です。  
  
 複数回呼び出す**irow::getcolumns**重ならないようにします。 たとえば、最初の呼び出し**irow::getcolumns**に列 1、2、および 3、2 番目の呼び出しが取得**irow::getcolumns**列 4、5 および 6 を呼び出す必要があります。 場合を後で呼び出す**irow::getcolumns**重なっているため、の状態フラグ (DBCOLUMNACCESS の dwstatus フィールド) が DBSTATUS_E_UNAVAILABLE に設定します。  
  
## <a name="see-also"></a>参照  
 [IRow による 1 行のフェッチ](fetching-a-single-row-with-irow.md)  
  
  