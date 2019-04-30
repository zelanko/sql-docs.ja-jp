---
title: 作成して、オブジェクト (XMLA) の変更 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 86f52c2ea61b8b62ea9bfe5ffe6b3c7b06977740
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63231947"
---
# <a name="creating-and-altering-objects-xmla"></a>オブジェクトの作成と変更 (XMLA)
  主要なオブジェクトは、個別に作成、変更、削除することができます。 主要なオブジェクトには以下のオブジェクトが含まれます。  
  
-   サーバー  
  
-   データベース  
  
-   ディメンション  
  
-   キューブ  
  
-   メジャー グループ  
  
-   [メジャー グループ]  
  
-   パースペクティブ  
  
-   [マイニング モデル]  
  
-   ロール  
  
-   サーバーまたはデータベースに関連付けられているコマンド  
  
-   データ ソース  
  
 使用する、[作成](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)のインスタンスで、主要なオブジェクトを作成するコマンド[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、および[Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)インスタンス上の既存の主要なオブジェクトを変更するコマンド。 使用して両方のコマンドを実行、 [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)メソッド。  
  
## <a name="creating-objects"></a>オブジェクトを作成します。  
 使用してオブジェクトを作成する場合、**作成**メソッド、親オブジェクトを含む最初に識別する必要があります、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]オブジェクトを作成します。 内のオブジェクト参照を提供することで、親オブジェクトを識別する、 [ParentObject](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)のプロパティ、**作成**コマンド。 それぞれのオブジェクト参照には親オブジェクトを一意に識別するために必要なオブジェクト識別子が含まれています、**作成**コマンド。 オブジェクト参照の詳細については、次を参照してください。[を識別するオブジェクトの定義および&#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/defining-and-identifying-objects-xmla.md)します。  
  
 たとえば、キューブに新しいメジャー グループを作成するには、キューブへのオブジェクト参照を指定する必要があります。 内のキューブのオブジェクト参照、 **ParentObject**プロパティを含むデータベース識別子とキューブの識別子では、別のデータベースで同じキューブ識別子を使用することも可能性があります。  
  
 [ObjectDefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla)要素には作成する主要なオブジェクトを定義する Analysis Services スクリプト言語 (ASSL) 要素が含まれています。 ASSL の詳細については、次を参照してください。 [Analysis Services スクリプト言語を使用した開発&#40;ASSL&#41;](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)します。  
  
 設定した場合、 **AllowOverwrite**の属性、**作成**コマンド true の場合、指定した識別子を持つ既存の主要なオブジェクトを上書きすることができます。 そうしない場合、親オブジェクト内に指定された識別子を持つ主要なオブジェクトが既に存在するときに、エラーが発生します。  
  
 詳細については、**作成**コマンドを参照してください[要素の作成&#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)します。  
  
### <a name="creating-session-objects"></a>セッション オブジェクトの作成  
 セッション オブジェクトは一時オブジェクトであり、クライアント アプリケーションで使用される明示的または暗黙的なセッションでのみ使用でき、セッションの終了時には削除されます。 セッション オブジェクトを作成するには設定して、**スコープ**の属性、**作成**コマンドを*セッション*します。  
  
> [!NOTE]  
>  使用する場合、*セッション*を設定する、 **ObjectDefinition**要素に含めることができますのみ[ディメンション](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl)、[キューブ](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl)、または[MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) ASSL の要素。  
  
## <a name="altering-objects"></a>オブジェクトの変更  
 使用してオブジェクトを変更するときに、 **Alter**メソッド、オブジェクト参照を提供することによって変更されるオブジェクト最初に識別する必要があります、[オブジェクト](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)のプロパティ、 **Alter**コマンド。 それぞれのオブジェクト参照にはオブジェクトを一意に識別するために必要なオブジェクト識別子が含まれています、 **Alter**コマンド。 オブジェクト参照の詳細については、次を参照してください。[を識別するオブジェクトの定義および&#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/defining-and-identifying-objects-xmla.md)します。  
  
 たとえば、キューブの構造を変更するためには、キューブへのオブジェクト参照を指定する必要があります。 内のキューブのオブジェクト参照、**オブジェクト**プロパティを含むデータベース識別子とキューブの識別子では、別のデータベースで同じキューブ識別子を使用することも可能性があります。  
  
 **ObjectDefinition**要素に変更する主要なオブジェクトを定義する ASSL の要素が含まれています。 ASSL の詳細については、次を参照してください。 [Analysis Services スクリプト言語を使用した開発&#40;ASSL&#41;](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)します。  
  
 設定した場合、 **AllowCreate**の属性、 **Alter**コマンド true の場合、オブジェクトが存在しない場合、指定された主要なオブジェクトを作成することができます。 そうしない場合、指定された主要なオブジェクトが存在していないときに、エラーが発生します。  
  
### <a name="using-the-objectexpansion-attribute"></a>ObjectExpansion 属性の使用  
 設定することができます、主要なオブジェクトのプロパティのみを変更し、主要なオブジェクトに格納される副次オブジェクトを再定義しない場合、 **ObjectExpansion**の属性、 **Alter**コマンド*Objectproperties です*します。 **ObjectDefinition**プロパティのみが、主要なオブジェクトのプロパティの要素を格納して、 **Alter**コマンドは、手を加えず、主要なオブジェクトに関連付けられている副次オブジェクトを残します。  
  
 設定する必要があります、主要なオブジェクトに対する副次オブジェクトを再定義する、 **ObjectExpansion**属性を*ExpandFull*オブジェクトの定義は、主要なオブジェクトに含まれるすべての副次オブジェクトを含める必要があります。 場合、 **ObjectDefinition**のプロパティ、 **Alter**コマンドは、主要なオブジェクトに格納される副次オブジェクトを明示的に含まれませんが含まれない副次オブジェクトを削除します。  
  
### <a name="altering-session-objects"></a>セッション オブジェクトの変更  
 によって作成されたセッション オブジェクトを変更する、**作成**コマンド、設定、**スコープ**の属性、 **Alter**コマンドを*セッション*します。  
  
> [!NOTE]  
>  使用する場合、*セッション*を設定する、 **ObjectDefinition**要素に含めることができますのみ[ディメンション](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl)、[キューブ](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl)、または[MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) ASSL の要素。  
  
## <a name="creating-or-altering-subordinate-objects"></a>下位オブジェクトの作成または変更  
 ただし、**作成**または**Alter**コマンドを作成または 1 つだけの最上位の主要なオブジェクトの変更、作成または変更されている、主要なオブジェクトは、囲んで定義を含めることができます**ObjectDefinition**従属する他のメジャーおよびマイナー オブジェクトのプロパティ。 たとえば、キューブを定義する場合で、親データベースを指定**ParentObject**、およびキューブの定義内**ObjectDefinition**メジャー内で、キューブのメジャー グループを定義することができますグループの各メジャー グループのパーティションを定義することができます。 副次オブジェクトは、それを格納する主要なオブジェクトの中でのみ定義できます。 メジャーおよびマイナー オブジェクトの詳細については、次を参照してください。[データベース オブジェクト&#40;Analysis Services - 多次元データ&#41;](../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)します。  
  
## <a name="examples"></a>使用例  
  
### <a name="description"></a>説明  
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
  
### <a name="description"></a>説明  
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
 **ObjectExpansion**の属性、 **Alter**コマンドに設定された*objectproperties です*します。 この設定では、 [ImpersonationInfo](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl)要素で定義されているデータ ソースから除外する、補助オブジェクトを使用して**ObjectDefinition**します。 そのため、そのデータ ソースに関する権限借用情報は、最初の例で指定したとおりにサービス アカウントに対して設定されたままになります。  
  
## <a name="see-also"></a>参照  
 [Execute メソッド&#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)   
 [Analysis Services スクリプト言語 (ASSL) での開発](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Analysis Services での XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
