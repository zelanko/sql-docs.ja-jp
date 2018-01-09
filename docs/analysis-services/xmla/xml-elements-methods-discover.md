---
title: "Discover メソッド (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/14/2016
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Discover Method
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#
- http://schemas.microsoft.com/analysisservices/2003/engine#
- microsoft.xml.analysis.discover
- urn:schemas-microsoft-com:xml-analysis#Discover
- Discover
helpviewer_keywords: Discover method
ms.assetid: 0eb52d88-c081-416e-a229-610e4373b0b3
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c7825925accedb8a32ab05af2f67efc02e5ae94b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="xml-elements---methods---discover"></a>XML 要素の方法 - 検出します。
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]インスタンスから使用可能なデータベースまたは特定のオブジェクトに関する詳細情報の一覧などの情報を取得[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]です。 使用して取得データ、 **Discover**メソッドは渡されたパラメーターの値によって異なります。  
  
 **Namespace** urn: スキーマ-microsoft-{urn:schemas-microsoft-com:xml-sql} の分析  
  
 **SOAP アクション**"urn: スキーマ-microsoft-{urn:schemas-microsoft-com:xml-sql}-分析: 検出"  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Discover>  
   <RequestType>...</RequestType>  
   <Restrictions>...</Restrictions>  
   <Properties>...</Properties>  
</Discover>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|基数|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[プロパティ](../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md)、 [RequestType](../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md)、[制限](../../analysis-services/xmla/xml-elements-properties/restrictions-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 **Discover**メソッドに関するメタデータを要求する[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンスおよびオブジェクト。 XMLA を使用してメタデータが返される[行セット](../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md)データ型。  
 
> [!TIP] 
> XML コマンドに慣れていない場合は、XMLA クエリ テンプレートをクリックして、上、**クエリ**Management Studio で、クエリを作成し、パラメーターを追加するツールバーです。 詳細については、「 [SQL Server Management Studio での Analysis Services テンプレートの使用](../../analysis-services/instances/use-analysis-services-templates-in-sql-server-management-studio.md)」を参照してください。 
  
## <a name="example"></a>例  
 次のコード サンプルで、クライアントは送信、 **Discover**からキューブの一覧を要求する呼び出し、[!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)]サンプル[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース。  
  
```  
<Discover xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <RequestType>MDSCHEMA_CUBES</RequestType>  
   <Restrictions>  
      <RestrictionList>  
         <CATALOG_NAME>Adventure Works DW Multidimensional 2012</CATALOG_NAME>  
      </RestrictionList>  
   </Restrictions>  
   <Properties>  
      <PropertyList>  
         <DataSourceInfo>Provider=MSOLAP;Data Source=local;</DataSourceInfo>  
         <Catalog>Adventure Works DW Multidimensional 2012</Catalog>  
         <Format>Tabular</Format>  
      </PropertyList>  
   </Properties>  
</Discover>  
```  
  
## <a name="see-also"></a>参照  
 [XML データ型 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [方法 &#40; を実行します。XMLA &#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)   
 [メソッドと #40 です。XMLA &#41;](../../analysis-services/xmla/xml-elements-methods.md)   
 [XML 要素 &#40;です。XMLA &#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [Analysis Services のスキーマ行セット](../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
