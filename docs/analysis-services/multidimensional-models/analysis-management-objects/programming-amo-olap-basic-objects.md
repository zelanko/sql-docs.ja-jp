---
title: "AMO OLAP 基本オブジェクトのプログラミング |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- programming [AMO]
- Analysis Management Objects, OLAP
- OLAP [AMO]
- AMO, OLAP
ms.assetid: ad1c970e-c0cb-4687-9563-56ab62c2db5f
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: eaca145753958228bdecae9b7bdcb2ebcdb8b6cb
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="programming-amo-olap-basic-objects"></a>AMO OLAP 基本オブジェクトのプログラミング
  複雑な [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] オブジェクトの作成は簡単でわかりやすいものですが、詳細については注意が必要です。 このトピックでは、OLAP 基本オブジェクトのプログラミングについて詳しく説明します。 このトピックには、次のセクションが含まれます。  
  
-   [Dimension オブジェクト](#Dim)  
  
-   [キューブ オブジェクト](#Cub)  
  
-   [MeasureGroup オブジェクト](#MG)  
  
-   [Partition オブジェクト](#Part)  
  
-   [Aggregation オブジェクト](#AD)  
  
##  <a name="Dim"></a>Dimension オブジェクト  
 ディメンションを管理または処理するには、<xref:Microsoft.AnalysisServices.Dimension> オブジェクトをプログラミングします。  
  
### <a name="creating-dropping-and-finding-a-dimension"></a>ディメンションの作成、削除、および検索  
 <xref:Microsoft.AnalysisServices.Dimension> オブジェクトを作成するには、次の 4 つの手順を実行します。  
  
1.  Dimension オブジェクトを作成し、基本属性を設定します。  
  
     基本属性は、名前、ディメンションの種類、ストレージ モード、データ ソース バインド、All メンバー名の属性、およびその他のディメンション属性です。  
  
     ディメンションを作成する前に、ディメンションがまだ存在していないことを確認してください。 ディメンションが存在している場合、そのディメンションを削除して再作成します。  
  
2.  ディメンションを定義する属性を作成します。  
  
     属性を使用するには、まず、必要な属性をスキーマに個別に追加する必要があります (サンプル コード末尾の CreateDataItem メソッドを参照)。その後、これらの属性をディメンションの属性のコレクションに追加できます。  
  
     Key 列および Name 列をすべての属性について定義する必要があります。  
  
     ディメンションの主キー属性を AttributeUsage.Key として定義し、この属性がディメンションへのキー アクセスであることを明確にする必要があります。  
  
3.  ユーザーがディメンションで移動するためにアクセスする階層を作成します。  
  
     階層を作成する際、作成した順序に従ってレベルの順序が上から順に定義されます。 階層のレベル コレクションに最初に追加したレベルが最上位レベルになります。  
  
4.  現在のディメンションの Update メソッドを使用してサーバーを更新します。  
  
 次のサンプル コードは、サンプル データベースの Adventure Works products テーブルから、Product ディメンションを作成します。  
  
```  
static void CreateProductDimension(Database db, string datasourceName)  
{  
    // Create the Product dimension  
    Dimension dim = db.Dimensions.FindByName("Product");  
    if ( dim != null)  
       dim.Drop();  
    dim = db.Dimensions.Add("Product");  
    dim.Type = DimensionType.Products;  
    dim.UnknownMember = UnknownMemberBehavior.Hidden;  
    dim.AttributeAllMemberName = "All Products";  
    dim.Source = new DataSourceViewBinding(datasourceName);  
    dim.StorageMode = DimensionStorageMode.Molap;  
  
    #region Create attributes  
  
    DimensionAttribute attr;  
  
    attr = dim.Attributes.Add("Product Name");  
    attr.Usage = AttributeUsage.Key;  
    attr.Type = AttributeType.Product;  
    attr.OrderBy = OrderBy.Name;  
    attr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "DimProduct", "ProductKey"));  
    attr.NameColumn = CreateDataItem(db.DataSourceViews[0], "DimProduct", "EnglishProductName");  
  
    attr = dim.Attributes.Add("Product Line");  
    attr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "DimProduct", "ProductLine"));  
    attr.NameColumn = CreateDataItem(db.DataSourceViews[0], "DimProduct", "ProductLineName");  
  
    attr = dim.Attributes.Add("Model Name");  
    attr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "DimProduct", "ModelName"));  
    attr.AttributeRelationships.Add(new AttributeRelationship("Product Line"));  
    attr.AttributeRelationships.Add(new AttributeRelationship("Subcategory"));  
  
    attr = dim.Attributes.Add("Subcategory");  
    attr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "DimProductSubcategory", "ProductSubcategoryKey"));  
    attr.KeyColumns[0].NullProcessing = NullProcessing.UnknownMember;  
    attr.NameColumn = CreateDataItem(db.DataSourceViews[0], "DimProductSubcategory", "EnglishProductSubcategoryName");  
    attr.AttributeRelationships.Add(new AttributeRelationship("Category"));  
  
    attr = dim.Attributes.Add("Category");  
    attr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "DimProductCategory", "ProductCategoryKey"));  
    attr.NameColumn = CreateDataItem(db.DataSourceViews[0], "DimProductCategory", "EnglishProductCategoryName");  
  
    attr = dim.Attributes.Add("List Price");  
    attr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "DimProduct", "ListPrice"));  
    attr.AttributeHierarchyEnabled = false;  
  
    attr = dim.Attributes.Add("Size");  
    attr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "DimProduct", "Size"));  
    attr.AttributeHierarchyEnabled = false;  
  
    attr = dim.Attributes.Add("Weight");  
    attr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "DimProduct", "Weight"));  
    attr.AttributeHierarchyEnabled = false;  
  
    #endregion  
  
    #region Create hierarchies  
  
    Hierarchy hier;  
  
    hier = dim.Hierarchies.Add("Product Model Categories");  
    hier.AllMemberName = "All Products";  
    hier.Levels.Add("Category").SourceAttributeID = "Category";  
    hier.Levels.Add("Subcategory").SourceAttributeID = "Subcategory";  
    hier.Levels.Add("Model Name").SourceAttributeID = "Model Name";  
  
    hier = dim.Hierarchies.Add("Product Categories");  
    hier.AllMemberName = "All Products";  
    hier.Levels.Add("Category").SourceAttributeID = "Category";  
    hier.Levels.Add("Subcategory").SourceAttributeID = "Subcategory";  
    hier.Levels.Add("Model Name").SourceAttributeID = "Product Name";  
  
    hier = dim.Hierarchies.Add("Product Model Lines");  
    hier.AllMemberName = "All Products";  
    hier.Levels.Add("Subcategory").SourceAttributeID = "Product Line";  
    hier.Levels.Add("Model Name").SourceAttributeID = "Model Name";  
  
    #endregion  
  
    dim.Update();  
}  
  
static DataItem CreateDataItem(DataSourceView dsv, string tableName, string columnName)  
{  
    DataTable dataTable = ((DataSourceView)dsv).Schema.Tables[tableName];  
    DataColumn dataColumn = dataTable.Columns[columnName];  
    return new DataItem(tableName, columnName,  
        OleDbTypeConverter.GetRestrictedOleDbType(dataColumn.DataType));  
}  
  
```  
  
### <a name="processing-a-dimension"></a>ディメンションの処理  
 ディメンションの処理は、<xref:Microsoft.AnalysisServices.Dimension> オブジェクトの Process メソッドを使用して簡単に実行できます。  
  
 ディメンションの処理は、ディメンションを使用するすべてのキューブに影響する可能性があります。 処理オプションの詳細については、次を参照してください[多次元モデル &#40; の処理。Analysis Services &#41;](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 次のコードは、指定されたデータベースのすべてのディメンションを増分更新します。  
  
```  
static void UpdateAllDimensions(Database db)  
{  
    foreach (Dimension dim in db.Dimensions)  
        dim.Process(ProcessType.ProcessUpdate);  
}  
```  
  
##  <a name="Cub"></a>キューブ オブジェクト  
 キューブを管理または処理するには、<xref:Microsoft.AnalysisServices.Cube> オブジェクトをプログラミングします。  
  
### <a name="creating-dropping-and-finding-a-cube"></a>キューブの作成、削除、および検索  
 キューブの管理はディメンションの管理に似ています。 <xref:Microsoft.AnalysisServices.Cube> オブジェクトを作成するには、次の 4 つの手順を実行します。  
  
1.  Cube オブジェクトを作成し、基本属性を設定します。  
  
     基本属性は、名前、ストレージ モード、データ ソース バインド、既定のメジャー、およびその他のキューブ属性です。  
  
     キューブを作成する前に、キューブが存在していないことを確認してください。 サンプルでは、キューブが存在する場合、そのキューブを削除して再作成します。  
  
2.  キューブのディメンションを追加します。  
  
     ディメンションは、データベースから現在のキューブのディメンション コレクションに追加されます。キューブ内のディメンションは、データベースのディメンション コレクションへの参照です。 各ディメンションはキューブに個別にマッピングする必要があります。 サンプルでは、データベース ディメンションの内部識別子、キューブ内のディメンション名、およびキューブ内の名前付きディメンションの ID を指定してディメンションをマッピングしています。  
  
     サンプル コードでは、異なるキューブ ディメンション名 (Date、Ship Date、Delivery Date) を指定して、"Date" ディメンションを 3 回追加していることに注意してください。 これらのディメンションは "多様" ディメンションと呼ばれます。 基本ディメンションは同一 (Date) ですが、ファクト テーブル内では異なる "ロール" (Order Date、Ship Date、Delivery Date) でディメンションが使用されます。"多様" ディメンションの定義方法については、後の「メジャー グループの作成、削除、および検索」を参照してください。  
  
3.  ユーザーがキューブのデータを閲覧するためにアクセスするメジャー グループを作成します。  
  
     メジャー グループの作成方法については、後の「メジャー グループの作成、削除、および検索」で説明します。 サンプルでは、メジャー グループごとに異なるメソッドでメジャー グループの作成をラップしています。  
  
4.  現在のキューブの Update メソッドを使用してサーバーを更新します。  
  
     この Update メソッドでは、サーバー内のすべてのオブジェクトを完全に更新するため、Update オプション ExpandFull を使用しています。  
  
 次のサンプル コードでは、Adventure Works キューブの一部を作成します。 このサンプル コードは、Adventure Works Analysis Services プロジェクト サンプルに含まれるディメンションまたはメジャー グループをすべて作成するわけではありません。  
  
```  
static void CreateAdventureWorksCube(Database db, string datasourceName)  
{  
    // Create the Adventure Works cube  
    Cube cube = db.Cubes.FindByName("Adventure Works");  
    if ( cube != null)  
       cube.Drop();  
    db.Cubes.Add("Adventure Works");  
    cube.DefaultMeasure = "[Reseller Sales Amount]";  
    cube.Source = new DataSourceViewBinding(datasourceName);  
    cube.StorageMode = StorageMode.Molap;  
  
    #region Create cube dimensions  
  
    Dimension dim;  
  
    dim = db.Dimensions.GetByName("Date");  
    cube.Dimensions.Add(dim.ID, "Date", "Order Date Key - Dim Time");  
    cube.Dimensions.Add(dim.ID, "Ship Date",  
        "Ship Date Key - Dim Time");  
    cube.Dimensions.Add(dim.ID, "Delivery Date",  
        "Delivery Date Key - Dim Time");  
  
    dim = db.Dimensions.GetByName("Customer");  
    cube.Dimensions.Add(dim.ID);  
  
    dim = db.Dimensions.GetByName("Reseller");  
    cube.Dimensions.Add(dim.ID);  
    #endregion  
  
    #region Create measure groups  
  
    CreateSalesReasonsMeasureGroup(cube);  
    CreateInternetSalesMeasureGroup(cube);  
    CreateResellerSalesMeasureGroup(cube);  
    CreateCustomersMeasureGroup(cube);  
    CreateCurrencyRatesMeasureGroup(cube);  
  
    #endregion  
  
    cube.Update(UpdateOptions.ExpandFull);  
}  
```  
  
### <a name="processing-a-cube"></a>キューブの処理  
 キューブの処理は、<xref:Microsoft.AnalysisServices.Cube> オブジェクトの Process メソッドを使用して簡単に実行できます。 キューブを処理すると、キューブ内のすべてのメジャー グループ、およびメジャー グループ内のすべてのパーティションも処理されます。 キューブ内で処理可能なオブジェクトはパーティションだけです。処理に関しては、メジャー グループはパーティションのコンテナーにすぎません。 キューブに対して指定した処理の種類はパーティションに反映されます。 キューブおよびメジャー グループの処理は、ディメンションとパーティションの処理に内部的に解決されます。  
  
 処理オプションの詳細については、次を参照してください。[オブジェクトの処理 & #40 です。XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/processing-objects-xmla.md)、および[多次元モデル &#40; の処理Analysis Services &#41;](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 次のコードでは、指定したデータベース内のすべてのキューブを完全に処理します。  
  
```  
foreach (Cube cube in db.Cubes)  
             cube.Process(ProcessType.ProcessFull);  
     }  
```  
  
##  <a name="MG"></a>MeasureGroup オブジェクト  
 メジャー グループを管理または処理するには、<xref:Microsoft.AnalysisServices.MeasureGroup> オブジェクトをプログラミングします。  
  
### <a name="creating-dropping-and-finding-a-measuregroup"></a>メジャー グループの作成、削除、および検索  
 メジャー グループの管理は、ディメンションおよびキューブの管理に似ています。 <xref:Microsoft.AnalysisServices.MeasureGroup> オブジェクトを作成するには、次の手順を実行します。  
  
1.  MeasureGroup オブジェクトを作成し、基本属性を設定します。  
  
     基本属性は、名前、ストレージ モード、処理モード、既定のメジャー、およびその他のメジャー グループ属性です。  
  
     メジャー グループを作成する前に、メジャー グループが存在していないことを確認してください。 サンプル コードでは、メジャー グループが存在する場合、そのメジャー グループを削除して再作成します。  
  
2.  メジャー グループのメジャーを作成します。 作成するメジャーごとに、名前、集計関数、ソース列、書式設定文字列の各属性が割り当てられます。 他の属性を割り当てることもできます。 次のサンプル コードでは、CreateDataItem メソッドでスキーマに列を追加していることに注意してください。  
  
3.  メジャー グループのディメンションを追加します。  
  
4.  ディメンションは、親のキューブのディメンション コレクションから現在のメジャー グループのディメンション コレクションに追加されます。 メジャー グループのディメンション コレクションにディメンションを追加したら、ファクト テーブルのキー列をディメンションにマッピングすることにより、ディメンションを介してメジャー グループを直ちに閲覧できるようになります。  
  
     次のサンプル コードの "Mapping dimension and key column from fact table" の下の行に注意してください。 異なる代理キーを名前が異なる同一のディメンションにリンクして、多様ディメンションを実装しています。 多様ディメンション (Date、Ship Date、Delivery Date) ごとに異なる代理キー (OrderDateKey、ShipDateKey、DueDateKey) がリンクされます。 これらはすべてファクト テーブル FactInternetSales のキーです。  
  
5.  デザインしたメジャー グループのパーティションを追加します。  
  
     次のサンプル コードでは、パーティションの作成を 1 つのメソッドでラップしています。  
  
6.  現在のメジャー グループの Update メソッドを使用してサーバーを更新します。  
  
     次のサンプル コードでは、キューブを更新する際にすべてのメジャー グループを更新します。  
  
 次のサンプル コードでは、Adventure Works Analysis Services プロジェクト サンプルの InternetSales メジャー グループを作成します。  
  
```  
static void CreateInternetSalesMeasureGroup(Cube cube)  
{  
    // Create the Internet Sales measure group  
    Database db = cube.Parent;  
    MeasureGroup mg = cube.MeasureGroups.FindByName("Internet Sales");  
    if ( mg != null)  
       mg.Drop();  
    mg = cube.MeasureGroups.Add("Internet Sales");  
    mg.StorageMode = StorageMode.Molap;  
    mg.ProcessingMode = ProcessingMode.LazyAggregations;  
    mg.Type = MeasureGroupType.Sales;  
  
    #region Create measures  
  
    Measure meas;  
  
    meas = mg.Measures.Add("Internet Sales Amount");  
    meas.AggregateFunction = AggregationFunction.Sum;  
    meas.FormatString = "Currency";  
    meas.Source = CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "SalesAmount");  
  
    meas = mg.Measures.Add("Internet Order Quantity");  
    meas.AggregateFunction = AggregationFunction.Sum;  
    meas.FormatString = "#,#";  
    meas.Source = CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "OrderQuantity");  
  
    meas = mg.Measures.Add("Internet Unit Price");  
    meas.AggregateFunction = AggregationFunction.Sum;  
    meas.FormatString = "Currency";  
    meas.Visible = false;  
    meas.Source = CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "UnitPrice");  
  
    meas = mg.Measures.Add("Internet Total Product Cost");  
    meas.AggregateFunction = AggregationFunction.Sum;  
    //meas.MeasureExpression = "[Internet Total Product Cost] * [Average Rate]";  
    meas.FormatString = "Currency";  
    meas.Source = CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "TotalProductCost");  
  
    meas = mg.Measures.Add("Internet Order Count");  
    meas.AggregateFunction = AggregationFunction.Count;  
    meas.FormatString = "#,#";  
    meas.Source = CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "ProductKey");  
  
    #endregion  
  
    #region Create measure group dimensions  
  
    CubeDimension cubeDim;  
    RegularMeasureGroupDimension regMgDim;  
    ManyToManyMeasureGroupDimension mmMgDim;  
    MeasureGroupAttribute mgAttr;  
  
    //   Mapping dimension and key column from fact table  
    //      > select dimension and add it to the measure group  
    cubeDim = cube.Dimensions.GetByName("Date");  
    regMgDim = new RegularMeasureGroupDimension(cubeDim.ID);  
    mg.Dimensions.Add(regMgDim);  
  
    //      > add key column from dimension and map it with   
    //        the surrogate key in the fact table  
    mgAttr = regMgDim.Attributes.Add(cubeDim.Dimension.Attributes.GetByName("Date").ID);   // this is dimension key column  
    mgAttr.Type = MeasureGroupAttributeType.Granularity;  
    mgAttr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "OrderDateKey"));   // this surrogate key in fact table  
  
    cubeDim = cube.Dimensions.GetByName("Ship Date");  
    regMgDim = new RegularMeasureGroupDimension(cubeDim.ID);  
    mg.Dimensions.Add(regMgDim);  
    mgAttr = regMgDim.Attributes.Add(cubeDim.Dimension.Attributes.GetByName("Date").ID);  
    mgAttr.Type = MeasureGroupAttributeType.Granularity;  
    mgAttr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "ShipDateKey"));  
  
    cubeDim = cube.Dimensions.GetByName("Delivery Date");  
    regMgDim = new RegularMeasureGroupDimension(cubeDim.ID);  
    mg.Dimensions.Add(regMgDim);  
    mgAttr = regMgDim.Attributes.Add(cubeDim.Dimension.Attributes.GetByName("Date").ID);  
    mgAttr.Type = MeasureGroupAttributeType.Granularity;  
    mgAttr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "DueDateKey"));  
  
    cubeDim = cube.Dimensions.GetByName("Customer");  
    regMgDim = new RegularMeasureGroupDimension(cubeDim.ID);  
    mg.Dimensions.Add(regMgDim);  
    mgAttr = regMgDim.Attributes.Add(cubeDim.Dimension.Attributes.GetByName("Full Name").ID);  
    mgAttr.Type = MeasureGroupAttributeType.Granularity;  
    mgAttr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "CustomerKey"));  
  
    cubeDim = cube.Dimensions.GetByName("Product");  
    regMgDim = new RegularMeasureGroupDimension(cubeDim.ID);  
    mg.Dimensions.Add(regMgDim);  
    mgAttr = regMgDim.Attributes.Add(cubeDim.Dimension.Attributes.GetByName("Product Name").ID);  
    mgAttr.Type = MeasureGroupAttributeType.Granularity;  
    mgAttr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "ProductKey"));  
  
    cubeDim = cube.Dimensions.GetByName("Source Currency");  
    regMgDim = new RegularMeasureGroupDimension(cubeDim.ID);  
    mg.Dimensions.Add(regMgDim);  
    mgAttr = regMgDim.Attributes.Add(cubeDim.Dimension.Attributes.GetByName("Currency").ID);  
    mgAttr.Type = MeasureGroupAttributeType.Granularity;  
    mgAttr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "CurrencyKey"));  
  
    cubeDim = cube.Dimensions.GetByName("Sales Reason");  
    mmMgDim = new ManyToManyMeasureGroupDimension();  
    mmMgDim.CubeDimensionID = cubeDim.ID;  
    mmMgDim.MeasureGroupID = cube.MeasureGroups.GetByName("Sales Reasons").ID;  
    mg.Dimensions.Add(mmMgDim);  
  
    cubeDim = cube.Dimensions.GetByName("Internet Sales Order Details");  
    regMgDim = new RegularMeasureGroupDimension(cubeDim.ID);  
    mg.Dimensions.Add(regMgDim);  
    mgAttr = regMgDim.Attributes.Add(cubeDim.Dimension.Attributes.GetByName("Sales Order Key").ID);  
    mgAttr.Type = MeasureGroupAttributeType.Granularity;  
    mgAttr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "SalesOrderNumber"));  
    mgAttr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "SalesOrderLineNumber"));  
  
    #endregion  
  
    #region Create partitions  
  
    CreateInternetSalesMeasureGroupPartitions( mg)  
  
    #endregion  
}  
```  
  
### <a name="processing-a-measure-group"></a>メジャー グループの処理  
 メジャー グループの処理は、<xref:Microsoft.AnalysisServices.MeasureGroup> オブジェクトの Process メソッドを使用して簡単に実行できます。 メジャー グループを処理すると、メジャー グループに属するすべてのパーティションが処理されます。 メジャー グループの処理は、ディメンションとパーティションの処理に内部的に解決されます。 参照してください[パーティションの処理](#ProcPart)このドキュメントでします。  
  
 処理オプションの詳細については、次を参照してください。[オブジェクトの処理 & #40 です。XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/processing-objects-xmla.md)、および[多次元モデル &#40; の処理Analysis Services &#41;](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 次のコードは、指定されたキューブのすべてのメジャー グループを完全に処理します。  
  
```  
static void FullProcessAllMeasureGroups(Cube cube)  
{  
    foreach (MeasureGroup mg in cube.MeasureGroups)  
        mg.Process(ProcessType.ProcessFull);  
}  
```  
  
##  <a name="Part"></a>Partition オブジェクト  
 パーティションを管理または処理するには、<xref:Microsoft.AnalysisServices.Partition> オブジェクトをプログラミングします。  
  
### <a name="creating-dropping-and-finding-a-partition"></a>パーティションの作成、削除、および検索  
 パーティションは、次の 2 つの手順で作成できる単純なオブジェクトです。  
  
1.  Partition オブジェクトを作成し、基本属性を設定します。  
  
     基本属性は、名前、ストレージ モード、パーティション ソース、スライス、およびその他のメジャー グループ属性です。 パーティション ソースは、現在のパーティションの SQL Select ステートメントを定義します。 スライスは、現在のパーティションに含まれる、親メジャー グループのディメンションの範囲を定義する組またはセットを表す MDX 式です。 MOLAP パーティションの場合は、パーティションを処理するたびにスライスが自動的に設定されます。  
  
     パーティションを作成する前に、パーティションが存在していないことを確認してください。 次のサンプル コードでは、パーティションが存在する場合、そのパーティションを削除して再作成します。  
  
2.  現在のパーティションの Update メソッドを使用してサーバーを更新します。  
  
     次のサンプル コードでは、キューブを更新する際にすべてのパーティションを更新します。  
  
 次のコード サンプルでは、"InternetSales" メジャー グループのパーティションを作成します。  
  
```  
static void CreateInternetSalesMeasureGroupPartitions(MeasureGroup mg)  
{  
    Partition part;  
    part = mg.Partitions.FindByName("Internet_Sales_184");  
    if ( part != null)  
       part.Drop();  
    part = mg.Partitions.Add("Internet_Sales_184");  
    part.StorageMode = StorageMode.Molap;  
    part.Source = new QueryBinding(db.DataSources[0].ID, "SELECT * FROM [dbo].[FactInternetSales] WHERE OrderDateKey <= '184'");  
    part.Slice = "[Date].[Calendar Year].&[2001]";  
    part.Annotations.Add("LastOrderDateKey", "184");  
  
    part = mg.Partitions.FindByName("Internet_Sales_549");  
    if ( part != null)  
       part.Drop();  
    part = mg.Partitions.Add("Internet_Sales_549");  
    part.StorageMode = StorageMode.Molap;  
    part.Source = new QueryBinding(db.DataSources[0].ID, "SELECT * FROM [dbo].[FactInternetSales] WHERE OrderDateKey > '184' AND OrderDateKey <= '549'");  
    part.Slice = "[Date].[Calendar Year].&[2002]";  
    part.Annotations.Add("LastOrderDateKey", "549");  
  
    part = mg.Partitions.FindByName("Internet_Sales_914");  
    if ( part != null)  
       part.Drop();  
    part = mg.Partitions.Add("Internet_Sales_914");  
    part.StorageMode = StorageMode.Molap;  
    part.Source = new QueryBinding(db.DataSources[0].ID, "SELECT * FROM [dbo].[FactInternetSales] WHERE OrderDateKey > '549' AND OrderDateKey <= '914'");  
    part.Slice = "[Date].[Calendar Year].&[2003]";  
    part.Annotations.Add("LastOrderDateKey", "914");  
}  
```  
  
###  <a name="ProcPart"></a>パーティションの処理  
 パーティションの処理は、<xref:Microsoft.AnalysisServices.Partition> オブジェクトの Process メソッドを使用して簡単に実行できます。  
  
 処理オプションの詳細については、次を参照してください。[オブジェクトの処理 & #40 です。XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/processing-objects-xmla.md)と[多次元モデル &#40; の処理Analysis Services &#41;](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 次のサンプル コードは、指定されたメジャー グループのすべてのパーティションを完全に処理します。  
  
```  
static void FullProcessAllPartitions(MeasureGroup mg)  
{  
    foreach (Partition part in mg.Partitions)  
        part.Process(ProcessType.ProcessFull);  
}  
```  
  
### <a name="merging-partitions"></a>パーティションのマージ  
 パーティションのマージとは、複数のパーティションを 1 つのパーティションに統合するための任意の操作のことです。  
  
 パーティションのマージは <xref:Microsoft.AnalysisServices.Partition> オブジェクトのメソッドです。 このコマンドは、1 つ以上のマージ元パーティションのデータをマージ先パーティションにマージし、マージ元パーティションを削除します。  
  
 パーティションは、次の基準をすべて満たす場合のみマージできます。  
  
-   各パーティションが同じメジャー グループに属している。  
  
-   各パーティションが同じモード (MOLAP、HOLAP、および ROLAP) で格納されている。  
  
-   各パーティションが同じサーバー上に格納されている (同じサーバー上に格納されているリモート パーティションはマージ可能です)。  
  
 以前のバージョンとは異なりで[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]ソースのすべてのパーティションは、同一の集計デザインである必要はありません。  
  
 マージ先パーティションの集計のセットは、マージ コマンドを実行する前の状態の集計のセットと同一になります。  
  
 次のサンプル コードは、指定されたメジャー グループのすべてのパーティションをマージします。 各パーティションは、メジャー グループの最初のパーティションにマージされます。  
  
```  
static void MergeAllPartitions(MeasureGroup mg)  
{  
    if (mg.Partitions.Count > 1)  
    {  
        Partition[] partArray = new Partition[mg.Partitions.Count - 1];  
        for (int i = 1; i < mg.Partitions.Count; i++)  
            partArray[i - 1] = mg.Partitions[i];  
        mg.Partitions[0].Merge(partArray);  
        //To have last changes in the server reflected in AMO  
        mg.Refresh();  
    }  
```  
  
##  <a name="AD"></a>Aggregation オブジェクト  
 集計をデザインして 1 つ以上のパーティションに適用するには、<xref:Microsoft.AnalysisServices.Aggregation> オブジェクトをプログラミングします。  
  
### <a name="creating-and-dropping-aggregations"></a>集計の作成および削除  
 <xref:Microsoft.AnalysisServices.AggregationDesign> オブジェクトの DesignAggregations メソッドを使用すると、集計を容易に作成してメジャー グループまたはパーティションに割り当てることができます。 <xref:Microsoft.AnalysisServices.AggregationDesign> オブジェクトはパーティションから独立したオブジェクトです。<xref:Microsoft.AnalysisServices.AggregationDesign> オブジェクトは <xref:Microsoft.AnalysisServices.MeasureGroup> オブジェクトに格納されています。 最適化レベル (0 ～ 100) またはストレージ レベル (バイト) を指定して集計をデザインできます。 複数のパーティションで同一の集計デザインを使用できます。  
  
 次のサンプル コードは、指定されたメジャー グループのすべてのパーティションの集計を作成します。 パーティション内の既存の集計はすべて削除されます。  
  
```  
static public String DesignAggregationsOnPartitions(MeasureGroup mg, double optimizationWanted, double maxStorageBytes)  
{  
    double optimization = 0;  
    double storage = 0;  
    long aggCount = 0;  
    bool finished = false;  
    AggregationDesign ad = null;  
    String aggDesignName;  
    String AggregationsDesigned = "";  
    aggDesignName = mg.AggregationPrefix + "_" + mg.Name;  
    ad = mg.AggregationDesigns.Add();  
    ad.Name = aggDesignName;  
    ad.InitializeDesign();  
    while ((!finished) && (optimization < optimizationWanted) && (storage < maxStorageBytes))  
    {  
        ad.DesignAggregations(out optimization, out storage, out aggCount, out finished);  
    }  
    ad.FinalizeDesign();  
    foreach (Partition part in mg.Partitions)  
    {  
        part.AggregationDesignID = ad.ID;  
        AggregationsDesigned += aggDesignName + " = " + aggCount.ToString() + " aggregations designed\r\n\tOptimization: " + optimization.ToString() + "/" + optimizationWanted.ToString() + "\n\r\tStorage: " + storage.ToString() + "/" + maxStorageBytes.ToString() + " ]\n\r";  
     }  
     return AggregationsDesigned;  
}  
```  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices>   
 [AMO クラスの概要](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [AMO OLAP クラス](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-olap-classes.md)   
 [論理アーキテクチャと #40 です。Analysis Services - 多次元データ &#41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [データベース オブジェクト & #40 です。Analysis Services - 多次元データ &#41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)   
 [多次元モデル &#40; の処理Analysis Services &#41;](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
 [Analysis Services 多次元モデリング チュートリアル用サンプル データとプロジェクトをインストールします。](../../../analysis-services/install-sample-data-and-projects.md)  
  
  

