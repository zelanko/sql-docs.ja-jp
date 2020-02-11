---
title: オブジェクトの作成と変更 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [XML for Analysis]
- subordinate objects [XML for Analysis]
- XML for Analysis, objects
- modifying objects
- removing objects
- deleting objects
- XMLA, objects
ms.assetid: a2080867-e130-440c-92eb-f768869f34a8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3dcc6eedc97b3d476d79420b4e067883e17f03d2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62702299"
---
# <a name="creating-and-altering-objects-xmla"></a>オブジェクトの作成と変更 (XMLA)
  主要なオブジェクトは、個別に作成、変更、削除することができます。 主要なオブジェクトには以下のオブジェクトが含まれます。  
  
-   サーバー  
  
-   データベース  
  
-   Dimensions  
  
-   キューブ  
  
-   メジャー グループ  
  
-   [メジャー グループ]  
  
-   パースペクティブ  
  
-   [マイニング モデル]  
  
-   ロール  
  
-   サーバーまたはデータベースに関連付けられているコマンド  
  
-   データ ソース  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) [!INCLUDE[msCoName](../../includes/msconame-md.md)]インスタンスに主要なオブジェクトを作成するには create コマンドを使用し、インスタンスの既存の主要なオブジェクトを変更するには[alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)コマンドを使用します。 どちらのコマンドも、 [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)メソッドを使用して実行されます。  
  
## <a name="creating-objects"></a>オブジェクトの作成  
 
  `Create` メソッドを使用してオブジェクトを作成する場合は、まず、作成する [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトを含む親オブジェクトを識別する必要があります。 親オブジェクトを特定するには、 `Create`コマンドの[ParentObject](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)プロパティにオブジェクト参照を指定します。 それぞれのオブジェクト参照には、`Create` コマンドの対象の親オブジェクトを一意に識別するのに必要なオブジェクト識別子が含まれます。 オブジェクト参照の詳細については、「 [XMLA&#41;&#40;オブジェクトの定義と識別](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)」を参照してください。  
  
 たとえば、キューブに新しいメジャー グループを作成するには、キューブへのオブジェクト参照を指定する必要があります。 
  `ParentObject` プロパティでのキューブへのオブジェクト参照には、データベース識別子とキューブ識別子の両方が含まれます。別のデータベースでも同じキューブ識別子が使用されている可能性があるためです。  
  
 [Objectdefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla)要素には、作成する主要なオブジェクトを定義する Analysis Services スクリプト言語 (assl) 要素が含まれています。 ASSL の詳細については、「 [Analysis Services スクリプト言語 &#40;assl&#41;を使用した開発](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)」を参照してください。  
  
 
  `AllowOverwrite` コマンドの `Create` 属性を true に設定すると、指定された識別子を持つ既存の主要なオブジェクトを上書きできます。 そうしない場合、親オブジェクト内に指定された識別子を持つ主要なオブジェクトが既に存在するときに、エラーが発生します。  
  
 コマンドの`Create`詳細については、「 [CREATE Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)」を参照してください。  
  
### <a name="creating-session-objects"></a>セッション オブジェクトの作成  
 セッション オブジェクトは一時オブジェクトであり、クライアント アプリケーションで使用される明示的または暗黙的なセッションでのみ使用でき、セッションの終了時には削除されます。 セッションオブジェクトを作成するには、 `Scope` `Create`コマンドの属性を*session*に設定します。  
  
> [!NOTE]  
>  *セッション*設定を使用する場合、 `ObjectDefinition`要素には[Dimension](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl)、 [Cube](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl)、または[MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) assl の要素のみを含めることができます。  
  
## <a name="altering-objects"></a>オブジェクトの変更  
 メソッドを使用してオブジェクトを変更する場合は、まず、 `Alter`コマンドの[object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)プロパティにオブジェクト参照を指定することによって、変更するオブジェクトを特定する必要があります。 `Alter` それぞれのオブジェクト参照には、`Alter` コマンドの対象のオブジェクトを一意に識別するのに必要なオブジェクト識別子が含まれます。 オブジェクト参照の詳細については、「 [XMLA&#41;&#40;オブジェクトの定義と識別](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)」を参照してください。  
  
 たとえば、キューブの構造を変更するためには、キューブへのオブジェクト参照を指定する必要があります。 
  `Object` プロパティでのキューブへのオブジェクト参照には、データベース識別子とキューブ識別子の両方が含まれます。別のデータベースでも同じキューブ識別子が使用されている可能性があるためです。  
  
 
  `ObjectDefinition` 要素には、変更する主要なオブジェクトを定義する ASSL 要素が含まれます。 ASSL の詳細については、「 [Analysis Services スクリプト言語 &#40;assl&#41;を使用した開発](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)」を参照してください。  
  
 
  `AllowCreate` コマンドの `Alter` 属性を true に設定すると、指定された主要なオブジェクトが存在しない場合に、それを作成することができます。 そうしない場合、指定された主要なオブジェクトが存在していないときに、エラーが発生します。  
  
### <a name="using-the-objectexpansion-attribute"></a>ObjectExpansion 属性の使用  
 主要なオブジェクトのプロパティのみを変更し、主要なオブジェクトに含まれているマイナーオブジェクトを再定義しない場合は、 `ObjectExpansion` `Alter`コマンドの属性を*objectproperties*に設定できます。 
  `ObjectDefinition` プロパティには、主要なオブジェクトのプロパティに対応する要素だけを含めればよく、その場合 `Alter` コマンドは主要なオブジェクトに関連付けられている副次オブジェクトに変更を加えません。  
  
 主要なオブジェクトの副オブジェクトを再定義するには、 `ObjectExpansion`属性を*expandfull*に設定し、オブジェクト定義に、主要なオブジェクトに含まれるすべてのマイナーオブジェクトを含める必要があります。 
  `ObjectDefinition` コマンドの `Alter` プロパティに、主要なオブジェクトに格納される副次オブジェクトが明示的に含められていない場合、含まれない副次オブジェクトは削除されます。  
  
### <a name="altering-session-objects"></a>セッション オブジェクトの変更  
 `Create`コマンドによって作成されたセッションオブジェクトを`Scope`変更するに`Alter`は、コマンドの属性を*session*に設定します。  
  
> [!NOTE]  
>  *セッション*設定を使用する場合、 `ObjectDefinition`要素には[Dimension](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl)、 [Cube](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl)、または[MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) assl の要素のみを含めることができます。  
  
## <a name="creating-or-altering-subordinate-objects"></a>下位オブジェクトの作成または変更  
 
  `Create` または `Alter` コマンドで作成または変更できるのは最上位の主要なオブジェクトだけですが、作成中または変更中の主要なオブジェクトには、囲んでいる `ObjectDefinition` プロパティの中に、従属する他の主要なオブジェクトや副次オブジェクトの定義を含めることができます。 たとえば、キューブを定義する場合、`ParentObject` で親データベースを指定します。`ObjectDefinition` でのキューブ定義にはキューブのメジャー グループを定義でき、さらにメジャー グループ内ではそれぞれのメジャー グループのパーティションを定義できます。 副次オブジェクトは、それを格納する主要なオブジェクトの中でのみ定義できます。 メジャーおよびマイナーオブジェクトの詳細については、「[データベースオブジェクト &#40;Analysis Services-多次元データ&#41;](../multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)」を参照してください。  
  
## <a name="examples"></a>例  
  
### <a name="description"></a>[説明]  
 次の例では、 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)]サンプル[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースを参照するリレーショナルデータソースを作成します。  
  
### <a name="code"></a>コード  
  
```  
<Create xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
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
  
### <a name="description"></a>[説明]  
 次の例では、前の例で作成されたリレーショナル データ ソースを変更して、データ ソースのクエリ タイムアウトを 30 秒に設定します。  
  
### <a name="code"></a>コード  
  
```  
<Alter ObjectExpansion="ObjectProperties" xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
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
  
### <a name="comments"></a>説明  
 `Alter`コマンド`ObjectExpansion`の属性が*objectproperties*に設定されました。 この設定により、 [ImpersonationInfo](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl)要素 (マイナーオブジェクト) を、で`ObjectDefinition`定義されているデータソースから除外できます。 そのため、そのデータ ソースに関する権限借用情報は、最初の例で指定したとおりにサービス アカウントに対して設定されたままになります。  
  
## <a name="see-also"></a>参照  
 [XMLA&#41;&#40;メソッドの実行](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)   
 [Analysis Services スクリプト言語 &#40;ASSL&#41;を使用した開発](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Analysis Services での XMLA による開発](developing-with-xmla-in-analysis-services.md)  
  
  
