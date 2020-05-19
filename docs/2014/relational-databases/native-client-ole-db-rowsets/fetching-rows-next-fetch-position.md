---
title: 次のフェッチ位置 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
ms.assetid: 9ef74b3f-c9c0-492f-9b93-d65738a61abd
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 05d2c63c2d973416883562512ac45dd391f6c4b6
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82694515"
---
# <a name="next-fetch-position"></a>次のフェッチ位置
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、次のフェッチ位置を追跡します。これにより、 **GetNextRows**メソッド (スキップ、方向の変更、または**FindNextRow**、 **Seek**、または**RestartPosition**メソッドへの介在する呼び出しを除く) の一連の呼び出しによって行セット全体が読み取られます。行をスキップしたり、繰り返したりする必要はありません。 **IRowset::GetNextRows**、**IRowset::RestartPosition**、または **IRowsetIndex::Seek** を呼び出すか、*pBookmark* 値に NULL を指定して **FindNextRow** を呼び出すことにより、次のフェッチ位置が変更されます。 *pBookmark* 値に NULL 以外の値を指定して **FindNextRow** を呼び出しても、次のフェッチ位置には影響しません。  
  
## <a name="see-also"></a>参照  
 [行のフェッチ](fetching-rows.md)  
  
  
