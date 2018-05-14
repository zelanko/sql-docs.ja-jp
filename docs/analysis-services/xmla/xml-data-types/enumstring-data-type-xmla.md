---
title: EnumString データ型 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bb1a181a73a6e6a2f4998fb12381c522afb4e510
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="enumstring-data-type-xmla"></a>EnumString データ型 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  特定の列挙子に対する名前付き定数のセットを表す派生データ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<EnumString>...</EnumString>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|**文字列**|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|なし|  
|派生要素|なし|  
  
## <a name="remarks"></a>解説  
 XML for Analysis (XMLA) では、検証可能な設定値のセットに関して文字列値を制限するために列挙を使用します。 **EnumString**標準 XML を使用して**文字列**データ型。 それぞれの名前付き定数の具体的な値は、列挙子定義によって指定されます。 追加することで列挙子が定義されている、 [DISCOVER_ENUMERATORS](../../../analysis-services/schema-rowsets/xml/discover-enumerators-rowset.md)スキーマ行セットを使用して取得できます、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) DISCOVER_ENUMERATORS を持つメソッド要求の種類。  
  
 次の表のインスタンスでサポートされている列挙子[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
|列挙子|Description|  
|----------------|-----------------|  
|ProviderType|内の ProviderType 列をサポートしている、 [DISCOVER_DATASOURCES](../../../analysis-services/schema-rowsets/xml/discover-datasources-rowset.md)スキーマ行セットによって返されるデータの種類を決定する、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。<br /><br /> この列挙体は、XMLA プロパティもサポートしています。 **ProviderType**、でサポートされているプロバイダーの種類を決定する、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。 この列挙は DISCOVER_DATASOURCES スキーマ行セット内でも使用されます。<br /><br /> 詳細については**ProviderType**を参照してください[サポートされる XMLA プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md)です。|  
|AuthenticationMode|DISCOVER_DATASOURCES スキーマ行セット内の AuthenticationMode 列をサポートします。これは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスへのアクセス時に渡される必要のあるセキュリティ資格情報を決定します。|  
|PropertyAccessType|内の PropertyAccessType 列をサポートしている、 [DISCOVER_PROPERTIES](../../../analysis-services/schema-rowsets/xml/discover-properties-rowset.md)スキーマ行セットを XMLA プロパティのアクセスの種類を決定します。|  
|StateSupport|XMLA プロパティをサポートして**StateSupport**、によってサポートされる状態保持のレベルを決定する、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。<br /><br /> 詳細については**StateSupport**を参照してください[サポートされる XMLA プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md)です。|  
|StateActionVerb|SOAP ヘッダー内の XMLA によってサポートされ、セッションの開始、識別、および終了に使用される動詞の一覧を含みます。<br /><br /> セッションの詳細については、次を参照してください。[接続の管理とセッション&#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)です。|  
|ResultsetFormat|XMLA プロパティをサポートして**形式**で返されるデータの種類を決定する、[ルート](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)要素。<br /><br /> 詳細については**形式**を参照してください[サポートされる XMLA プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md)です。|  
|ResultsetAxisFormat|XMLA プロパティをサポートして**AxisFormat**で返される軸情報の形式を決定する、**ルート**多次元データを含む要素です。<br /><br /> 詳細については**AxisFormat**を参照してください[サポートされる XMLA プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md)です。|  
|ResultsetContents|XMLA プロパティをサポートして**コンテンツ**でのメタデータやデータが返されるかどうかを決定する、**ルート**要素。<br /><br /> 詳細については**コンテンツ**を参照してください[サポートされる XMLA プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md)です。|  
|MDXSupportLevel|XMLA プロパティをサポートして**MDXSupport**で利用可能な多次元式 (MDX) サポートのレベルを示す、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。<br /><br /> 詳細については**MDXSupport**を参照してください[サポートされる XMLA プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md)です。|  
  
## <a name="see-also"></a>参照  
 [XML データ型&#40;XMLA&#41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)  
  
  
