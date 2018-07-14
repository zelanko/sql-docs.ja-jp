---
title: PermissionSet 要素 (ASSL) |Microsoft Docs
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
- PermissionSet Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- PermissionSet
helpviewer_keywords:
- PermissionSet element
ms.assetid: da5a9175-48e4-4b5e-a780-3e0077939974
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 471ef43aea9fadcca7ab8a4a36870a3bdddee22f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37263468"
---
# <a name="permissionset-element-assl"></a>PermissionSet 要素 (ASSL)
  関連付けられているアクセス許可セットを識別、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework アセンブリ。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ClrAssembly>  
   ...  
   <PermissionSet>...</PermissionSet>  
  
</ClrAssembly>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*Safe*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ClrAssembly](../data-type/assembly-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*Safe*|内部計算およびローカル データ アクセスのみ可能です。 *安全な*は最も制限の厳しい権限セットです。 持つアセンブリによって実行されるコード*セーフ*アクセス許可がファイル、ネットワーク、環境変数、またはレジストリなどの外部システム リソースにアクセスできません。|  
|*Externalaccess です。*|*安全な*ファイル、ネットワーク、環境変数、レジストリなどの外部システム リソースにアクセスを追加できます。|  
|*無制限*|無制限内外両方のリソースに無制限のアセンブリへのアクセス許可[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。 内から実行されるコード、 *Unrestricted*アセンブリはアンマネージ コードを呼び出すことができます。|  
  
 許容された値に対応する列挙体`PermissionSet`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.PermissionSet>します。  
  
## <a name="see-also"></a>参照  
 [ComAssembly データ型&#40;ASSL&#41;](../data-type/comassembly-data-type-assl.md)   
 [Assemblies 要素&#40;ASSL&#41;](../collections/assemblies-element-assl.md)   
 [Database 要素&#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Server 要素&#40;ASSL&#41;](../objects/server-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
