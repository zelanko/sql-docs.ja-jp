---
title: Edition 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Edition Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Edition
helpviewer_keywords:
- Edition element
ms.assetid: 521e1286-097e-494f-b036-61047096e87e
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8a94ed085a345100579b3305fa43e7e360fe8258
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37245662"
---
# <a name="edition-element-assl"></a>Edition 要素 (ASSL)
  インスタンスの読み取り専用エディションを含む[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]によって表される、 [Server](../objects/server-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Server>  
      ...  
      <Edition>...</Edition>  
   ...  
</Server>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[[サーバー]](../objects/server-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Edition` 要素は、どのエディションの [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] がインストールされているかを示します。 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|説明|  
|-----------|-----------------|  
|*Standard*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (32 ビット プロセッサ向け) の standard エディションです。|  
|*Enterprise*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 32 ビット プロセッサの Enterprise エディションです。|  
|*EnterpriseCore*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Enterprise edition: core-based Licensing (32 ビット プロセッサ向け)。|  
|*BusinessIntelligence*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 32 ビット プロセッサの business Intelligence エディションです。|  
|*Developer*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Developer edition (32 ビット プロセッサ向け)|  
|*評価版*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Evaluation エディション (64 ビット プロセッサ向け) です。|  
|*地元の*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ローカルのエディション (32 ビット プロセッサ向け) です。|  
|*Standard64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Standard のエディション (64 ビット プロセッサ向け) です。|  
|*Enterprise64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 64 ビット プロセッサでの Enterprise エディションです。|  
|*EnterpriseCore64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Enterprise edition: core-based Licensing (64 ビット プロセッサ向け)。|  
|*BusinessIntelligence64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 64 ビット プロセッサでの business Intelligence エディションです。|  
|*Developer64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Developer エディション (64 ビット プロセッサ向け)|  
|*Evaluation64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Evaluation エディション (64 ビット プロセッサ向け) です。|  
|*Local64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ローカルのエディション (64 ビット プロセッサ向け) です。|  
  
 許容された値に対応する列挙`ServerEdition`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ServerEdition>します。  
  
## <a name="see-also"></a>参照  
 [Version 要素&#40;ASSL&#41;](version-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
