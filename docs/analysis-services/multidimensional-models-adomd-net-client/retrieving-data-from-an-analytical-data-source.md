---
title: 分析データ ソースからデータを取得する |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: adomd
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 91976fcd4f3922041152fe41c0e03f89e05483b2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="retrieving-data-from-an-analytical-data-source"></a>分析データ ソースからのデータの取得
  接続を確立し、クエリを作成すると、任意のデータを取得できます。 ADOMD.NET では、次の 3 つの異なるオブジェクトを使用してデータを取得することができます (<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>、 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>、および<xref:System.Xml.XmlReader>) のいずれかを呼び出すことによって、 **Execute**のメソッド、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>オブジェクト。  
  
 これら 3 つのオブジェクトは、対話性とオーバーヘッドがそれぞれ異なります。  
  
-   *対話機能*使いやすさと、オブジェクト モデルを通じて利用可能な情報の量を表します。  
  
-   *オーバーヘッド*オブジェクト モデルとオブジェクト モデルがデータを取得する速度のために必要なメモリの量、サーバーへのネットワーク接続経由でオブジェクト モデルを生成するトラフィックの量を指します。  
  
 次の表は、各オブジェクトの対話性とオーバーヘッドを示しています。それぞれの違いを確認したうえで、アプリケーションに最適なデータ取得オブジェクトを選択してください。  
  
|オブジェクト|対話性|オーバーヘッド|次元の保持|使用方法に関する情報|  
|------------|-------------------|--------------|----------------------------|-----------------------|  
|<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>|最も高い|やや大きい (結果として、データの取得は最も低速)|はい|[セルセットを使用したデータの取得](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-cellset.md)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter>|中程度|中程度|いいえ|[DataAdapter からの DataSet の読み込み](http://go.microsoft.com/fwlink/?LinkId=70016)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>|中程度|中程度|いいえ|[AdomdDataReader を使用したデータの取得](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-adomddatareader.md)|  
|<xref:System.Xml.XmlReader>|最低|最も小さい (その結果、データの取得は最も高速)|はい|[XmlReader を使用してデータを取得します。](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-xmlreader.md)|  
  
## <a name="see-also"></a>参照  
 [ADOMD.NET クライアント プログラミング](../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)  
  
  
