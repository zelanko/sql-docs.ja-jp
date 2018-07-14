---
title: キャッシュの管理 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- XMLA, cache
- XML for Analysis, cache
- clearing cache
- cache [Analysis Services]
ms.assetid: afad5c39-d4c3-4307-b3b9-a06617da0028
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: da13c86e86a2f51719a9d4f0aedfda33935766ae
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37180819"
---
# <a name="managing-caches-xmla"></a>キャッシュの管理 (XMLA)
  使用することができます、 [ClearCache](../xmla/xml-elements-commands/clearcache-element-xmla.md) XML for Analysis (XMLA)、指定したディメンションまたはパーティションのキャッシュをクリアするコマンド。 キャッシュの力をクリアする[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]そのオブジェクトのキャッシュを再構築します。  
  
## <a name="specifying-objects"></a>オブジェクトの指定  
 [オブジェクト](../xmla/xml-elements-properties/object-element-xmla.md)のプロパティ、`ClearCache`コマンドは、次のオブジェクトの 1 つのみのオブジェクト参照を含めることができます。 以下に該当しないオブジェクトに対するオブジェクト参照が含まれる場合、エラーが発生します。  
  
 [データベース]  
 データベースに含まれるすべてのディメンションおよびパーティションのキャッシュを消去します。  
  
 [ディメンション]  
 指定されたディメンションのキャッシュを消去します。  
  
 Cube  
 キューブのメジャー グループに含まれるすべてのパーティションのキャッシュを消去します。  
  
 [メジャー グループ]  
 メジャー グループに含まれるすべてのパーティションのキャッシュを消去します。  
  
 パーティション  
 指定されたパーティションのキャッシュを消去します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services での XMLA による開発](developing-with-xmla-in-analysis-services.md)  
  
  
