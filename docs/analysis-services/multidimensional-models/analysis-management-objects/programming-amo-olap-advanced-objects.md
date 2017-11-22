---
title: "プログラミング AMO OLAP オブジェクトの詳細 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
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
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- programming [AMO]
- Analysis Management Objects, OLAP
- OLAP [AMO]
- AMO, OLAP
ms.assetid: b75f35a7-32df-4f22-983d-324aa98e15a9
caps.latest.revision: "23"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b58d475dfab97de8076bf058bfdd1171ddb37f35
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="programming-amo-olap-advanced-objects"></a>高度な AMO OLAP オブジェクトのプログラミング
  このトピックでは、高度な OLAP オブジェクトの分析管理オブジェクト (AMO) プログラミングの詳細について説明します。 このトピックには、次のセクションが含まれます。  
  
-   [Action オブジェクト](#Action)  
  
-   [Kpi オブジェクト](#KPI)  
  
-   [Perspective オブジェクト](#Persp)  
  
-   [ProactiveCaching オブジェクト](#PC)  
  
-   [Translation オブジェクト](#Transl)  
  
##  <a name="Action"></a>Action オブジェクト  
 アクション クラスは、キューブの特定領域の参照時に、アクティブな応答を作成するために使用します。 Action オブジェクトは AMO を使用して定義できます。ただし、このオブジェクトはデータを参照するクライアント アプリケーションから使用されます。 アクションにはさまざまな種類があり、その種類に応じて作成する必要があります。 アクションの種類は次のとおりです。  
  
-   ドリルスルー アクション。このアクションが発生したキューブで選択されているセル内のデータを表す行セットを返します。  
  
-   レポート アクション。このアクションは、実行されたキューブで選択されているセクションに関連付けられた [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] からレポートを返します。  
  
-   標準アクション。このアクションは、実行されたキューブで選択されているセクションに関連付けられたアクション要素 (URL、HTML、DataSet、RowSet などの要素) を返します。  
  
 Action オブジェクトを作成するには、次の手順を実行します。  
  
1.  Action の派生オブジェクトを作成し、基本属性を設定します。  
  
     基本属性には、アクションの種類、対象の種類またはキューブのセクション、対象またはアクションが使用可能なキューブの特定領域、キャプション、およびキャプションが MDX 式であることなどがあります。  
  
2.  アクションの種類の特別な属性を設定します。  
  
     3 種類のアクションはそれぞれ属性が異なります。パラメーターについては、次のサンプル コードを参照してください。  
  
3.  アクションをキューブ コレクションに追加してキューブを更新します。 アクションは更新可能なオブジェクトではありません。  
  
 アクションのテストには別のプログラム アプリケーションが必要です。 アクションは [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] でテストできます。 最初に、インストールする必要があります[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]サンプルを参照してください[多次元モデル &#40; の処理Analysis Services &#41;](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 次のサンプル コードでは、Adventure Works Analysis Services Project サンプルから 3 つの異なるアクションをレプリケートします。 次のサンプルを使用して作成したアクションは "My" から始まるため、アクションを区別することができます。  
  
```  
static public void CreateActions(Cube cube)  
{  
    #region Adding a drillthrough action  
    // Verify That action exists and drop it  
    if (cube.Actions.ContainsName("My Reseller Details"))  
        cube.Actions.Remove("My Drillthrough Action",true);  
  
    //Create a Drillthrough action  
    DrillThroughAction dtaction = new DrillThroughAction("My Reseller Details", "My Drillthrough Action");  
  
    //Define the Action  
    dtaction.Type = ActionType.DrillThrough;  
    dtaction.TargetType = ActionTargetType.Cells;  
    dtaction.Target = "MeasureGroupMeasures(\"Reseller Sales\")";  
    dtaction.Caption = "My Drillthrough...";  
    dtaction.CaptionIsMdx = false;  
  
    #region create drillthrough action specifics  
    //Adding Drillthrough columns  
    //Adding Measure columns to the drillthrough  
    MeasureGroup mg = cube.MeasureGroups.FindByName("Reseller Sales");  
    MeasureBinding mb1 = new MeasureBinding();  
    mb1.MeasureID = mg.Measures.FindByName( "Reseller Sales Amount").ID;  
    dtaction.Columns.Add(mb1);  
  
    MeasureBinding mb2 = new MeasureBinding();  
    mb2.MeasureID = mg.Measures.FindByName("Reseller Order Quantity").ID;  
    dtaction.Columns.Add(mb2);  
  
    MeasureBinding mb3 = new MeasureBinding();  
    mb3.MeasureID = mg.Measures.FindByName("Reseller Unit Price").ID;  
    dtaction.Columns.Add(mb3);  
  
    //Adding Dimension Columns to the drillthrough  
    CubeAttributeBinding cb1 = new CubeAttributeBinding();  
    cb1.CubeID = cube.ID;  
    cb1.CubeDimensionID = cube.Dimensions.FindByName("Reseller").ID;  
    cb1.AttributeID = "Reseller Name";  
    cb1.Type = AttributeBindingType.All;  
    dtaction.Columns.Add(cb1);  
  
    CubeAttributeBinding cb2 = new CubeAttributeBinding();  
    cb2.CubeID = cube.ID;  
    cb2.CubeDimensionID = cube.Dimensions.FindByName("Product").ID;  
    cb2.AttributeID = "Product Name";  
    cb2.Type = AttributeBindingType.All;  
    dtaction.Columns.Add(cb2);  
    #endregion  
  
    //Add the defined action to the cube  
    cube.Actions.Add(dtaction);  
    #endregion  
  
    #region Adding a Standard action  
    // Verify That action exists and drop it  
    if (cube.Actions.ContainsName("My City Map"))  
        cube.Actions.Remove("My Action", true);  
  
    //Create a Drillthrough action  
    StandardAction stdaction = new StandardAction("My City Map", "My Action");  
  
    //Define the Action  
    stdaction.Type = ActionType.Url;  
    stdaction.TargetType = ActionTargetType.AttributeMembers;  
    stdaction.Target = "[Geography].[City]";  
    stdaction.Caption = "\"My View Map for \" + [Geography].[City].CurrentMember.Member_Caption + \"...\"";  
    stdaction.CaptionIsMdx = true;  
  
    #region create standard action specifics  
    stdaction.Expression = "\"http://maps.msn.com/home.aspx?plce1=\" + " +  
        "[Geography].[City].CurrentMember.Name + \",\" + " +  
        "[Geography].[State-Province].CurrentMember.Name + \",\" + " +  
        "[Geography].[Country].CurrentMember.Name + " +  
        "\"&regn1=\" + " +  
        "Case " +  
            "When [Geography].[Country].CurrentMember Is " +  
                    "[Geography].[Country].&[Australia] " +  
                "Then \"3\" " +  
            "When [Geography].[Country].CurrentMember Is " +  
                    "[Geography].[Country].&[Canada] " +  
                "Or [Geography].[Country].CurrentMember Is " +  
                    "[Geography].[Country].&[United States] " +  
                "Then \"0\" " +  
                "Else \"1\" " +  
        "End ";  
    #endregion  
  
    //Add the defined action to the cube  
    cube.Actions.Add(stdaction);  
  
    #endregion  
  
    #region Adding a Reporting action  
    // Verify That action exists and drop it  
    if (cube.Actions.ContainsName("My Sales Reason Comparisons"))  
        cube.Actions.Remove("My Report Action", true);  
  
    //Create a Report action  
    ReportAction rsaction = new ReportAction("My Sales Reason Comparisonsp", "My Report Action");  
  
    //Define the Action  
    rsaction.Type = ActionType.Report;  
    rsaction.TargetType = ActionTargetType.AttributeMembers;  
    rsaction.Target = "[Product].[Category]";  
    rsaction.Caption = "\"My Sales Reason Comparisons for \" + [Product].[Category].CurrentMember.Member_Caption + \"...\"";  
    rsaction.CaptionIsMdx = true;  
  
    #region create Report action specifics  
    rsaction.ReportServer = "MyRSSamplesServer";  
    rsaction.Path = "ReportServer?/AdventureWorks Sample Reports/Sales Reason Comparisons";  
    rsaction.ReportParameters.Add("ProductCategory", "UrlEscapeFragment( [Product].[Category].CurrentMember.UniqueName )");  
    rsaction.ReportFormatParameters.Add("rs:Command", "Render");  
    rsaction.ReportFormatParameters.Add("rs:Renderer", "HTML5");  
    #endregion  
  
    //Add the defined action to the cube  
    cube.Actions.Add(rsaction);  
  
    #endregion  
}  
```  
  
##  <a name="KPI"></a>Kpi オブジェクト  
 主要業績評価指標 (KPI) はキューブ内のメジャー グループに関連付けられた、ビジネスの成功の評価に使用される計算のコレクションです。 <xref:Microsoft.AnalysisServices.Kpi> オブジェクトは AMO で定義できます。ただし、このオブジェクトはデータを参照するクライアント アプリケーションから使用されます。  
  
 作成する、<xref:Microsoft.AnalysisServices.Kpi>オブジェクトには、次の手順が必要です。  
  
1.  <xref:Microsoft.AnalysisServices.Kpi> オブジェクトを作成し、基本属性を設定します。  
  
     基本属性には、説明、表示フォルダー、関連付けられたメジャー グループ、および値があります。 表示フォルダーは、エンド ユーザーが KPI を見つけることができるように、クライアント アプリケーションに KPI の格納場所を指示します。 関連付けられたメジャー グループは、すべての MDX 計算の参照元となるメジャー グループを示します。 値は、業績評価指標の実際の値を MDX 式で表します。  
  
2.  KPI 指標、目標、状態、および傾向を定義します。  
  
     指標は -1 ～ 1 の範囲内で評価される MDX 式です。ただし、指標の値の範囲を定義するのはブラウザー アプリケーションです。  
  
3.  [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] で KPI を参照する場合、-1 未満の値は -1 として処理され、1 を超える値は 1 として処理されます。  
  
4.  グラフィック イメージを定義します。  
  
     グラフィック イメージは文字列値であり、表示する正しいイメージのセットを識別するために、クライアント アプリケーション内で参照として使用されます。 また、グラフィック イメージの文字列は表示関数の動作も定義します。 通常、範囲は奇数個の状態 ("良い" ～ "悪い" まで) に分けられており、イメージ セットのイメージが各状態に割り当てられています。  
  
     [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] を使用して KPI を参照した場合、名前に応じて指標の範囲が 3 つまたは 5 つの状態に分けられます。 さらに、範囲が逆になる (-1 が "良い"、1 が "悪い") 名前もあります。 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] における範囲内の 3 つの状態は次のとおりです。  
  
    -   悪い =-1 ～-0.5  
  
    -   [Ok] を-0.4999 を-0.4999 を =  
  
    -   0.50 ～ 1 の良い =  
  
     [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] における範囲内の 5 つの状態は次のとおりです。  
  
    -   悪い = -1 ～ -0.75  
  
    -   リスク = -0.7499 ～ -0.25  
  
    -   OK = -0.2499 ～ 0.2499  
  
    -   発生させる = 0.25 ~ 0.7499  
  
    -   良い = 0.75 ～ 1  
  
 次の表に、イメージに関連付けられた使用法、名前、および状態の数を示します。  
  
|イメージの使用法|イメージの名前|状態の数|  
|-----------------|----------------|----------------------|  
|[状態]|図形|3|  
|[状態]|信号機|3|  
|[状態]|道路標識|3|  
|[状態]|ゲージ|3|  
|[状態]|反転ゲージ|5|  
|[状態]|温度計|3|  
|[状態]|シリンダー|3|  
|[状態]|外観|3|  
|[状態]|変位の矢印|3|  
|傾向|標準の矢印|3|  
|傾向|状態の矢印|3|  
|傾向|反転した状態の矢印|5|  
|傾向|外観|3|  
  
1.  KPI は更新可能なオブジェクトではないため、KPI をキューブ コレクションに追加してキューブを更新します。  
  
 KPI のテストには別のプログラム アプリケーションが必要です。 KPI は [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] でテストできます。  
  
 次のサンプル コードでは、Adventure Works Analysis Services Project サンプルに含まれる Adventure Works キューブの KPI を "Financial Perpective/Grow Revenue" フォルダーに作成します。  
  
```  
static public void CreateKPIs(Cube cube)  
{  
    Kpi kpi = cube.Kpis.Add("My Internet Revenue", "My Internet Revenue");  
    kpi.Description = "(My) Revenue achieved through direct sales via Interner";  
    kpi.DisplayFolder = "\\Financial Perspective\\Grow Revenue";  
    kpi.AssociatedMeasureGroupID = "Internet Sales";  
    kpi.Value = "[Measures].[Internet Sales Amount]";  
    #region Goal  
    kpi.Goal = "Case" +  
               "     When IsEmpty" +  
               "          (" +  
               "            ParallelPeriod" +  
               "            (" +  
               "              [Date].[Fiscal Time].[Fiscal Year]," +  
               "              1," +  
               "              [Date].[Fiscal Time].CurrentMember" +  
               "            )" +  
               "          )" +   
               "     Then [Measures].[Internet Sales Amount]" +  
               "     Else 1.10 *" +  
               "          (" +  
               "            [Measures].[Internet Sales Amount]," +  
               "            ParallelPeriod" +  
               "            (" +  
               "              [Date].[Fiscal Time].[Fiscal Year]," +  
               "              1," +  
               "              [Date].[Fiscal Time].CurrentMember" +  
               "            )" +  
               "          ) " +  
               " End";  
    #endregion  
    #region Status  
    kpi.Status = "Case" +  
                 "   When KpiValue( \"Internet Revenue\" ) / KpiGoal ( \"Internet Revenue\" ) >= .95 " +  
                 "   Then 1 " +  
                 "   When KpiValue( \"Internet Revenue\" ) / KpiGoal ( \"Internet Revenue\" ) <  .95 " +  
                 "        And  " +  
                 "        KpiValue( \"Internet Revenue\" ) / KpiGoal ( \"Internet Revenue\" ) >= .85 " +  
                 "   Then 0 " +  
                 "   Else -1 " +  
                 "End";  
    #endregion  
    #region Trend  
    kpi.Trend = "Case " +  
                "    When VBA!Abs " +  
                "         ( " +  
                "           KpiValue( \"Internet Revenue\" ) -  " +  
                "           ( " +  
                "             KpiValue ( \"Internet Revenue\" ), " +  
                "             ParallelPeriod " +  
                "             (  " +  
                "               [Date].[Fiscal Time].[Fiscal Year], " +  
                "               1, " +  
                "               [Date].[Fiscal Time].CurrentMember " +  
                "             ) " +  
                "           ) / " +  
                "           ( " +  
                "             KpiValue ( \"Internet Revenue\" ), " +  
                "             ParallelPeriod " +  
                "             (  " +  
                "               [Date].[Fiscal Time].[Fiscal Year], " +  
                "               1, " +  
                "               [Date].[Fiscal Time].CurrentMember " +  
                "             ) " +  
                "           )   " +  
                "         ) <=.02  " +  
                "    Then 0 " +  
                "    When KpiValue( \"Internet Revenue\" ) -  " +  
                "         ( " +  
                "           KpiValue ( \"Internet Revenue\" ), " +  
                "           ParallelPeriod " +  
                "           (  " +  
                "             [Date].[Fiscal Time].[Fiscal Year], " +  
                "             1, " +  
                "             [Date].[Fiscal Time].CurrentMember " +  
                "           ) " +  
                "         ) / " +  
                "         ( " +  
                "           KpiValue ( \"Internet Revenue\" ), " +  
                "           ParallelPeriod " +  
                "           (  " +  
                "             [Date].[Fiscal Time].[Fiscal Year], " +  
                "             1, " +  
                "             [Date].[Fiscal Time].CurrentMember " +  
                "           ) " +  
                "         )  >.02 " +  
                "    Then 1 " +  
                "    Else -1 " +  
                "End";  
    #endregion  
    kpi.TrendGraphic = "Standard Arrow";  
    kpi.StatusGraphic = "Cylinder";  
}.  
```  
  
##  <a name="Persp"></a>Perspective オブジェクト  
 <xref:Microsoft.AnalysisServices.Perspective> オブジェクトは AMO で定義できます。ただし、このオブジェクトはデータを参照するクライアント アプリケーションから使用されます。  
  
 作成する、<xref:Microsoft.AnalysisServices.Perspective>オブジェクトには、次の手順が必要です。  
  
1.  <xref:Microsoft.AnalysisServices.Perspective> オブジェクトを作成し、基本属性を設定します。  
  
     基本属性には、名前、既定のメジャー、説明、および注釈があります。  
  
2.  エンド ユーザーに表示される親キューブからすべてのオブジェクトを追加します。  
  
     キューブ ディメンション (属性および階層)、メジャー グループ (メジャーおよびメジャー グループ)、アクション、KPI、および計算を追加します。  
  
3.  パースペクティブは更新可能なオブジェクトではないため、パースペクティブをキューブ コレクションに追加してキューブを更新します。  
  
 パースペクティブのテストには別のプログラム アプリケーションが必要です。 パースペクティブは [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] でテストできます。  
  
 次のコードでは、指定したキューブに対して "Direct Sales" という名前のパースペクティブを作成します。  
  
```  
static public void CreatePerspectives(Cube cube)  
{  
    Perspective perspective = cube.Perspectives.Add("Direct Sales", "Direct Sales");  
    CubeDimension dim1 = cube.Dimensions.GetByName("Date");  
    PerspectiveDimension pdim1 = perspective.Dimensions.Add(dim1.DimensionID);  
    pdim1.Attributes.Add("Date");  
    pdim1.Attributes.Add("Calendar Year");  
    pdim1.Attributes.Add("Fiscal Year");  
    pdim1.Attributes.Add("Calendar Quarter");  
    pdim1.Attributes.Add("Fiscal Quarter");  
    pdim1.Attributes.Add("Calendar Month Number");  
    pdim1.Attributes.Add("Fiscal Month Number");  
    pdim1.Hierarchies.Add("Calendar Time");  
    pdim1.Hierarchies.Add("Fiscal Time");  
  
    CubeDimension dim2 = cube.Dimensions.GetByName("Product");  
    PerspectiveDimension pdim2 = perspective.Dimensions.Add(dim2.DimensionID);  
    pdim2.Attributes.Add("Product Name");  
    pdim2.Attributes.Add("Product Line");  
    pdim2.Attributes.Add("Model Name");  
    pdim2.Attributes.Add("List Price");  
    pdim2.Attributes.Add("Size");  
    pdim2.Attributes.Add("Weight");  
    pdim2.Hierarchies.Add("Product Model Categories");  
    pdim2.Hierarchies.Add("Product Categories");  
  
    PerspectiveMeasureGroup pmg = perspective.MeasureGroups.Add("Internet Sales");  
    pmg.Measures.Add("Internet Sales Amount");  
    pmg.Measures.Add("Internet Order Quantity");  
    pmg.Measures.Add("Internet Unit Price");  
  
    pmg = perspective.MeasureGroups.Add("Reseller Sales");  
    pmg.Measures.Add("Reseler Sales Amount");  
    pmg.Measures.Add("Reseller Order Quantity");  
    pmg.Measures.Add("Reseller Unit Price");  
  
    PerspectiveAction pact = perspective.Actions.Add("Drillthrough Action");  
  
    PerspectiveKpi pkpi = perspective.Kpis.Add("Internet Revenue");  
    Cube.Update();  
}  
```  
  
##  <a name="PC"></a>ProactiveCaching オブジェクト  
 <xref:Microsoft.AnalysisServices.ProactiveCaching> オブジェクトは AMO で定義できます。  
  
 作成する、<xref:Microsoft.AnalysisServices.ProactiveCaching>オブジェクトには、次の手順が必要です。  
  
1.  作成、<xref:Microsoft.AnalysisServices.ProactiveCaching>オブジェクト。  
  
     定義する基本属性はありません。  
  
2.  キャッシュの仕様を追加します。  
  
|仕様|Description|  
|-------------------|-----------------|  
|AggregationStorage|集計で使用するストレージの種類。<br /><br /> パーティションにのみ適用されます。 ディメンションである必要があります**正規です。**|  
|SilenceInterval|MOLAP イメージ作成を開始する前にキャッシュが存在する最短時間。|  
|[待機時間]|最も古い通知から MOLAP イメージが破棄される時点までの時間。|  
|SilenceOverrideInterval|初期通知の後、MOLAP イメージ作成が無条件で開始されるまでの時間。|  
|ForceRebuildInterval|新しい MOLAP イメージが削除された後、MOLAP イメージ作成が無条件で開始されるまでの時間 (通知なし)。|  
|OnlineMode|MOLAP イメージが使用可能になる時点。<br /><br /> いずれかになります**イミディ エイト**または**OnCacheComplete**です。|  
  
1.  <xref:Microsoft.AnalysisServices.ProactiveCaching> オブジェクトを親コレクションに追加します。 <xref:Microsoft.AnalysisServices.ProactiveCaching> は更新可能なオブジェクトではないため、親を更新する必要があります。  
  
 次のコード サンプルでは、指定されたデータベースの Adventure Works キューブに含まれる Internet Sales メジャー グループのすべてのパーティションに <xref:Microsoft.AnalysisServices.ProactiveCaching> オブジェクトを作成します。  
  
```  
static public void SetProactiveCachingSettings(Database db)  
{  
    ProactiveCaching pc;  
    if (db.Cubes.ContainsName("Adventure Works") && db.Cubes.FindByName("Adventure Works").MeasureGroups.ContainsName("Internet Sales"))  
    {  
        ProactiveCachingTablesBinding pctb;  
        TableNotification tn;  
  
        MeasureGroup mg = db.Cubes.FindByName("Adventure Works").MeasureGroups.FindByName("Internet Sales");  
        foreach(Partition part in mg.Partitions)  
        {  
            pc = new ProactiveCaching();  
            pc.AggregationStorage = ProactiveCachingAggregationStorage.MolapOnly;  
            pc.SilenceInterval = TimeSpan.FromSeconds(10);  
            pc.Latency = TimeSpan.FromSeconds(-1);  
            pc.SilenceOverrideInterval = TimeSpan.FromMinutes(10);  
            pc.ForceRebuildInterval = TimeSpan.FromSeconds(-1);  
            pc.Enabled = true;  
            pc.OnlineMode = ProactiveCachingOnlineMode.OnCacheComplete;  
            pctb = new ProactiveCachingTablesBinding();  
            pctb.NotificationTechnique = NotificationTechnique.Server;  
            tn = new TableNotification("[FactInternetSales]", "dbo");  
            pctb.TableNotifications.Add( tn);  
            pc.Source = pctb;  
  
            part.ProactiveCaching = pc;  
            part.Update();  
        }  
    }  
}  
```  
  
##  <a name="Transl"></a>Translation オブジェクト  
 Translation オブジェクトは AMO で定義できます。ただし、このオブジェクトはデータを参照するクライアント アプリケーションから使用されます。 Translation オブジェクトのコーディングは簡単です。 オブジェクトのキャプションの翻訳は、ロケール識別子とキャプションの翻訳の組によって提供されます。 すべてのキャプションで複数の翻訳を使用できます。 ディメンション、属性、階層、キューブ、メジャー グループ、メジャーなど、ほとんどの [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] オブジェクトに対して翻訳を提供できます。  
  
 次のコード サンプルでは、属性 Product Name の名前をスペイン語に翻訳します。  
  
```  
static public void CreateTranslations(Database db)  
{  
    //Spanish Tranlations for Product Category in Product Dimension  
    Dimension dim = db.Dimensions["Product"];  
    DimensionAttribute atr = dim.Attributes["Product Name"];  
    Translation tran = atr.Translations.Add(3082);  
    tran.Caption = "Nombre Producto";  
  
    dim.Update(UpdateOptions.ExpandFull);  
  
}  
```  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices>   
 [AMO クラスの概要](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [AMO OLAP クラス](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-olap-classes.md)   
 [論理アーキテクチャと #40 です。Analysis Services - 多次元データ &#41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [データベース オブジェクト &#40;です。Analysis Services - 多次元データ &#41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)   
 [多次元モデル &#40; の処理Analysis Services &#41;](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
 [Analysis Services 多次元モデリング チュートリアル用サンプル データとプロジェクトをインストールします。](../../../analysis-services/install-sample-data-and-projects.md)  
  
  
