---
title: ParentObject 要素 (XMLA) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ParentObject Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#ParentObject
- http://schemas.microsoft.com/analysisservices/2003/engine#ParentObject
- microsoft.xml.analysis.parentobject
helpviewer_keywords:
- ParentObject element
ms.assetid: f821f8f1-554a-4f16-bf09-262a9448e304
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 011f38f6f6b2bef8d167ee450d8f015b29a596b4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="parentobject-element-xmla"></a>ParentObject 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  親によって定義されているオブジェクトの作成に使用する親オブジェクトの識別子を含む[作成](../../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Create>  
   ...  
   <ParentObject>  
      <!-- Object reference -->  
   </ParentObject>  
   ...  
</Create>  
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
|親要素|[作成](../../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)|  
|子要素|必須の Analysis Services Scripting Language (ASSL) 要素。 オブジェクトとその先祖の ID 要素をリストすることによって指定された (を除く、**サーバー**オブジェクトです)。たとえば、次**ParentObject**要素が、パーティションを識別します。<br /><br /> `<ParentObject>`<br /><br /> `<DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>`<br /><br /> `<CubeID>Adventure Works</CubeID>`<br /><br /> `<MeasureGroupID>Internet Sales</MeasureGroupID>`<br /><br /> `<PartitionID>Inernet_Sales_2001</PartitionID>`<br /><br /> `</ParentObject>`|  
  
## <a name="remarks"></a>解説  
 識別子の出現順序は重要ではありません。  
  
## <a name="example"></a>例  
 次の例を作成、**マーケット バスケット**に含まれる、マイニング構造、[!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)]サンプル[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データベース。  
  
```  
<Create xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>database</DatabaseID>  
    </ParentObject>  
    <ObjectDefinition>  
        <MiningStructure xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
            <ID>Market Basket</ID>  
            <Name>Market Basket</Name>  
            <Source xsi:type="DataSourceViewBinding">  
                <DataSourceViewID>Adventure Works DW</DataSourceViewID>  
            </Source>  
            <Language>1033</Language>  
            <Collation>Latin1_General_CI_AS</Collation>  
            <Columns>  
                <Column xsi:type="ScalarMiningStructureColumn">  
                    <ID>Order Number</ID>  
                    <Name>Order Number</Name>  
                    <IsKey>true</IsKey>  
                    <Type>Text</Type>  
                    <Content>Key</Content>  
                    <KeyColumns>  
                        <KeyColumn>  
                            <NullProcessing>Error</NullProcessing>  
                            <DataType>WChar</DataType>  
                            <DataSize>20</DataSize>  
                            <Source xsi:type="ColumnBinding">  
                                <TableID>dbo_vAssocSeqOrders</TableID>  
                                <ColumnID>OrderNumber</ColumnID>  
                            </Source>  
                        </KeyColumn>  
                    </KeyColumns>  
                </Column>  
                <Column xsi:type="TableMiningStructureColumn">  
                    <Annotations>  
                        <Annotation>  
                            <Name>MDXFilterComponent</Name>  
                            <Value />  
                        </Annotation>  
                    </Annotations>  
                    <ID>v Assoc Seq Line Items</ID>  
                    <Name>v Assoc Seq Line Items</Name>  
                    <ForeignKeyColumns>  
                        <ForeignKeyColumn>  
                            <NullProcessing>Error</NullProcessing>  
                            <DataType>WChar</DataType>  
                            <DataSize>20</DataSize>  
                            <Source xsi:type="ColumnBinding">  
                                <TableID>dbo_vAssocSeqLineItems</TableID>  
                                <ColumnID>OrderNumber</ColumnID>  
                            </Source>  
                        </ForeignKeyColumn>  
                    </ForeignKeyColumns>  
                    <Columns>  
                        <Column xsi:type="ScalarMiningStructureColumn">  
                            <ID>Model</ID>  
                            <Name>Model</Name>  
                            <IsKey>true</IsKey>  
                            <Type>Text</Type>  
                            <Content>Key</Content>  
                            <KeyColumns>  
                                <KeyColumn>  
                                    <DataType>WChar</DataType>  
                                    <DataSize>50</DataSize>  
                                    <Source xsi:type="ColumnBinding">  
                                        <TableID>dbo_vAssocSeqLineItems</TableID>  
                                        <ColumnID>Model</ColumnID>  
                                    </Source>  
                                </KeyColumn>  
                            </KeyColumns>  
                        </Column>  
                    </Columns>  
                </Column>  
            </Columns>  
            <MiningModels>  
                <MiningModel>  
                    <ID>Market Basket</ID>  
                    <Name>Association</Name>  
                    <Algorithm>Microsoft_Association_Rules</Algorithm>  
                    <AlgorithmParameters>  
                        <AlgorithmParameter>  
                            <Name>MINIMUM_PROBABILITY</Name>  
                            <Value xsi:type="xsd:double">0.1</Value>  
                        </AlgorithmParameter>  
                        <AlgorithmParameter>  
                            <Name>MINIMUM_SUPPORT</Name>  
                            <Value xsi:type="xsd:double">0.01</Value>  
                        </AlgorithmParameter>  
                    </AlgorithmParameters>  
                    <Columns>  
                        <Column>  
                            <ID>Order Number</ID>  
                            <Name>Order Number</Name>  
                            <SourceColumnID>Order Number</SourceColumnID>  
                            <Usage>Key</Usage>  
                        </Column>  
                        <Column>  
                            <ID>v Assoc Seq Line Items</ID>  
                            <Name>v Assoc Seq Line Items</Name>  
                            <SourceColumnID>v Assoc Seq Line Items</SourceColumnID>  
                            <Usage>Predict</Usage>  
                            <Columns>  
                                <Column>  
                                    <ID>Model</ID>  
                                    <Name>Model</Name>  
                                    <SourceColumnID>Model</SourceColumnID>  
                                    <Usage>Key</Usage>  
                                </Column>  
                            </Columns>  
                        </Column>  
                    </Columns>  
                    <Language>1033</Language>  
                    <Collation>Latin1_General_CI_AS</Collation>  
                </MiningModel>  
            </MiningModels>  
        </MiningStructure>  
    </ObjectDefinition>  
</Create>  
```  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
