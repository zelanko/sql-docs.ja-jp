---
title: キャッシュ (XMLA) の管理 |Microsoft ドキュメント
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
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b40efd25088e90b3761d3532188d5bdadce7630c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176285"
---
# <a name="managing-caches-xmla"></a>キャッシュの管理 (XMLA)
  使用することができます、 [ClearCache](../xmla/xml-elements-commands/clearcache-element-xmla.md) XML for Analysis (XMLA) を指定したディメンションまたはパーティションのキャッシュをクリアするコマンド。 キャッシュの強制をクリアする[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]をそのオブジェクトのキャッシュを再構築します。  
  
## <a name="specifying-objects"></a>オブジェクトの指定  
 [オブジェクト](../xmla/xml-elements-properties/object-element-xmla.md)のプロパティ、`ClearCache`コマンドは、次のオブジェクトの 1 つだけに対するオブジェクト参照を含めることができます。 以下に該当しないオブジェクトに対するオブジェクト参照が含まれる場合、エラーが発生します。  
  
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
  
  