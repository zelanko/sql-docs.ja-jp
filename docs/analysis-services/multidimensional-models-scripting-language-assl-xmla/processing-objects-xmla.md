---
title: オブジェクトの処理 (XMLA) |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 59a581f7e70f3fc1afd7eb7c1eaf4751d32719d0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63261662"
---
# <a name="processing-objects-xmla"></a>オブジェクトの処理 (XMLA)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]処理は、手順、または、ビジネス分析のための情報に手順を有効にするデータを一連の。 処理内容はオブジェクトの種類によって異なりますが、データを情報に変換する処理の一部として必ず実行されます。  
  
 プロセスに、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]オブジェクトを使用することができます、[プロセス](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla)コマンド。 **プロセス**コマンドで、次のオブジェクトを処理できる、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンス。  
  
-   キューブ  
  
-   データベース  
  
-   ディメンション  
  
-   メジャー グループ  
  
-   [マイニング モデル]  
  
-   マイニング構造  
  
-   [メジャー グループ]  
  
 オブジェクトの処理を制御する、**プロセス**コマンドにはさまざまなプロパティを設定することができます。 **プロセス**コマンドを制御するプロパティには: どの程度の処理が行われます、どのオブジェクトを処理する、アウトオブ ライン バインドを使用するかどうか、エラーを処理する方法および書き戻しテーブルを管理する方法。  
  
## <a name="specifying-processing-options"></a>処理オプションの指定  
 [型](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla)のプロパティ、**プロセス**コマンド オブジェクトの処理時に使用する処理オプションを指定します。 処理オプションの詳細については、「[処理オプションと設定 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md)」を参照してください。  
  
 次の表に、定数を**型**プロパティと各定数を使用して処理できるさまざまなオブジェクト。  
  
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
  
 処理の詳細については[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、オブジェクトを参照してください[多次元モデルの処理&#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)します。  
  
## <a name="specifying-objects-to-be-processed"></a>処理対象のオブジェクトの指定  
 [オブジェクト](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)のプロパティ、**プロセス**コマンドには、処理するオブジェクトのオブジェクト識別子が含まれています。 1 つのオブジェクトで指定できます、**プロセス**コマンドが、オブジェクトの処理も子オブジェクトを処理します。 たとえば、キューブ内のメジャー グループを処理すると、そのメジャー グループのすべてのパーティションが処理されます。また、データベースを処理すると、キューブ、ディメンション、およびマイニング構造など、そのデータベースに含まれるすべてのオブジェクトが処理されます。  
  
 設定した場合、 **ProcessAffectedObjects**の属性、**プロセス**true の場合、指定したオブジェクトを処理することによって影響を受けるオブジェクトの処理も関連するすべてのコマンドします。 使用して、ディメンションの増分更新する場合など、 *ProcessUpdate*処理オプション、**プロセス**コマンドを任意のパーティションの集計はメンバーによって無効になる中追加または削除によって処理されることも[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]場合**ProcessAffectedObjects**設定を true にします。 この場合、1 つで**プロセス**コマンドで複数のオブジェクトを処理できる、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンスが[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]で指定された 1 つのオブジェクトだけでなくオブジェクトが決定、**プロセス**コマンドが処理することもあります。  
  
 ただし、同時に複数を使用して、ディメンションなど、複数のオブジェクトを処理できる**プロセス**コマンドの中で、**バッチ**コマンド。 バッチ操作オブジェクトの直列または並列処理のために、細かいレベルの制御を提供する、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンスを使用するより、 **ProcessAffectedObjects**属性、およびの処理方法をチューニングできるより大きな[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース。 バッチ操作の実行の詳細については、次を参照してください。[バッチ操作の実行&#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/performing-batch-operations-xmla.md)します。  
  
## <a name="specifying-out-of-line-bindings"></a>不一致バインドの指定  
 場合、**プロセス**コマンドが含まれていない、**バッチ**コマンド、アウトオブ ライン バインドで必要に応じて指定できます、[バインド](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla)、 [DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasource-element-xmla)、および[DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla)のプロパティ、**プロセス**コマンドを処理するオブジェクト。 アウトオブ ライン バインドがデータ ソース、データ ソース ビュー、およびその他のオブジェクトの実行時にのみ、バインドが存在するへの参照、**プロセス**コマンド、および関連付けられている既存のバインドを上書きします処理中のオブジェクト。 不一致バインドが指定されていない場合、処理対象のオブジェクトに現在関連付けられているバインドが使用されます。  
  
 不一致バインドは以下の状況で使用されます。  
  
-   パーティションの増分更新を行う。行が 2 回カウントされないように、代替のファクト テーブルか、既存のファクト テーブルに対するフィルターを指定する必要があります。  
  
-   データ フロー タスクを使用して[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]ディメンション、マイニング モデル、またはパーティションの処理中にデータを提供します。  
  
 不一致バインドは、Analysis Services Scripting Language (ASSL) の一部として記述されます。 ASSL でのアウトオブ ライン バインドの詳細については、次を参照してください。[データ ソースとバインド&#40;SSAS 多次元&#41;](../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)します。  
  
### <a name="incrementally-updating-partitions"></a>パーティションの増分更新  
 通常、既に処理されているパーティションを増分更新する場合は、不一致バインドが必要です。これは、パーティションに対して指定されているバインドが、既にパーティション内で集計されているファクト テーブル データを参照するためです。 使用して、既に処理されているパーティションを増分更新する場合、**プロセス**コマンド、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]は、次の操作を実行します。  
  
-   増分更新を行うパーティションと同じ構造の一時パーティションを作成します。  
  
-   指定されたアウトオブ ライン バインドを使用して、一時パーティションを処理、**プロセス**コマンド。  
  
-   一時パーティションを、選択された既存のパーティションにマージします。  
  
 XML for Analysis (XMLA) を使用してパーティションのマージの詳細については、次を参照してください。[パーティションのマージ&#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/merging-partitions-xmla.md)します。  
  
## <a name="handling-processing-errors"></a>処理エラーの処理  
 [ErrorConfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla)のプロパティ、**プロセス**コマンドを使用して、オブジェクトの処理中に発生したエラーを処理する方法を指定できます。 たとえば、ディメンションの処理時に、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] がキー属性のキー列で重複した値を検出したとします。 属性キーは一意である必要があるため、重複するレコードは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって破棄されます。 に基づいて、 [KeyDuplicate](https://docs.microsoft.com/bi-reference/assl/properties/keyduplicate-element-assl)プロパティの**ErrorConfiguration**、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]でした。  
  
-   エラーを無視し、ディメンションの処理を続行する。  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] が重複したキーを検出したことを示すメッセージを返し、処理を続行する。  
  
 対象のような多くの条件が**ErrorConfiguration**実行時のオプション、**プロセス**コマンド。  
  
## <a name="managing-writeback-tables"></a>書き戻しテーブルの管理  
 場合、**プロセス**コマンドには、書き込み許可パーティション、またはこのようなそのパーティションが既に完全に処理しないため、キューブまたはメジャー グループが検出すると、そのパーティションの書き戻しテーブルが存在可能性がありますしません。 [WritebackTableCreation](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/writebacktablecreation-element-xmla)のプロパティ、**プロセス**コマンドを決定するかどうか[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]書き戻しテーブルを作成する必要があります。  
  
## <a name="examples"></a>使用例  
  
### <a name="description"></a>説明  
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
  
### <a name="description"></a>説明  
 次の例では、増分処理、 **Internet_Sales_2004**でパーティション分割、 **Internet Sales**のメジャー グループ、 **Adventure Works DW** 内のキューブ[!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)]サンプル[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース。 **プロセス**コマンドは、パーティションに追加する注文の集計、2006 年 12 月 31 日より後の日付でクエリのアウトオブ ライン バインドを使用して、**バインド**のプロパティ、**プロセス**パーティションに追加する集計の生成元となるファクト テーブルの行を取得するコマンド。  
  
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
  
  
