---
title: キャッシュの管理 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XMLA, cache
- XML for Analysis, cache
- clearing cache
- cache [Analysis Services]
ms.assetid: afad5c39-d4c3-4307-b3b9-a06617da0028
author: minewiskan
ms.author: owend
ms.openlocfilehash: cdc5bcd2e0500749edfa298a871b6fec7243ddfb
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544984"
---
# <a name="managing-caches-xmla"></a>キャッシュの管理 (XMLA)
  XML for Analysis (XMLA) の[clearcache](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/clearcache-element-xmla)コマンドを使用して、指定したディメンションまたはパーティションのキャッシュを消去できます。 キャッシュをクリアすると、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] そのオブジェクトのキャッシュが強制的に再構築されます。  
  
## <a name="specifying-objects"></a>オブジェクトの指定  
 コマンドの[object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)プロパティには、 `ClearCache` 次のいずれかのオブジェクトに対してのみオブジェクト参照を含めることができます。 以下に該当しないオブジェクトに対するオブジェクト参照が含まれる場合、エラーが発生します。  
  
 データベース  
 データベースに含まれるすべてのディメンションおよびパーティションのキャッシュを消去します。  
  
 Dimension  
 指定されたディメンションのキャッシュを消去します。  
  
 Cube  
 キューブのメジャー グループに含まれるすべてのパーティションのキャッシュを消去します。  
  
 [メジャー グループ]  
 メジャー グループに含まれるすべてのパーティションのキャッシュを消去します。  
  
 Partition  
 指定されたパーティションのキャッシュを消去します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services での XMLA による開発](developing-with-xmla-in-analysis-services.md)  
  
  
