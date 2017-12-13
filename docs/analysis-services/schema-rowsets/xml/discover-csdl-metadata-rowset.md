---
title: "DISCOVER_CSDL_METADATA 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: a2d3cffd-a2c4-411c-b244-9e41ebe30939
caps.latest.revision: "22"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3679e15b62a746cba1322bdf85691e313839ba46
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="discovercsdlmetadata-rowset"></a>DISCOVER_CSDL_METADATA 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]に関する情報を返します、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データ モデル (テーブルまたは多次元)、CSDLBI 形式 (Conceptual Schema Definition Language BI 注釈付き) でモデルの定義を提供します。 CSDLBI は、Entity Data Framework によって使用される XML スキーマである CSDL に基づくもので、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーと [!INCLUDE[ssCrescent](../../../includes/sscrescent-md.md)] クライアントの間の通信に使用されます。 ビジネス インテリジェンス (BI) 注釈は、テーブル モデルとテーブル モデル内のオブジェクトに関する追加のメタデータを提供します。 テーブル データ モデルの詳細については、「[ビジネス インテリジェンス向け CSDL 注釈 &#40;CSDLBI&#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdl-annotations-for-business-intelligence-csdlbi.md)」を参照してください。  
  
 返される行セットは、コマンドのセキュリティ コンテキストの影響を受けます。 サーバーから CSDL 定義を取得するには、Analysis Services インスタンスの読み取り権限が必要です。  
  
 行セット要求を発行するクライアントの言語識別子はコマンドの接続文字列に組み込まれており、行セットの一部として返される各種プロパティの表示言語に影響を及ぼします。  言語識別子の影響を受ける可能性のあるプロパティとその説明については、「解説」を参照してください。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DISCOVER_CSDL_METADATA** 行セットには、次の列が含まれています。  
  
|**列名**|**型インジケーター**|**制限**|**Description**|  
|---------------------|------------------------|---------------------|---------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|可|CSDLBI 記述の要求対象となるデータベースの名前を指定します。 省略した場合は、現在のデータベースが使用されます。<br /><br /> この制限は、すべての種類のモデルに対して必要です。|  
|**PERSPECTIVE_ID**|**DBTYPE_WSTR**|可|CATALOG_NAME によって指定されたモデルに定義されているパースペクティブの ID を指定します。<br /><br /> 省略可能な制限。 すべての種類のモデルに適用されます。|  
|**PERSPECTIVE_NAME**|**DBTYPE_WSTR**|可|CATALOG_NAME によって指定されたモデルに定義されているパースペクティブの名前を指定します。<br /><br /> この制限は、テーブル モデルにパースペクティブが含まれるか、多次元ソリューションに複数のキューブまたはパースペクティブが含まれる場合に必要です。|  
|**メタデータ**|**DBTYPE_WSTR**|不可|データ ソースとそのプロパティの XML 定義を CSDLBI スキーマに従って保持する文字列です。|  
|**CUBE_ID**|**DBTYPE_WSTR**|可|文字列識別子。<br /><br /> この制限は、多次元データベースに対しては省略可能です。 複数のキューブが利用可能であるときに、制限が省略されると、既定のキューブが返されます。|  
  
## <a name="remarks"></a>解説  
 DISCOVER_CSDL_METADATA には、次の要件があります。  
  
-   CATALOG_NAME の制限を使用してデータベースが指定されていないと、DISCOVER 要求は失敗します。  
  
-   テーブル モデルでモデルに複数のパースペクティブがある場合は、パースペクティブ ID が必要です。  
  
-   多次元モデルでは、カタログの名前とキューブ (パースペクティブ) の名前の両方が必要です。  
  
-   制限としてパースペクティブが指定された場合、モデルの場合と同じ CSDL 行セットが返されます。 ただし、モデルには含まれているが指定されたパースペクティブには含まれていないオブジェクトはすべて **Hidden** = True としてマークされます。  
  
-   テーブルおよび列に関して、DISCOVER 要求は、常にキューブ ディメンションからの値を出力します。 キューブ ディメンションのプロパティが設定されていない場合は、ディメンションからの値が返されます。  
  
-   DISCOVER 要求は、セマンティック エラーを含んだメジャーまたは計算列を返すことができません。  
  
-   DISCOVER 要求は、プロパティ値を持たないオブジェクトの情報は一切返しません。 また、既定値が使用された属性の値も、DISCOVER 要求からは返されません。  
  
 行セットとして返された XML 文字列には、次の言語固有のプロパティまたは値が含まれていることがあります。 たとえば、LCID が 0403 (Catalan Spanish) であるクライアントから行セット要求を発行した場合、プロパティからは、Catalan Spanish に応じた適切な値が返されます。 サーバー上に翻訳が存在しない場合は、サーバーの既定の言語の文字列が返されます。  
  
-   Caption  
  
-   Qualifier  
  
-   SortDirection  
  
-   IsRightToLeft  
  
## <a name="example"></a>例  
 **テーブル**  
  
 次の XMLA クエリは、AdventureWorks 2012 のテーブル モデル サンプルの CSDL 表現を返します。 各テーブル ソリューションには 1 つのモデルだけを含めることができるので、PERSPECTIVE_NAME 制限を空白にできます。 ただしこのモデルには複数のパースペクティブが含まれています。  
  
```  
  
<Discover  xmlns="urn:schemas-microsoft-com:xml-analysis">  
     <RequestType>DISCOVER_CSDL_METADATA</RequestType>  
         <Restrictions>  
            <RestrictionList>  
                <CATALOG_NAME>AdventureWorks2012Tabular</CATALOG_NAME>  
                <PERSPECTIVE_NAME>EMPLOYEE</PERSPECTIVE_NAME>  
                <VERSION>2.0</VERSION>  
            </RestrictionList>  
         </Restrictions>  
         <Properties>  
                <PropertyList>  
                </PropertyList>  
         </Properties>  
</Discover>  
  
```  
  
## <a name="example"></a>例  
 **多次元**  
  
 次の XMLA クエリでは、Contoso Operations キューブの CSDLBI 表現を返します。 VERSION 制限は多次元データベースへのクエリを実行するために必要です。 Contoso Retail データベースには 2 つのキューブが含まれているため、Operations キューブが PERSPECTIVE_NAME 制限を使用して参照されています。  
  
```  
  
<Discover  xmlns="urn:schemas-microsoft-com:xml-analysis">  
     <RequestType>DISCOVER_CSDL_METADATA</RequestType>  
         <Restrictions>  
            <RestrictionList>  
                <CATALOG_NAME>Contoso_Retail</CATALOG_NAME>  
                <PERSPECTIVE_NAME>Operation</PERSPECTIVE_NAME>  
                <VERSION>2.0</VERSION>  
            </RestrictionList>  
         </Restrictions>  
         <Properties>  
                <PropertyList>  
                </PropertyList>  
         </Properties>  
 </Discover>  
  
```  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|値|  
|--------------|-----------|  
|GUID|3444B255-171E-4cb9-AD98-19E57888A75F|  
|ADOMDNAME|Csdl|  
  
## <a name="see-also"></a>参照  
 [Analysis Services のスキーマ行セット](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)   
 [Business Intelligence &#40; 向けの CSDL 注釈CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdl-annotations-for-business-intelligence-csdlbi.md)  
  
  
