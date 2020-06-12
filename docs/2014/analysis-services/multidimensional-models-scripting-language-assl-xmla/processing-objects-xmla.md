---
title: オブジェクトの処理 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
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
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2e59c7953ae8fc7d3cfceafa7b0e9d8c7186daf8
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544931"
---
# <a name="processing-objects-xmla"></a>オブジェクトの処理 (XMLA)
  では [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、ビジネス分析のためにデータを情報に変換するステップまたは一連の手順が処理されます。 処理内容はオブジェクトの種類によって異なりますが、データを情報に変換する処理の一部として必ず実行されます。  
  
 オブジェクトを処理するには、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [process](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla)コマンドを使用します。 `Process` コマンドでは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの以下のオブジェクトを処理できます。  
  
-   キューブ  
  
-   データベース  
  
-   Dimensions  
  
-   メジャー グループ  
  
-   [マイニング モデル]  
  
-   マイニング構造  
  
-   メジャー グループ  
  
 `Process` コマンドには、オブジェクトの処理を制御するために設定できるさまざまなプロパティが用意されています。 `Process` コマンドには、行う処理の程度、処理対象のオブジェクト、不一致バインドを使用するかどうか、エラー処理の方法、および書き戻しテーブルの管理方法を制御するプロパティがあります。  
  
## <a name="specifying-processing-options"></a>処理オプションの指定  
 コマンドの[Type](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla)プロパティは、 `Process` オブジェクトを処理するときに使用する処理オプションを指定します。 処理オプションの詳細については、「[処理オプションと設定 &#40;Analysis Services&#41;](../multidimensional-models/processing-options-and-settings-analysis-services.md)」を参照してください。  
  
 次の表は、`Type` プロパティの定数と、各定数を使用して処理できるさまざまなオブジェクトの一覧を示しています。  
  
|`Type` の値|適用されるオブジェクト|  
|--------------------|------------------------|  
|*ProcessFull*|キューブ、データベース、ディメンション、メジャー グループ、マイニング モデル、マイニング構造、パーティション|  
|*ProcessAdd*|ディメンション、パーティション|  
|*ProcessUpdate*|Dimension|  
|*ProcessIndexes*|ディメンション、キューブ、メジャーグループ、パーティション|  
|*ProcessData*|ディメンション、キューブ、メジャーグループ、パーティション|  
|*ProcessDefault*|キューブ、データベース、ディメンション、メジャー グループ、マイニング モデル、マイニング構造、パーティション|  
|*ProcessClear*|キューブ、データベース、ディメンション、メジャー グループ、マイニング モデル、マイニング構造、パーティション|  
|*ProcessStructure*|キューブ、マイニング構造|  
|*ProcessClearStructureOnly*|マイニング構造|  
|*ProcessScriptCache*|Cube|  
  
 オブジェクトの処理の詳細について [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、「[多次元モデルオブジェクトの処理](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)」を参照してください。  
  
## <a name="specifying-objects-to-be-processed"></a>処理対象のオブジェクトの指定  
 コマンドの[object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)プロパティには、 `Process` 処理するオブジェクトのオブジェクト識別子が含まれています。 `Process` コマンドで指定できるオブジェクトは 1 つだけですが、1 つのオブジェクトを処理すると、その子オブジェクトも処理されます。 たとえば、キューブ内のメジャー グループを処理すると、そのメジャー グループのすべてのパーティションが処理されます。また、データベースを処理すると、キューブ、ディメンション、およびマイニング構造など、そのデータベースに含まれるすべてのオブジェクトが処理されます。  
  
 `ProcessAffectedObjects` コマンドの `Process` 属性を true に設定すると、指定されたオブジェクトを処理することによって影響を受ける関連オブジェクトもすべて処理されます。 たとえば、コマンドで*Processupdate*処理オプションを使用してディメンションを増分更新する場合 `Process` 、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] `ProcessAffectedObjects` が true に設定されていると、メンバーの追加または削除によって集計が無効になるパーティションは、によっても処理されます。 この場合、1 つの `Process` コマンドで [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの複数のオブジェクトを処理することができますが、`Process` コマンドで指定された単一のオブジェクトの他に処理する必要があるオブジェクトは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって決定されます。  
  
 しかし、`Process` コマンドの中で複数の `Batch` コマンドを使用することによって、ディメンションなどの複数のオブジェクトを同時に処理することもできます。 バッチ操作では、`ProcessAffectedObjects` 属性を使用する場合よりも詳細なレベルで、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのオブジェクトの直列または並列処理を制御することができ、大規模な [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの処理方法をチューニングすることができます。 バッチ操作の実行の詳細については、「 [XMLA&#41;&#40;のバッチ操作の実行](performing-batch-operations-xmla.md)」を参照してください。  
  
## <a name="specifying-out-of-line-bindings"></a>不一致バインドの指定  
 コマンド `Process` がコマンドに含まれていない場合は、 `Batch` 必要に応じて、コマンドの[bindings](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla)、 [DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)、および[DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla)プロパティで不一致バインドを指定して、 `Process` 処理するオブジェクトを指定できます。 不一致バインドは、バインドが `Process` コマンドの実行時のみに存在する、データ ソース、データ ソース ビュー、および他のオブジェクトへの参照であり、処理中のオブジェクトに関連付けられている既存のバインドをオーバーライドします。 不一致バインドが指定されていない場合、処理対象のオブジェクトに現在関連付けられているバインドが使用されます。  
  
 不一致バインドは以下の状況で使用されます。  
  
-   パーティションの増分更新を行う。行が 2 回カウントされないように、代替のファクト テーブルか、既存のファクト テーブルに対するフィルターを指定する必要があります。  
  
-   のデータフロータスクを使用して、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ディメンション、マイニングモデル、またはパーティションの処理中にデータを提供します。  
  
 不一致バインドは、Analysis Services Scripting Language (ASSL) の一部として記述されます。 ASSL での不一致バインドの詳細については、「 [SSAS 多次元&#41;&#40;データソースとバインド](../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)」を参照してください。  
  
### <a name="incrementally-updating-partitions"></a>パーティションの増分更新  
 通常、既に処理されているパーティションを増分更新する場合は、不一致バインドが必要です。これは、パーティションに対して指定されているバインドが、既にパーティション内で集計されているファクト テーブル データを参照するためです。 既に処理されているパーティションを `Process` コマンドを使用して増分更新する場合、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は以下のアクションを実行します。  
  
-   増分更新を行うパーティションと同じ構造の一時パーティションを作成します。  
  
-   `Process` コマンドで指定された不一致バインドを使用して、一時パーティションを処理します。  
  
-   一時パーティションを、選択された既存のパーティションにマージします。  
  
 XML for Analysis (XMLA) を使用したパーティションのマージの詳細については、「 [xmla&#41;&#40;のパーティションのマージ](merging-partitions-xmla.md)」を参照してください。  
  
## <a name="handling-processing-errors"></a>処理エラーの処理  
 コマンドの[Errorconfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla)プロパティでは、 `Process` オブジェクトの処理中に発生したエラーの処理方法を指定できます。 たとえば、ディメンションの処理時に、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] がキー属性のキー列で重複した値を検出したとします。 属性キーは一意である必要があるため、重複するレコードは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって破棄されます。 の[Keyduplicate](https://docs.microsoft.com/bi-reference/assl/properties/keyduplicate-element-assl)プロパティに基づいて `ErrorConfiguration` 、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 次のことが考えられます。  
  
-   エラーを無視し、ディメンションの処理を続行する。  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] が重複したキーを検出したことを示すメッセージを返し、処理を続行する。  
  
 `ErrorConfiguration` によって `Process` コマンドの実行時のオプションが指定される同様の状況は、他にも多くあります。  
  
## <a name="managing-writeback-tables"></a>書き戻しテーブルの管理  
 `Process` コマンドで、まだ完全に処理されていない書き込み許可パーティション、または完全に処理されていない書き込み許可パーティションに対するキューブやメジャー グループが見つかった場合、そのパーティションには書き戻しテーブルがまだ存在していない可能性があります。 コマンドの[WritebackTableCreation](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/writebacktablecreation-element-xmla)プロパティは、 `Process` [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] が書き戻しテーブルを作成するかどうかを決定します。  
  
## <a name="examples"></a>例  
  
### <a name="description"></a>説明  
 次の例は、[!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サンプル データベースを完全に処理します。  
  
### <a name="code"></a>コード  
  
```  
<Process xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Object>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
  </Object>  
  <Type>ProcessFull</Type>  
  <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
</Process>  
```  
  
### <a name="description"></a>説明  
 次の例では、サンプルデータベースの**Adventure WORKS DW**キューブの**Internet Sales**メジャーグループの**Internet_Sales_2004**パーティションを増分処理し [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。 コマンドは、 `Process` コマンドのプロパティで不一致クエリバインドを使用して、パーティションに `Bindings` `Process` 追加する集計を生成するファクトテーブルの行を取得することにより、2006年12月31日より後の注文日の集計をパーティションに追加します。  
  
### <a name="code"></a>コード  
  
```  
<Process ProcessAffectedObjects="true" xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
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
  
  
