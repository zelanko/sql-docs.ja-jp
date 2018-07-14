---
title: EnumString データ型 (XMLA) |Microsoft Docs
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
- EnumString Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- EnumString
- urn:schemas-microsoft-com:xml-analysis#EnumString
- http://schemas.microsoft.com/analysisservices/2003/engine#EnumString
helpviewer_keywords:
- EnumString data type
ms.assetid: 9214195e-4539-419b-95ec-b7aa75e033ab
caps.latest.revision: 29
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ea4f9057c05d7be5a5f8d8591d27460540a377fe
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37224032"
---
# <a name="enumstring-data-type-xmla"></a>EnumString データ型 (XMLA)
  特定の列挙子に対する名前付き定数のセットを表す派生データ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<EnumString>...</EnumString>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|`string`|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|なし|  
|派生要素|なし|  
  
## <a name="remarks"></a>コメント  
 XML for Analysis (XMLA) では、検証可能な設定値のセットに関して文字列値を制限するために列挙を使用します。 `EnumString` は標準 XML `string` データ型を使用します。 それぞれの名前付き定数の具体的な値は、列挙子定義によって指定されます。 追加することで列挙子が定義されている、 [DISCOVER_ENUMERATORS](../../schema-rowsets/xml/discover-enumerators-rowset.md)スキーマ行セットを使用して取得できます、 [Discover](../xml-elements-methods-discover.md) DISCOVER_ENUMERATORS メソッド要求の種類。  
  
 次の表のインスタンスでサポートされている列挙子[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。  
  
|列挙子|説明|  
|----------------|-----------------|  
|ProviderType|内の ProviderType 列をサポートしている、 [DISCOVER_DATASOURCES](../../schema-rowsets/xml/discover-datasources-rowset.md)スキーマ行セットによって返されるデータの種類を決定する、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。<br /><br /> さらに、この列挙は XMLA プロパティ `ProviderType` もサポートします。これは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスによってサポートされるプロバイダーの種類を決定します。 この列挙は DISCOVER_DATASOURCES スキーマ行セット内でも使用されます。<br /><br /> 詳細については`ProviderType`を参照してください[サポートされる XMLA プロパティ&#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md)します。|  
|AuthenticationMode|DISCOVER_DATASOURCES スキーマ行セット内の AuthenticationMode 列をサポートします。これは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスへのアクセス時に渡される必要のあるセキュリティ資格情報を決定します。|  
|PropertyAccessType|内の PropertyAccessType 列をサポートしている、 [DISCOVER_PROPERTIES](../../schema-rowsets/xml/discover-properties-rowset.md)スキーマ行セット、XMLA プロパティの使用可能なアクセスの種類を決定します。|  
|StateSupport|XMLA プロパティ `StateSupport` をサポートします。これは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスによってサポートされる状態保持のレベルを決定します。<br /><br /> 詳細については`StateSupport`を参照してください[サポートされる XMLA プロパティ&#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md)します。|  
|StateActionVerb|SOAP ヘッダー内の XMLA によってサポートされ、セッションの開始、識別、および終了に使用される動詞の一覧を含みます。<br /><br /> セッションの詳細については、次を参照してください。[接続の管理とセッション&#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)します。|  
|ResultsetFormat|XMLA プロパティをサポートしている`Format`で返されるデータの種類を決定する、[ルート](../xml-elements-properties/root-element-xmla.md)要素。<br /><br /> 詳細については`Format`を参照してください[サポートされる XMLA プロパティ&#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md)します。|  
|ResultsetAxisFormat|XMLA プロパティ `AxisFormat` をサポートします。これは、多次元データを含む `root` 要素内に返される軸情報の形式を決定します。<br /><br /> 詳細については`AxisFormat`を参照してください[サポートされる XMLA プロパティ&#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md)します。|  
|ResultsetContents|XMLA プロパティ `Content` をサポートします。これは、`root` 要素内にメタデータまたはデータが返されるかどうかを決定します。<br /><br /> 詳細については`Content`を参照してください[サポートされる XMLA プロパティ&#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md)します。|  
|MDXSupportLevel|XMLA プロパティ `MDXSupport` をサポートします。これは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンス上で利用可能な多次元式 (MDX) サポートのレベルを示します。<br /><br /> 詳細については`MDXSupport`を参照してください[サポートされる XMLA プロパティ&#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md)します。|  
  
## <a name="see-also"></a>参照  
 [XML データ型&#40;XMLA&#41;](xml-data-types-xmla.md)  
  
  
