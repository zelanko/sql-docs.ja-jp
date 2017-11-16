---
title: "キャッシュ (XMLA) の管理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- XMLA, cache
- XML for Analysis, cache
- clearing cache
- cache [Analysis Services]
ms.assetid: afad5c39-d4c3-4307-b3b9-a06617da0028
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 69fc72149887598efe1c84c35c88fa24c7cdadbc
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="managing-caches-xmla"></a>キャッシュの管理 (XMLA)
  使用することができます、 [ClearCache](../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md) XML for Analysis (XMLA) を指定したディメンションまたはパーティションのキャッシュをクリアするコマンド。 キャッシュの強制をクリアする[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]をそのオブジェクトのキャッシュを再構築します。  
  
## <a name="specifying-objects"></a>オブジェクトの指定  
 [オブジェクト](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)のプロパティ、 **ClearCache**コマンドは、次のオブジェクトの 1 つだけに対するオブジェクト参照を含めることができます。 以下に該当しないオブジェクトに対するオブジェクト参照が含まれる場合、エラーが発生します。  
  
 データベース  
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
 [Analysis Services の XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  

