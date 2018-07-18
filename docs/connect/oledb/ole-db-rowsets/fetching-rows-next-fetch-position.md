---
title: 次のフェッチ位置 |Microsoft ドキュメント
description: 行のフェッチで次のフェッチ位置
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 46e6e3b9898d6c1adbe4df4bdc2b33444b623df9
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2018
ms.locfileid: "35690115"
---
# <a name="fetching-rows---next-fetch-position"></a>行のフェッチで次のフェッチ位置
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver SQL サーバーが保持の追跡の次のフェッチ位置のためをへの呼び出しのシーケンス、 **GetNextRows**メソッド (の方向、または介在する変更がへの呼び出しにスキップせず、 **FindNextRow**、**シーク**、または**RestartPosition**メソッド) をスキップまたは任意の行を繰り返ししないで行セット全体を読み取ります。 次のフェッチ位置が変更されたかを呼び出して**irowset::getnextrows**、 **irowset::restartposition**、または**irowsetindex::seek**、またはを呼び出すことによって**FindNextRow**と null *pBookmark*値。 呼び出す**FindNextRow** null 以外の値*pBookmark*値では次のフェッチ位置には影響しません。  
  
## <a name="see-also"></a>参照  
 [行のフェッチ](../../oledb/ole-db-rowsets/fetching-rows.md)  
  
  
