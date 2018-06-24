---
title: 分析データ ソースからデータを取得する |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data retrieval [ADOMD.NET]
- retrieving data
- ADOMD.NET, data retrieval
- data retrieval [ADOMD.NET], about retrieving data
ms.assetid: 88358189-28aa-4bc7-8dda-5a92e3a012b8
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6e6243a815b399c91a2cd7aaa9eca712c6c569bf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070583"
---
# <a name="retrieving-data-from-an-analytical-data-source"></a>分析データ ソースからのデータの取得
  接続を確立し、クエリを作成すると、任意のデータを取得できます。 ADOMD.NET では、<xref:Microsoft.AnalysisServices.AdomdClient.CellSet> オブジェクトのいずれかの `Execute` メソッドを呼び出すことにより、3 種類のオブジェクト (<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>、<xref:System.Xml.XmlReader>、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>) を使用してデータを取得できます。  
  
 これら 3 つのオブジェクトは、対話性とオーバーヘッドがそれぞれ異なります。  
  
-   *対話機能*使いやすさと、オブジェクト モデルを通じて利用可能な情報の量を表します。  
  
-   *オーバーヘッド*オブジェクト モデルとオブジェクト モデルがデータを取得する速度のために必要なメモリの量、サーバーへのネットワーク接続経由でオブジェクト モデルを生成するトラフィックの量を指します。  
  
 次の表は、各オブジェクトの対話性とオーバーヘッドを示しています。それぞれの違いを確認したうえで、アプリケーションに最適なデータ取得オブジェクトを選択してください。  
  
|オブジェクト|対話性|オーバーヘッド|次元の保持|使用方法に関する情報|  
|------------|-------------------|--------------|----------------------------|-----------------------|  
|<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>|最も高い|やや大きい (結果として、データの取得は最も低速)|はい|[セルセットを使用したデータの取得](retrieving-data-using-the-cellset.md)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter>|中程度|中程度|いいえ|[DataAdapter からの DataSet の読み込み](http://go.microsoft.com/fwlink/?LinkId=70016)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>|中程度|中程度|いいえ|[AdomdDataReader を使用したデータの取得](retrieving-data-using-the-adomddatareader.md)|  
|<xref:System.Xml.XmlReader>|最低|最も小さい (その結果、データの取得は最も高速)|はい|[XmlReader を使用したデータの取得](retrieving-data-using-the-xmlreader.md)|  
  
## <a name="see-also"></a>参照  
 [ADOMD.NET クライアント プログラミング](adomd-net-client-programming.md)  
  
  