---
title: AMO データ マイニング オブジェクトをプログラミング |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: amo
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9ba64d48fe93ea047210c00717d84cde0e4dcae9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="programming-amo-data-mining-objects"></a>AMO データ マイニング オブジェクトのプログラミング
  AMO を使用すれば、データ マイニング オブジェクトを簡単にプログラミングできます。 まず、マイニング プロジェクトをサポートするデータ構造モデルを作成します。 次に、マイニング アルゴリズムをサポートするデータ マイニング モデルを作成します。マイニング アルゴリズムは、データに含まれる未知のリレーションシップを予測または検出するために使用します。 構造やアルゴリズムなどのマイニング プロジェクトを作成したら、マイニング モデルを処理することにより、後でクライアント アプリケーションからクエリや予測を行うときに使用するトレーニングされたモデルを取得できます。  
  
 1 つ覚えておく必要があるのは、AMO ではクエリを実行できないという点です。AMO は、マイニング構造およびマイニング モデルの管理に使用します。 クエリを実行する、データを使用して[ADOMD.NET での開発](../../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md)です。  
  
 このトピックには、次のセクションが含まれます。  
  
-   [MiningStructure オブジェクト](#MiningStructure)  
  
-   [MiningModel オブジェクト](#MiningModel)  
  
##  <a name="MiningStructure"></a> MiningStructure オブジェクト  
 マイニング構造は、すべてのマイニング モデルの作成に使用するデータ構造の定義です。 マイニング構造には、データベースで定義されたデータ ソース ビューへのバインドと、マイニング モデル内のすべての列定義が含まれます。 マイニング構造には複数のマイニング モデルを含めることができます。  
  
 作成する、<xref:Microsoft.AnalysisServices.MiningStructure>オブジェクトには、次の手順が必要です。  
  
1.  <xref:Microsoft.AnalysisServices.MiningStructure> オブジェクトを作成し、基本属性を設定します。 基本属性には、オブジェクト名、オブジェクト ID (内部 ID)、およびデータ ソース バインドがあります。  
  
2.  モデルの列を作成します。 列はスカラー定義またはテーブル定義のいずれかです。  
  
     各列には、名前、内部 ID、種類、コンテンツ定義、およびバインドが必要です。  
  
3.  オブジェクトの Update メソッドを使用して、サーバー上で <xref:Microsoft.AnalysisServices.MiningStructure> オブジェクトを更新します。  
  
     マイニング構造は処理可能です。マイニング構造を処理すると、子マイニング モデルが処理または再トレーニングされます。  
  
 次のサンプル コードでは、売り上げを時系列で予測するマイニング構造を作成します。 サンプル コードを実行する前に確認するデータベース*db*のパラメーターとして渡される`CreateSalesForecastingMiningStructure`に含まれています`db.DataSourceViews[0]`ビューへの参照*dbo.vTimeSeries* で[!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)]サンプル データベース。  
  
```  
public static MiningStructure CreateSalesForecastingMiningStructure(Database db)  
{  
    MiningStructure ms = db.MiningStructures.FindByName("Forecasting Sales Structure");  
    if (ms != null)  
        ms.Drop();  
    ms = db.MiningStructures.Add("Forecasting Sales Structure", "Forecasting Sales Structure");  
    ms.Source = new DataSourceViewBinding(db.DataSourceViews[0].ID);  
  
    ScalarMiningStructureColumn amount = ms.Columns.Add("Amount", "Amount");  
    amount.Type = MiningStructureColumnTypes.Double;  
    amount.Content = MiningStructureColumnContents.Continuous;  
    amount.KeyColumns.Add("vTimeSeries", "Amount", OleDbType.Currency);  
  
    ScalarMiningStructureColumn modelRegion = ms.Columns.Add("Model Region", "Model Region");  
    modelRegion.IsKey = true;  
    modelRegion.Type = MiningStructureColumnTypes.Text;  
    modelRegion.Content = MiningStructureColumnContents.Key;  
    modelRegion.KeyColumns.Add("vTimeSeries", "ModelRegion", OleDbType.WChar, 56);  
  
    ScalarMiningStructureColumn qty = ms.Columns.Add("Quantity", "Quantity");  
    qty.Type = MiningStructureColumnTypes.Long;  
    qty.Content = MiningStructureColumnContents.Continuous;  
    qty.KeyColumns.Add("vTimeSeries", "Quantity", OleDbType.Integer);  
  
    ScalarMiningStructureColumn timeIndex = ms.Columns.Add("TimeIndex", "TimeIndex");  
    timeIndex.IsKey = true;  
    timeIndex.Type = MiningStructureColumnTypes.Long;  
    timeIndex.Content = MiningStructureColumnContents.KeyTime;  
    timeIndex.KeyColumns.Add("vTimeSeries", "TimeIndex", OleDbType.Integer);  
  
    ms.Update();  
    return ms;  
}  
```  
  
##  <a name="MiningModel"></a> MiningModel オブジェクト  
 マイニング モデルは、マイニング アルゴリズムで使用されるすべての列および列定義のリポジトリです。  
  
 作成する、<xref:Microsoft.AnalysisServices.MiningModel>オブジェクトには、次の手順が必要です。  
  
1.  <xref:Microsoft.AnalysisServices.MiningModel> オブジェクトを作成し、基本属性を設定します。  
  
     基本属性には、オブジェクト名、オブジェクト ID (内部 ID)、およびマイニング アルゴリズムの仕様があります。  
  
2.  マイニング モデルの列を追加します。 列の 1 つをケース キーとして定義する必要があります。  
  
3.  オブジェクトの Update メソッドを使用して、サーバー上で <xref:Microsoft.AnalysisServices.MiningModel> オブジェクトを更新します。  
  
     <xref:Microsoft.AnalysisServices.MiningModel> オブジェクトは、親の <xref:Microsoft.AnalysisServices.MiningStructure> に含まれる他のモデルから独立して処理できます。  
  
 次のサンプル コードでは、"Forecasting Sales Structure" マイニング構造に基づいて Microsoft タイム シリーズ予測モデルを作成します。  
  
```  
public static MiningModel CreateSalesForecastingMiningModel(MiningStructure ms)  
{  
    if (ms.MiningModels.ContainsName("Sales Forecasting Model"))  
    {  
        ms.MiningModels["Sales Forecasting Model"].Drop();  
    }  
    MiningModel mm = ms.CreateMiningModel(true, "Sales Forecasting Model");  
    mm.Algorithm = MiningModelAlgorithms.MicrosoftTimeSeries;  
    mm.AlgorithmParameters.Add("PERIODICITY_HINT", "{12}");  
  
    MiningModelColumn amount = new MiningModelColumn();  
    amount.SourceColumnID = "Amount";  
    amount.Usage = MiningModelColumnUsages.Predict;  
  
    MiningModelColumn modelRegion = new MiningModelColumn();  
    modelRegion.SourceColumnID = "Model Region";  
    modelRegion.Usage = MiningModelColumnUsages.Key;  
  
    MiningModelColumn qty = new MiningModelColumn();  
    qty.SourceColumnID = "Quantity";  
    qty.Usage = MiningModelColumnUsages.Predict;  
  
    MiningModelColumn ti = new MiningModelColumn();  
    ti.SourceColumnID = "TimeIndex";  
    ti.Usage = MiningModelColumnUsages.Key;  
  
    mm.Update();  
    mm.Process(ProcessType.ProcessFull);  
    return mm;  
}  
```  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices>   
 [AMO 基礎クラス](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-fundamental-classes.md)   
 [AMO クラスの概要](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [AMO データ マイニング クラス](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-data-mining-classes.md)   
 [論理アーキテクチャと #40 です。Analysis Services - 多次元データ & #41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [データベース オブジェクト & #40 です。Analysis Services - 多次元データ & #41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  
