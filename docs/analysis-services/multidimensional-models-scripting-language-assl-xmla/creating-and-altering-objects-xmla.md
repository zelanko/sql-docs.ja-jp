---
title: "作成して、オブジェクト (XMLA) の変更 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- objects [XML for Analysis]
- subordinate objects [XML for Analysis]
- XML for Analysis, objects
- modifying objects
- removing objects
- deleting objects
- XMLA, objects
ms.assetid: a2080867-e130-440c-92eb-f768869f34a8
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6906c6dbab99923983cbfa4e75c35c6f3c0f5073
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="creating-and-altering-objects-xmla"></a>オブジェクトの作成と変更 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
主要なオブジェクトは、個別に作成、変更、削除することができます。 主要なオブジェクトには以下のオブジェクトが含まれます。  
  
-   サーバー  
  
-   データベース  
  
-   ディメンション  
  
-   キューブ  
  
-   メジャー グループ  
  
-   パーティション  
  
-   パースペクティブ  
  
-   [マイニング モデル]  
  
-   ロール  
  
-   サーバーまたはデータベースに関連付けられているコマンド  
  
-   [データ ソース]  
  
 使用する、[作成](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)のインスタンスで、主要なオブジェクトを作成するコマンド[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、および[Alter](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)インスタンス上の既存の主要なオブジェクトを変更するコマンド。 使用して両方のコマンドは、実行、 [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドです。  
  
## <a name="creating-objects"></a>オブジェクトを作成します。  
 使用してオブジェクトを作成する場合、**作成**メソッド、親オブジェクトを含むまず特定する必要があります、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]オブジェクトを作成します。 内のオブジェクト参照を提供することにより、親オブジェクトを識別する、 [ParentObject](../../analysis-services/xmla/xml-elements-properties/parentobject-element-xmla.md)のプロパティ、**作成**コマンド。 それぞれのオブジェクト参照には親オブジェクトを一意に識別するために必要なオブジェクト識別子が含まれています、**作成**コマンド。 オブジェクト参照の詳細については、次を参照してください。[定義とオブジェクトを識別する &#40;です。XMLA &#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/defining-and-identifying-objects-xmla.md).  
  
 たとえば、キューブに新しいメジャー グループを作成するには、キューブへのオブジェクト参照を指定する必要があります。 キューブ内のオブジェクトの参照、 **ParentObject**プロパティが含まれています、データベース識別子と、キューブ識別子の両方、別のデータベースで同じキューブ識別子を使用することも可能性があります。  
  
 [ObjectDefinition](../../analysis-services/xmla/xml-elements-properties/objectdefinition-element-xmla.md)要素には作成する主要なオブジェクトを定義する Analysis Services スクリプト言語 (ASSL) 要素が含まれています。 ASSL の詳細については、次を参照してください[Analysis Services スクリプト言語 &#40; を使用した開発。ASSL &#41;](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
 設定した場合、 **AllowOverwrite**の属性、**作成**true の場合に使用するコマンドを指定した識別子を持つ既存の主要なオブジェクトを上書きすることができます。 そうしない場合、親オブジェクト内に指定された識別子を持つ主要なオブジェクトが既に存在するときに、エラーが発生します。  
  
 詳細については、**作成**コマンドを参照してください[要素の作成 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md).  
  
### <a name="creating-session-objects"></a>セッション オブジェクトの作成  
 セッション オブジェクトは一時オブジェクトであり、クライアント アプリケーションで使用される明示的または暗黙的なセッションでのみ使用でき、セッションの終了時には削除されます。 セッション オブジェクトを作成するには設定して、**スコープ**の属性、**作成**コマンドを*セッション*です。  
  
> [!NOTE]  
>  使用する場合、*セッション*を設定する、 **ObjectDefinition**要素を含めることができますのみ[ディメンション](../../analysis-services/scripting/objects/dimension-element-assl.md)、[キューブ](../../analysis-services/scripting/objects/cube-element-assl.md)、または[MiningModel](../../analysis-services/scripting/objects/miningmodel-element-assl.md) ASSL の要素。  
  
## <a name="altering-objects"></a>オブジェクトの変更  
 使用してオブジェクトを変更するときに、 **Alter**メソッド内のオブジェクト参照を提供することによって変更されるオブジェクトまず特定する必要があります、[オブジェクト](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)のプロパティ、 **をAlter**コマンド。 それぞれのオブジェクト参照にはであるオブジェクトを一意に識別するために必要なオブジェクト識別子が含まれています、 **Alter**コマンド。 オブジェクト参照の詳細については、次を参照してください。[定義とオブジェクトを識別する &#40;です。XMLA &#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/defining-and-identifying-objects-xmla.md).  
  
 たとえば、キューブの構造を変更するためには、キューブへのオブジェクト参照を指定する必要があります。 キューブ内のオブジェクトの参照、**オブジェクト**プロパティが含まれています、データベース識別子と、キューブ識別子の両方、別のデータベースで同じキューブ識別子を使用することも可能性があります。  
  
 **ObjectDefinition**要素には、変更する主要なオブジェクトを定義する ASSL の要素が含まれています。 ASSL の詳細については、次を参照してください[Analysis Services スクリプト言語 &#40; を使用した開発。ASSL &#41;](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
 設定した場合、 **AllowCreate**の属性、 **Alter** true の場合に使用するコマンド オブジェクトが存在しない場合は、指定された主要なオブジェクトを作成することができます。 そうしない場合、指定された主要なオブジェクトが存在していないときに、エラーが発生します。  
  
### <a name="using-the-objectexpansion-attribute"></a>ObjectExpansion 属性の使用  
 主要なオブジェクトのプロパティのみを変更して、主要なオブジェクトに格納される副次オブジェクトを再定義を行わない場合は、設定、 **ObjectExpansion**の属性、 **Alter**コマンド*ObjectProperties*です。 **ObjectDefinition**プロパティのみが主要なオブジェクトのプロパティの要素を格納して、 **Alter**コマンド アンタッチの主要なオブジェクトに関連付けられている副次オブジェクトのままにします。  
  
 設定する必要があります、主要なオブジェクトに対する副次オブジェクトを再定義する、 **ObjectExpansion**属性を*ExpandFull*オブジェクト定義は、主要なオブジェクトに含まれるすべての副次オブジェクトを含める必要があります。 場合、 **ObjectDefinition**のプロパティ、 **Alter**コマンドは主要なオブジェクトによって格納される副次オブジェクトを明示的に含まれませんに含まれていない、マイナー オブジェクトを削除します。  
  
### <a name="altering-session-objects"></a>セッション オブジェクトの変更  
 によって作成されたセッション オブジェクトを変更する、**作成**コマンド、設定、**スコープ**の属性、 **Alter**コマンドを*セッション*です。  
  
> [!NOTE]  
>  使用する場合、*セッション*を設定する、 **ObjectDefinition**要素を含めることができますのみ[ディメンション](../../analysis-services/scripting/objects/dimension-element-assl.md)、[キューブ](../../analysis-services/scripting/objects/cube-element-assl.md)、または[MiningModel](../../analysis-services/scripting/objects/miningmodel-element-assl.md) ASSL の要素。  
  
## <a name="creating-or-altering-subordinate-objects"></a>下位オブジェクトの作成または変更  
 ただし、**作成**または**Alter**作成または変更されている、主要なオブジェクトが、それを囲む内の定義を含めることができます、コマンドで作成または 1 つだけの最上位の主要なオブジェクトを変更**ObjectDefinition**従属する他のメジャーおよびマイナー オブジェクトのプロパティです。 たとえば、キューブを定義する場合の親データベースを指定**ParentObject**とでのキューブ定義内で**ObjectDefinition**メジャー グループおよびメジャー内で、キューブに対して定義できます。グループの各メジャー グループのパーティションを定義することができます。 副次オブジェクトは、それを格納する主要なオブジェクトの中でのみ定義できます。 メジャーおよびマイナー オブジェクトに関する詳細については、次を参照してください。[データベース オブジェクト &#40;です。Analysis Services - 多次元データ &#41;](../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md).  
  
## <a name="examples"></a>使用例  
  
### <a name="description"></a>Description  
 次の例を参照するリレーショナル データ ソースの作成、[!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)]サンプル[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース。  
  
### <a name="code"></a>コード  
  
```  
<Create xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    </ParentObject>  
    <ObjectDefinition>  
        <DataSource xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="RelationalDataSource">  
            <ID>AdventureWorksDW2012</ID>  
            <Name>AdventureWorksDW2012</Name>  
            <ConnectionString>Data Source=localhost;Initial Catalog=AdventureWorksDW2008R2;Integrated Security=True</ConnectionString>  
            <ImpersonationInfo>  
                <ImpersonationMode>ImpersonateServiceAccount</ImpersonationMode>  
            </ImpersonationInfo>  
            <ManagedProvider>System.Data.SqlClient</ManagedProvider>  
            <Timeout>PT0S</Timeout>  
        </DataSource>  
    </ObjectDefinition>  
</Create>  
```  
  
### <a name="description"></a>Description  
 次の例では、前の例で作成されたリレーショナル データ ソースを変更して、データ ソースのクエリ タイムアウトを 30 秒に設定します。  
  
### <a name="code"></a>コード  
  
```  
<Alter ObjectExpansion="ObjectProperties" xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DataSourceID>AdventureWorksDW2012</DataSourceID>  
    </Object>  
    <ObjectDefinition>  
        <DataSource xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="RelationalDataSource">  
            <ID>AdventureWorksDW2012</ID>  
            <Name>AdventureWorksDW2012</Name>  
            <ConnectionString>Data Source=fr-dwk-02;Initial Catalog=AdventureWorksDW2008R2;Integrated Security=True</ConnectionString>  
            <ManagedProvider>System.Data.SqlClient</ManagedProvider>  
            <Timeout>PT30S</Timeout>  
        </DataSource>  
    </ObjectDefinition>  
</Alter>  
```  
  
### <a name="comments"></a>コメント  
 **ObjectExpansion**の属性、 **Alter**コマンドに設定された*ObjectProperties*です。 この設定により、 [ImpersonationInfo](../../analysis-services/scripting/properties/impersonationinfo-element-assl.md)要素で定義されているデータ ソースから除外する、マイナー オブジェクトを使用して**ObjectDefinition**です。 そのため、そのデータ ソースに関する権限借用情報は、最初の例で指定したとおりにサービス アカウントに対して設定されたままになります。  
  
## <a name="see-also"></a>参照  
 [方法 &#40; を実行します。XMLA &#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)   
 [Analysis Services スクリプト言語 &#40; を使用した開発ASSL &#41;](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Analysis Services の XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
