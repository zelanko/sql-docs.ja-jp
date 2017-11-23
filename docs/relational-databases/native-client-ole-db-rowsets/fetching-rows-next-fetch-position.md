---
title: "次のフェッチ位置 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
ms.assetid: 9ef74b3f-c9c0-492f-9b93-d65738a61abd
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c0e1b54804a64941840bc62b003564e012f07088
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="fetching-rows---next-fetch-position"></a>行のフェッチで次のフェッチ位置
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは常に追跡の次のフェッチ位置のためをへの呼び出しのシーケンス、 **GetNextRows**メソッド (の方向、または介在する変更がへの呼び出しにスキップせず、 **FindNextRow**、**シーク**、または**RestartPosition**メソッド) をスキップまたは任意の行を繰り返ししないで行セット全体を読み取ります。 次のフェッチ位置が変更されたかを呼び出して**irowset::getnextrows**、 **irowset::restartposition**、または**irowsetindex::seek**、またはを呼び出すことによって**FindNextRow**と null *pBookmark*値。 呼び出す**FindNextRow** null 以外の値*pBookmark*値では次のフェッチ位置には影響しません。  
  
## <a name="see-also"></a>参照  
 [行のフェッチ](../../relational-databases/native-client-ole-db-rowsets/fetching-rows.md)  
  
  
