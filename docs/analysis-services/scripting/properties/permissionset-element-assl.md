---
title: "PermissionSet 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- PermissionSet Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- PermissionSet
helpviewer_keywords:
- PermissionSet element
ms.assetid: da5a9175-48e4-4b5e-a780-3e0077939974
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d1448c3db59f149697fa429e6d122d9d20fd403f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

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
|既定値|*セーフ*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*セーフ*|内部計算およびローカル データ アクセスのみ可能です。 *安全な*最も制限の厳しい権限セットです。 持つアセンブリによって実行されるコード*セーフ*アクセス許可がファイル、ネットワーク、環境変数、レジストリなどの外部システム リソースにアクセスできません。|  
|*Externalaccess です。*|*安全な*ファイル、ネットワーク、環境変数、レジストリなどの外部システム リソースにアクセスする追加機能を使用します。|  
|*制限なし*|制限のない内部および外部のリソースに無制限のアクセスを許可[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。 コードを内から実行する、 *Unrestricted*アセンブリはアンマネージ コードを呼び出すことができます。|  
  
 許可される値に対応する列挙**PermissionSet**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.PermissionSet>します。  
  
## <a name="see-also"></a>参照  
 [ComAssembly データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/comassembly-data-type-assl.md)   
 [Assemblies 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/collections/assemblies-element-assl.md)   
 [Database 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [Server 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

