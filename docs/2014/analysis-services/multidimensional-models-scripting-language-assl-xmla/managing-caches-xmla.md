---
title: キャッシュの管理 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- XMLA, cache
- XML for Analysis, cache
- clearing cache
- cache [Analysis Services]
ms.assetid: afad5c39-d4c3-4307-b3b9-a06617da0028
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8d4d95e556059709f1d4e5a0fc069b6da5ed289c
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/26/2018
ms.locfileid: "50146554"
---
# <a name="managing-caches-xmla"></a>キャッシュの管理 (XMLA)
  使用することができます、 [ClearCache](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/clearcache-element-xmla) XML for Analysis (XMLA)、指定したディメンションまたはパーティションのキャッシュをクリアするコマンド。 キャッシュの力をクリアする[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]そのオブジェクトのキャッシュを再構築します。  
  
## <a name="specifying-objects"></a>オブジェクトの指定  
 [オブジェクト](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)のプロパティ、`ClearCache`コマンドは、次のオブジェクトの 1 つのみのオブジェクト参照を含めることができます。 以下に該当しないオブジェクトに対するオブジェクト参照が含まれる場合、エラーが発生します。  
  
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
  
  
