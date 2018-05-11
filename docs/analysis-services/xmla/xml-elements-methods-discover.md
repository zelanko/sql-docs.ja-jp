---
title: Discover メソッド (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4bc359e24664f97db41acd87914194731c37e325
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="xml-elements---methods---discover"></a>XML 要素の方法 - 検出します。
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  インスタンスから使用可能なデータベースまたは特定のオブジェクトに関する詳細情報の一覧などの情報を取得[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]です。 使用して取得データ、 **Discover**メソッドは渡されたパラメーターの値によって異なります。  
  
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
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
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
 [XML データ型 & #40 です。XMLA & #41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [メソッドを実行する&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)   
 [メソッド&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods.md)   
 [XML 要素 & #40 です。XMLA & #41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [Analysis Services のスキーマ行セット](../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
