---
title: ADOMD.NET オブジェクト モデルを扱う |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: adomd
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bc5162230c47692c22e0fdedef9133c000948e19
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="retrieving-metadata---working-with-adomdnet-object-model"></a>ADOMD.NET オブジェクト モデルの操作のメタデータを取得します。
  ADOMD.NET は、分析データ ソース内のキューブと下位オブジェクトを表示するためのオブジェクト モデルです。 ただし、分析データ ソースのすべてのメタデータを、このオブジェクト モデルで操作できるわけではありません。 このオブジェクト モデルでアクセスできるのは、ユーザーがコマンドを対話的に作成する際、クライアント アプリケーションに表示されると役立つ情報だけです。 提示するメタデータの複雑さが軽減されたことで、ADOMD.NET オブジェクト モデルがより使いやすくなりました。  
  
 ADOMD.NET オブジェクト モデルでは、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトを使用して、分析データ ソースで定義されているオンライン分析処理 (OLAP) キューブとマイニング モデルの情報、およびディメンション、名前付きセット、マイニング アルゴリズムなどの関連オブジェクトにアクセスできます。  
  
## <a name="retrieving-olap-metadata"></a>OLAP メタデータの取得  
 各 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトには、ユーザーまたはアプリケーションが利用できるキューブを表す <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> オブジェクトのコレクションがあります。 <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> オブジェクトは、キューブに関する情報に加え、ディメンション、主要業績評価指標、メジャー、名前付きセットなど、そのキューブに関連するさまざまなオブジェクトの情報を提供します。  
  
 複数の OLAP サーバーをサポートするよう設計されたクライアント アプリケーションでメタデータを表示する場合や、一般的なメタデータを表示したり、アクセスしたりする場合は、できる限り <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> オブジェクトを使用してください。  
  
> [!NOTE]  
>  プロバイダー固有のメタデータが必要な場合、または詳細なメタデータの表示やアクセスを行う場合は、スキーマ行セットを使用してメタデータを取得する必要があります。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)」を参照してください。  
  
 次の例では、<xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> オブジェクトを使用して、表示可能なキューブとそのディメンションをローカル サーバーから取得します。  
  
 [!code-cs[Adomd.NetClient#RetrieveCubesAndDimensions](../../analysis-services/multidimensional-models-adomd-net-client/codesnippet/csharp/retrieving-metadata-work_1_1.cs)]  
  
## <a name="retrieving-data-mining-metadata"></a>データ マイニング メタデータの取得  
 各 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトは、データ ソースのデータ マイニング機能に関する情報を提供する複数のコレクションで構成されます。  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningModelCollection> には、データ ソース内のマイニング モデルの一覧が含まれています。  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningServiceCollection> は、使用可能なマイニング アルゴリズムに関する情報を提供します。  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningStructureCollection> は、サーバーのマイニング構造に関する情報を示します。  
  
 サーバー上のマイニング モデルに対するクエリの実行方法を判断するには、<xref:Microsoft.AnalysisServices.AdomdServer.MiningModel.Columns%2A> コレクションを反復処理します。 各 <xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn> オブジェクトは以下の特性を公開します。  
  
-   オブジェクトが入力列かどうか (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.IsInput%2A>)。  
  
-   オブジェクトが予測列かどうか (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.IsPredictable%2A>)。  
  
-   不連続の列に関連付けられた値 (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.Values%2A>)。  
  
-   列内のデータの型 (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.Type%2A>)。  
  
## <a name="see-also"></a>参照  
 [分析データ ソースからのメタデータの取得](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md)  
  
  
