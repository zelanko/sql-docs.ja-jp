---
title: PermissionSet 要素 (ASSL) |Microsoft ドキュメント
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
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a6246058af826a73b589f1854b0236de946a4d65
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165918"
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
|親要素|[ClrAssembly](../data-type/assembly-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*セーフ*|内部計算およびローカル データ アクセスのみ可能です。 *安全な*最も制限の厳しい権限セットです。 持つアセンブリによって実行されるコード*セーフ*アクセス許可がファイル、ネットワーク、環境変数、レジストリなどの外部システム リソースにアクセスできません。|  
|*Externalaccess です。*|*安全な*ファイル、ネットワーク、環境変数、レジストリなどの外部システム リソースにアクセスする追加機能を使用します。|  
|*制限なし*|制限のない内部および外部のリソースに無制限のアクセスを許可[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。 コードを内から実行する、 *Unrestricted*アセンブリはアンマネージ コードを呼び出すことができます。|  
  
 許可される値に対応する列挙`PermissionSet`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.PermissionSet>します。  
  
## <a name="see-also"></a>参照  
 [ComAssembly データ型&#40;ASSL&#41;](../data-type/comassembly-data-type-assl.md)   
 [Assemblies 要素&#40;ASSL&#41;](../collections/assemblies-element-assl.md)   
 [Database 要素&#40;ASSL&#41;](../objects/database-element-assl.md)   
 [サーバー要素&#40;ASSL&#41;](../objects/server-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  