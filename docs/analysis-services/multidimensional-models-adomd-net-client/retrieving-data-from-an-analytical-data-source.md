---
title: "分析データ ソースからデータを取得する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- data retrieval [ADOMD.NET]
- retrieving data
- ADOMD.NET, data retrieval
- data retrieval [ADOMD.NET], about retrieving data
ms.assetid: 88358189-28aa-4bc7-8dda-5a92e3a012b8
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 473813a85d925bc98f914293ae075a7254597b6d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="retrieving-data-from-an-analytical-data-source"></a>分析データ ソースからのデータの取得
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]接続を作成するし、クエリを作成すると、すべてのデータを取得できます。 ADOMD.NET では、次の 3 つの異なるオブジェクトを使用してデータを取得することができます (<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>、 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>、および<xref:System.Xml.XmlReader>) のいずれかを呼び出すことによって、 **Execute**のメソッド、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>オブジェクト。  
  
 これら 3 つのオブジェクトは、対話性とオーバーヘッドがそれぞれ異なります。  
  
-   *対話機能*使いやすさと、オブジェクト モデルを通じて利用可能な情報の量を表します。  
  
-   *オーバーヘッド*オブジェクト モデルとオブジェクト モデルがデータを取得する速度のために必要なメモリの量、サーバーへのネットワーク接続経由でオブジェクト モデルを生成するトラフィックの量を指します。  
  
 次の表は、各オブジェクトの対話性とオーバーヘッドを示しています。それぞれの違いを確認したうえで、アプリケーションに最適なデータ取得オブジェクトを選択してください。  
  
|Object|対話性|オーバーヘッド|次元の保持|使用方法に関する情報|  
|------------|-------------------|--------------|----------------------------|-----------------------|  
|<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>|最も高い|やや大きい (結果として、データの取得は最も低速)|可|[セルセットを使用したデータの取得](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-cellset.md)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter>|中程度|中程度|不可|[DataAdapter からの DataSet の読み込み](http://go.microsoft.com/fwlink/?LinkId=70016)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>|中程度|中程度|不可|[AdomdDataReader を使用したデータの取得](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-adomddatareader.md)|  
|<xref:System.Xml.XmlReader>|最低|最も小さい (その結果、データの取得は最も高速)|可|[XmlReader を使用したデータの取得](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-xmlreader.md)|  
  
## <a name="see-also"></a>参照  
 [ADOMD.NET クライアント プログラミング](../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)  
  
  
