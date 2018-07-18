---
title: 次のフェッチ位置 |Microsoft Docs
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
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
ms.assetid: 9ef74b3f-c9c0-492f-9b93-d65738a61abd
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d6fa0247cafa0d0750f224e3b369965fd4e7989
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37423571"
---
# <a name="next-fetch-position"></a>次のフェッチ位置
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは常に追跡の次のフェッチ位置のためをへの呼び出しのシーケンス、 **GetNextRows**メソッド (の方向、または介在する変更の呼び出しをスキップ、なし、 **FindNextRow**、**シーク**、または**RestartPosition**メソッド) をスキップまたは任意の行を繰り返しせずに行セット全体を読み取ります。 呼び出すか、次のフェッチ位置が変更された**irowset::getnextrows**、 **irowset::restartposition**、または**irowsetindex::seek**を呼び出すことによって、または**FindNextRow** null で*pBookmark*値。 呼び出す**FindNextRow**値に null 以外*pBookmark*値では、次のフェッチ位置には影響しません。  
  
## <a name="see-also"></a>参照  
 [行のフェッチ](fetching-rows.md)  
  
  
