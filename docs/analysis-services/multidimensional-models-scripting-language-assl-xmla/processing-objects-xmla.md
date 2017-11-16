---
title: "オブジェクト (XMLA) の処理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- errors [XML for Analysis]
- objects [XML for Analysis]
- XML for Analysis, objects
- XMLA, partitions
- partitions [Analysis Services], XML for Analysis
- XML for Analysis, partitions
- writeback [Analysis Services], XML for Analysis
- out-of-line bindings
- processing objects [XML for Analysis]
- XMLA, objects
ms.assetid: a65b3249-303d-49c6-98af-6ac6eed11a03
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6dfc2fafb76d19ea986b697ec065abec738f4c05
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="processing-objects-xmla"></a>オブジェクトの処理 (XMLA)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]処理は、手順つまたは一連のオンであるデータをビジネス分析のための情報にします。 処理内容はオブジェクトの種類によって異なりますが、データを情報に変換する処理の一部として必ず実行されます。  
  
 プロセスに、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]オブジェクトを使用する、[プロセス](../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)コマンド。 **プロセス**コマンドで、次のオブジェクトを処理できる、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンス。  
  
-   キューブ  
  
-   データベース  
  
-   ディメンション  
  
-   メジャー グループ  
  
-   [マイニング モデル]  
  
-   マイニング構造  
  
-   パーティション  
  
 オブジェクトの処理を制御する、**プロセス**コマンドにはさまざまなプロパティを設定することができます。 **プロセス**コマンドを制御するプロパティには: 量処理が行われます、どのオブジェクトを処理する、アウトオブ ライン バインドを使用するかどうか、エラーを処理する方法および書き戻しテーブルを管理する方法です。  
  
## <a name="specifying-processing-options"></a>処理オプションの指定  
 [型](../../analysis-services/xmla/xml-elements-properties/type-element-xmla.md)のプロパティ、**プロセス**コマンドは、オブジェクトの処理時に使用する処理オプションを指定します。 処理オプションの詳細については、「[処理オプションと設定 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md)」を参照してください。  
  
 次の表に、定数を**型**プロパティと各定数を使用して処理できるさまざまなオブジェクトです。  
  
|**型**値|適用されるオブジェクト|  
|--------------------|------------------------|  
|*ProcessFull*|キューブ、データベース、ディメンション、メジャー グループ、マイニング モデル、マイニング構造、パーティション|  
|*ProcessAdd*|ディメンション、パーティション|  
|*ProcessUpdate*|[ディメンション]|  
|*ProcessIndexes*|ディメンション、キューブ、メジャー グループ、パーティション|  
|*ProcessData*|ディメンション、キューブ、メジャー グループ、パーティション|  
|*ProcessDefault*|キューブ、データベース、ディメンション、メジャー グループ、マイニング モデル、マイニング構造、パーティション|  
|*ProcessClear*|キューブ、データベース、ディメンション、メジャー グループ、マイニング モデル、マイニング構造、パーティション|  
|*ProcessStructure*|キューブ、マイニング構造|  
|*ProcessClearStructureOnly*|マイニング構造|  
|*ProcessScriptCache*|Cube|  
  
 処理の詳細については[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、オブジェクトを参照してください[多次元モデル &#40; の処理Analysis Services &#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
## <a name="specifying-objects-to-be-processed"></a>処理対象のオブジェクトの指定  
 [オブジェクト](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)のプロパティ、**プロセス**コマンドには、処理するオブジェクトのオブジェクト識別子が含まれています。 1 つのオブジェクトを指定することができます、**プロセス**の子オブジェクトも処理コマンドしますが、オブジェクトを処理します。 たとえば、キューブ内のメジャー グループを処理すると、そのメジャー グループのすべてのパーティションが処理されます。また、データベースを処理すると、キューブ、ディメンション、およびマイニング構造など、そのデータベースに含まれるすべてのオブジェクトが処理されます。  
  
 設定した場合、 **ProcessAffectedObjects**の属性、**プロセス**関連する、指定したオブジェクトを処理することで影響を受けるオブジェクトの処理も true の場合、コマンドします。 たとえばを使用して、ディメンションの増分更新、 *ProcessUpdate*処理オプション、**プロセス**コマンド、任意のパーティションの集計がメンバーによって無効になる中追加または削除しても、処理されます[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]場合**ProcessAffectedObjects**が設定を true にします。 この場合は、1 つの**プロセス**コマンドで複数のオブジェクトを処理できる、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、インスタンスが、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]で指定された 1 つのオブジェクトだけでなくオブジェクトが決定、**プロセス**コマンドを処理もする必要があります。  
  
 ただし、複数を使用して、同時にディメンションなど、複数のオブジェクトを処理することができます**プロセス**コマンドの中で、**バッチ**コマンド。 バッチ操作では、オブジェクトの直列または並列処理のため、細かいレベルの制御を提供に、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンスを使用するより、 **ProcessAffectedObjects**属性がありの処理方法をチューニングできる大きな[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース。 バッチ操作の実行の詳細については、次を参照してください。[バッチ操作の実行 & #40 です。XMLA &#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/performing-batch-operations-xmla.md).  
  
## <a name="specifying-out-of-line-bindings"></a>不一致バインドの指定  
 場合、**プロセス**でコマンドが含まれていない、**バッチ**コマンド内の行外のバインディング オプションで指定できます、[バインド](../../analysis-services/xmla/xml-elements-properties/bindings-element-xmla.md)、[データソース](../../analysis-services/xmla/xml-elements-properties/datasource-element-xmla.md)、および[DataSourceView](../../analysis-services/xmla/xml-elements-properties/datasourceview-element-xmla.md)のプロパティ、**プロセス**コマンドを処理するオブジェクト。 アウトオブ ライン バインドは、データ ソース、データ ソース ビュー、およびその他のオブジェクトの実行時にのみ存在するバインドへの参照、**プロセス**コマンド、およびに関連付けられている既存のバインドを上書きします処理中のオブジェクト。 不一致バインドが指定されていない場合、処理対象のオブジェクトに現在関連付けられているバインドが使用されます。  
  
 不一致バインドは以下の状況で使用されます。  
  
-   パーティションの増分更新を行う。行が 2 回カウントされないように、代替のファクト テーブルか、既存のファクト テーブルに対するフィルターを指定する必要があります。  
  
-   データ フロー タスクを使用して[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]ディメンション、マイニング モデル、またはパーティションの処理中にデータを提供します。  
  
 不一致バインドは、Analysis Services Scripting Language (ASSL) の一部として記述されます。 ASSL での不一致バインドの詳細については、次を参照してください。[データ ソースとのバインド & #40 です。SSAS 多次元 &#41;](../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
### <a name="incrementally-updating-partitions"></a>パーティションの増分更新  
 通常、既に処理されているパーティションを増分更新する場合は、不一致バインドが必要です。これは、パーティションに対して指定されているバインドが、既にパーティション内で集計されているファクト テーブル データを参照するためです。 使用して既に処理されているパーティションを増分更新する場合、**プロセス**コマンド、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]は、次の操作を実行します。  
  
-   増分更新を行うパーティションと同じ構造の一時パーティションを作成します。  
  
-   指定された行外のバインディングを使用して、一時パーティションを処理、**プロセス**コマンド。  
  
-   一時パーティションを、選択された既存のパーティションにマージします。  
  
 XML for Analysis (XMLA) を使用してパーティションのマージに関する詳細については、次を参照してください。[パーティションのマージと #40 です。XMLA &#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/merging-partitions-xmla.md).  
  
## <a name="handling-processing-errors"></a>処理エラーの処理  
 [ErrorConfiguration](../../analysis-services/xmla/xml-elements-properties/errorconfiguration-element-xmla.md)のプロパティ、**プロセス**コマンドでは、オブジェクトの処理中に発生したエラーの処理方法を指定できます。 たとえば、ディメンションの処理時に、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] がキー属性のキー列で重複した値を検出したとします。 属性キーは一意である必要があるため、重複するレコードは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって破棄されます。 に基づいて、 [KeyDuplicate](../../analysis-services/scripting/properties/keyduplicate-element-assl.md)プロパティ**ErrorConfiguration**、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]でした。  
  
-   エラーを無視し、ディメンションの処理を続行する。  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] が重複したキーを検出したことを示すメッセージを返し、処理を続行する。  
  
 対象の多くのような条件がある**ErrorConfiguration**実行時のオプション、**プロセス**コマンド。  
  
## <a name="managing-writeback-tables"></a>書き戻しテーブルの管理  
 場合、**プロセス**コマンドには、書き込み許可パーティション、またはこのようなパーティションの既に完全に処理されていないキューブまたはメジャー グループが検出すると、書き戻しテーブルが既にそのパーティションの存在しません。 [WritebackTableCreation](../../analysis-services/xmla/xml-elements-properties/writebacktablecreation-element-xmla.md)のプロパティ、**プロセス**コマンドを確認するかどうか[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]書き戻しテーブルを作成する必要があります。  
  
## <a name="examples"></a>使用例  
  
### <a name="description"></a>Description  
 次の例は、[!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サンプル データベースを完全に処理します。  
  
### <a name="code"></a>コード  
  
```  
<Process xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Object>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
  </Object>  
  <Type>ProcessFull</Type>  
  <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
</Process>  
```  
  
### <a name="description"></a>Description  
 次の例、 **Internet_Sales_2004**でパーティション分割、 **Internet Sales**のメジャー グループ、 **Adventure Works DW** 内のキューブ[!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)]サンプル[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース。 **プロセス**コマンドはパーティションに追加する順序の集計、2006 年 12 月 31 日より後の日付での不一致クエリ バインドを使用して、**バインド**のプロパティ、**プロセス**パーティションに追加する集計を生成するファクト テーブルの行を取得するコマンド。  
  
### <a name="code"></a>コード  
  
```  
<Process ProcessAffectedObjects="true" xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Object>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works DW</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2006</PartitionID>  
  </Object>  
  <Bindings>  
    <Binding>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2006</PartitionID>  
      <Source xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="QueryBinding">  
        <DataSourceID>Adventure Works DW</DataSourceID>  
        <QueryDefinition>  
          SELECT  
            [dbo].[FactInternetSales].[ProductKey],  
            [dbo].[FactInternetSales].[OrderDateKey],  
            [dbo].[FactInternetSales].[DueDateKey],  
            [dbo].[FactInternetSales].[ShipDateKey],   
            [dbo].[FactInternetSales].[CustomerKey],   
            [dbo].[FactInternetSales].[PromotionKey],  
            [dbo].[FactInternetSales].[CurrencyKey],  
            [dbo].[FactInternetSales].[SalesTerritoryKey],  
            [dbo].[FactInternetSales].[SalesOrderNumber],  
            [dbo].[FactInternetSales].[SalesOrderLineNumber],  
            [dbo].[FactInternetSales].[RevisionNumber],  
            [dbo].[FactInternetSales].[OrderQuantity],  
            [dbo].[FactInternetSales].[UnitPrice],  
            [dbo].[FactInternetSales].[ExtendedAmount],  
            [dbo].[FactInternetSales].[UnitPriceDiscountPct],  
            [dbo].[FactInternetSales].[DiscountAmount],  
            [dbo].[FactInternetSales].[ProductStandardCost],  
            [dbo].[FactInternetSales].[TotalProductCost],  
            [dbo].[FactInternetSales].[SalesAmount],  
            [dbo].[FactInternetSales].[TaxAmt],  
            [dbo].[FactInternetSales].[Freight],  
            [dbo].[FactInternetSales].[CarrierTrackingNumber],  
            [dbo].[FactInternetSales].[CustomerPONumber]  
          FROM [dbo].[FactInternetSales]  
          WHERE OrderDateKey > '1280'  
        </QueryDefinition>  
      </Source>  
    </Binding>  
  </Bindings>  
  <Type>ProcessAdd</Type>  
  <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
</Process>  
```  
  
  

