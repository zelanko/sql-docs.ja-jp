---
title: Irow::getcolumns を使用して |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 21046f1ab8c25a9f929f8e6cf95281e74c157ae6
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37430051"
---
# <a name="using-irowgetcolumns"></a>IRow::GetColumns の使用
  **IRow**実装が列に順方向専用のシーケンシャル アクセスを許可します。 1 回の呼び出しを含む行のすべての列にアクセスする**irow::getcolumns**呼び出したり**irow::getcolumns**複数回、行内の複数の列をアクセスするたびにします。  
  
 複数回呼び出す**irow::getcolumns**が重なり合ってはなりません。 たとえば、最初の呼び出し**irow::getcolumns**に列 1、2、および 3、2 番目の呼び出しを取得します**irow::getcolumns**列 4、5、および 6 を呼び出す必要があります。 場合に後で呼び出す**irow::getcolumns**重なっているため、の状態フラグ (DBCOLUMNACCESS の dwstatus フィールド) が DBSTATUS_E_UNAVAILABLE に設定されます。  
  
## <a name="see-also"></a>参照  
 [IRow による 1 行のフェッチ](fetching-a-single-row-with-irow.md)  
  
  
