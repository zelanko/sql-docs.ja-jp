---
title: XmlReader を使用してデータを取得する |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: adomd
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 43ce3cda885ec3583fb69d565b5dae875b492db6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="retrieving-data-using-the-xmlreader"></a>XmlReader を使用したデータの取得
  **XmlReader**クラスの一部、 **System.Xml** Microsoft .NET Framework クラス ライブラリの名前空間がに似ていますが、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>を内のクラス、 **XmlReader**クラスもにより高速かつ非キャッシュ、前方参照専用データにアクセスします。 メモリ内分析のビューを使用して、データの必要性が存在しない場合、<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>オブジェクト、 **XmlReader**オブジェクトでは、特に大量のデータ用の XML データを取得するために最適です。 **XmlReader** 、データをストリーム**XmlReader**を取得し、場合と同様に、呼び出し元にデータを公開する前にすべてのデータをキャッシュする必要はありません、<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>オブジェクトは、変換に使用された、XML for Analysis 応答を分析オブジェクト モデル表現です。  
  
 **XmlReader**クラスに直接アクセス、XML for Analysis 応答 ADOMD.NET が受信したときに、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A>のメソッド、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>オブジェクトが呼び出されるとします。 取得するデータは未加工の XML なので、データとメタデータを手動で解析する必要があります。 データの取得が完了するとすぐに、 **XmlReader**オブジェクトを閉じる必要があります。  
  
## <a name="retrieving-data-and-metadata"></a>データとメタデータの取得  
 使用する、 **XmlReader**クラスのデータを取得する、次の手順を実行します。  
  
1.  **オブジェクトの新しいインスタンスを作成します。**  
  
     新しいインスタンスを作成する、 **XmlReader**クラスを呼び出す、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A>または<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A>のメソッド、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>オブジェクト。  
  
2.  **データを取得します。**  
  
     コマンドは、クエリを実行し、返します後、 **XmlReader**、データおよびメタデータを解析する必要があります。 XML データおよびメタデータは、XML for Analysis プロバイダーで使用されるネイティブ形式で表されます。 ほとんどの XML for Analysis プロバイダーでは、ネイティブ形式は、 **MDDataSet**形式です。 **MDDataSet**形式が適切に構成された形式でのセル セットのデータとメタデータの両方を提供します。 詳細については、 **MDDataSet**書式を設定し、XML for Analysis 仕様を参照してください。  
  
3.  **リーダーを閉じます。**  
  
     常に呼び出す必要があります、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Close%2A>メソッドを使用してが完了したら、 **XmlReader**オブジェクト。 中に、 **XmlReader**を開いて、 **XmlReader**が排他的に使用、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>コマンドを実行するために使用されたオブジェクト。 使用しているすべてのコマンドを実行することはできません<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>、別の作成を含む**XmlReader**または<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>元を終了するまで、 **XmlReader**です。  
  
### <a name="example-of-retrieving-data-from-the-xmlreader"></a>XmlReader からのデータ取得例  
 次の例は、コマンドを実行し、としてデータを取得、 **XmlReader**コンソールにファイルの内容を出力します。  
  
 [!code-cs[Adomd.NetClient#OutputDataWithXML](../../analysis-services/multidimensional-models-adomd-net-client/codesnippet/csharp/retrieving-data-using-th_1_1.cs)]  
  
## <a name="see-also"></a>参照  
 [分析データ ソースからデータを取得します。](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-from-an-analytical-data-source.md)   
 [セルセットを使用してデータを取得します。](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-cellset.md)   
 [AdomdDataReader を使用したデータの取得](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-adomddatareader.md)  
  
  
