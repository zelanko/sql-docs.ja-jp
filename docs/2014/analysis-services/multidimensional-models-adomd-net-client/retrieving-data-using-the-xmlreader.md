---
title: XmlReader を使用してデータを取得する |Microsoft ドキュメント
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
- retrieving data
- XmlReader object
- data retrieval [ADOMD.NET], XmlReader object
ms.assetid: 420ec40e-be2d-413a-b4b2-6d2b1756e270
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 257777c40c829921680b8fce333bd6e44f6f57fd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075847"
---
# <a name="retrieving-data-using-the-xmlreader"></a>XmlReader を使用したデータの取得
  `XmlReader`クラスの一部、 `System.Xml` Microsoft .NET Framework クラス ライブラリの名前空間がに似ていますが、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>を内のクラス、`XmlReader`クラスもにより高速かつ非キャッシュ、前方参照専用データにアクセスします。 <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> オブジェクトを使用したデータのインメモリ分析ビューが不要であれば、`XmlReader` オブジェクトは、大量の XML データを取得するのに最も適しています。 `XmlReader` 、データをストリーム`XmlReader`を取得し、場合と同様に、呼び出し元にデータを公開する前にすべてのデータをキャッシュする必要はありません、<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>オブジェクトは、分析オブジェクトに XML for Analysis 応答を変換に使用されました。モデルの表現。  
  
 `XmlReader` クラスは、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A> オブジェクトの <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> メソッドが呼び出されると、ADOMD.NET が受信した XML for Analysis 応答への直接アクセスを提供します。 取得するデータは未加工の XML なので、データとメタデータを手動で解析する必要があります。 データの取得が完了したら、すぐに `XmlReader` オブジェクトを閉じてください。  
  
## <a name="retrieving-data-and-metadata"></a>データとメタデータの取得  
 `XmlReader` クラスを使用してデータを取得するには、次の手順に従います。  
  
1.  **オブジェクトの新しいインスタンスを作成します。**  
  
     `XmlReader` クラスの新しいインスタンスを作成するには、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> オブジェクトの <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A> メソッドまたは <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> メソッドを呼び出します。  
  
2.  **データを取得します。**  
  
     コマンドによってクエリが実行され、`XmlReader` が返された後、データとメタデータを自分で解析する必要があります。 XML データおよびメタデータは、XML for Analysis プロバイダーで使用されるネイティブ形式で表されます。 通常、XML for Analysis プロバイダーのネイティブ形式は `MDDataSet` 形式です。 `MDDataSet` 形式によって、セルセットのデータおよびメタデータの両方が、適切に構成された形式で提供されます。 `MDDataSet` 形式の詳細については、XML for Analysis の仕様書を参照してください。  
  
3.  **リーダーを閉じます。**  
  
     <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Close%2A> オブジェクトの使用が終了したら、常に `XmlReader` メソッドを呼び出す必要があります。 `XmlReader` が開いている間は、その `XmlReader` によって、コマンドの実行時に使用した <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトが排他的に使用されます。 現在開いている `XmlReader` を閉じない限り、新しい `XmlReader` や <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> を作成するなど、その <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> を使用するコマンドは一切実行できません。  
  
### <a name="example-of-retrieving-data-from-the-xmlreader"></a>XmlReader からのデータ取得例  
 次の例では、コマンドを実行してデータを `XmlReader` として取得し、ファイルの内容をコンソールに出力します。  
  
 [!code-csharp[Adomd.NetClient#OutputDataWithXML](../../snippets/csharp/SQL14/adomd.net/adomd.netclient/cs/adomdexample.cs#outputdatawithxml)]  
  
## <a name="see-also"></a>参照  
 [分析データ ソースからデータを取得します。](retrieving-data-from-an-analytical-data-source.md)   
 [セルセットを使用してデータを取得します。](retrieving-data-using-the-cellset.md)   
 [AdomdDataReader を使用したデータの取得](retrieving-data-using-the-adomddatareader.md)  
  
  