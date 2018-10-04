---
title: 分析データ ソースからデータの取得 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- data retrieval [ADOMD.NET]
- retrieving data
- ADOMD.NET, data retrieval
- data retrieval [ADOMD.NET], about retrieving data
ms.assetid: 88358189-28aa-4bc7-8dda-5a92e3a012b8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0cfc0c783e8c61689d8f5b0ca3bab6ded39a57a4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48212382"
---
# <a name="retrieving-data-from-an-analytical-data-source"></a>分析データ ソースからのデータの取得
  接続を確立し、クエリを作成すると、任意のデータを取得できます。 ADOMD.NET では、<xref:Microsoft.AnalysisServices.AdomdClient.CellSet> オブジェクトのいずれかの `Execute` メソッドを呼び出すことにより、3 種類のオブジェクト (<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>、<xref:System.Xml.XmlReader>、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>) を使用してデータを取得できます。  
  
 これら 3 つのオブジェクトは、対話性とオーバーヘッドがそれぞれ異なります。  
  
-   *対話機能*使いやすさと、オブジェクト モデルを通じて入手できる情報量を表します。  
  
-   *オーバーヘッド*オブジェクト モデルは、オブジェクト モデルとオブジェクト モデルがデータを取得する速度のために必要なメモリの量、サーバーへのネットワーク接続経由で生成されるトラフィックの量を参照します。  
  
 次の表は、各オブジェクトの対話性とオーバーヘッドを示しています。それぞれの違いを確認したうえで、アプリケーションに最適なデータ取得オブジェクトを選択してください。  
  
|オブジェクト|対話性|オーバーヘッド|次元の保持|使用方法に関する情報|  
|------------|-------------------|--------------|----------------------------|-----------------------|  
|<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>|最も高い|やや大きい (結果として、データの取得は最も低速)|はい|[セルセットを使用したデータの取得](retrieving-data-using-the-cellset.md)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter>|中程度|中程度|いいえ|[DataAdapter からの dataset](http://go.microsoft.com/fwlink/?LinkId=70016)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>|中程度|中程度|いいえ|[AdomdDataReader を使用したデータの取得](retrieving-data-using-the-adomddatareader.md)|  
|<xref:System.Xml.XmlReader>|最小|最も小さい (その結果、データの取得は最も高速)|はい|[XmlReader を使用したデータの取得](retrieving-data-using-the-xmlreader.md)|  
  
## <a name="see-also"></a>参照  
 [ADOMD.NET クライアント プログラミング](adomd-net-client-programming.md)  
  
  
