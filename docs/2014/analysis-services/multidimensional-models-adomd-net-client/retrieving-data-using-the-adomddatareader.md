---
title: AdomdDataReader を使用してデータを取得する |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
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
- AdomdDataReader object
- data retrieval [ADOMD.NET], AdomdDataReader object
ms.assetid: 8ed7ea26-b5f8-4852-80fc-75dd62df5b3a
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 17ed47d13aab29ea47c5f1d041705029844e359e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072466"
---
# <a name="retrieving-data-using-the-adomddatareader"></a>AdomdDataReader を使用したデータの取得
  <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> オブジェクトは、オーバーヘッドと対話性のバランスがとれた分析データ取得方法です。 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> オブジェクトは、分析データ ソースから、読み取り専用かつ順方向専用のフラットなデータ ストリームを取得します。 このようにデータ ストリームがバッファリングされないことで、手順ロジックにより、分析データソースから取得した結果を順次効率的に処理することができます。 大量のデータを取得して表示する場合は、データがメモリ キャッシュに格納されない <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> が適しています。  
  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> では、返されるクエリの完全な結果を待たずに、使用可能になったデータをすぐに取得できるので、アプリケーションのパフォーマンスも向上します。 また、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> は、既定では一度に 1 つの行のみをメモリに格納するため、システムのオーバーヘッドが軽減されます。  
  
 パフォーマンスが最適化される代わりに、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> オブジェクトの場合、取得したデータに関する情報は他のデータ取得方法より少なくなります。 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> オブジェクトは、データやメタデータを表す大規模オブジェクト モデルをサポートしていません。また、セルの書き戻しなど、複雑な分析機能も実行できません。 その代わり、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> オブジェクトには、セルセットのデータを取得するための厳密に型指定されたメソッド セットと、セルセットのメタデータを表形式で取得するためのメソッドが用意されています。 さらに、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>を実装する、 **IDbDataReader**データ バインディングをサポートするインターフェイスを使用してデータを取得するため、`SelectCommand`メソッドから、 **System.Data**の名前空間、Microsoft .NET Framework クラス ライブラリです。  
  
## <a name="retrieving-data-from-the-adomddatareader"></a>AdomdDataReader からのデータの取得  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> オブジェクトを使用してデータを取得するには、次の手順を実行します。  
  
1.  **オブジェクトの新しいインスタンスを作成します。**  
  
     <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> クラスの新しいインスタンスを作成するには、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> オブジェクトの <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteReader%2A> メソッドまたは <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> メソッドを呼び出します。  
  
2.  **データを取得します。**  
  
     コマンドでクエリを実行すると、ADOMD.NET は `Resultset` 形式 (XML for Analysis 仕様に記述されている表形式) で結果を返して、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> オブジェクトのデータをフラット化します。 このようなデータで、さまざまな次元を考慮して分析データをクエリする場合、表形式は一般的ではありません。  
  
     ADOMD.NET は、これらの表形式の結果を、次のメソッドのいずれかを使用して要求されるまでクライアントのネットワーク バッファーに格納します。  
  
    -   <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.Read%2A> オブジェクトの <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> メソッドを呼び出します。  
  
         <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.Read%2A> メソッドは、クエリ結果から行を取得します。 その後、列の名前または順序付き参照を <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.Item%2A> プロパティに渡して、返される行の各列にアクセスできます。 たとえば、現在の行の最初の列の名前は ColumnName になります。 次に、`reader[0].ToString()` または `reader["ColumnName"].ToString()` は、現在の行の最初の列のコンテンツを返します。  
  
    -   型指定されたアクセサー メソッドのいずれかを呼び出します。  
  
         <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> は、一連の型指定されたアクセサー メソッドを提供します。このメソッドを使用すると、ネイティブ データ型の列値にアクセスできます。 列値の基になるデータ型がわかっている場合は、型指定されたアクセサー メソッドを使用することで列値の取得時に必要な型変換が削減され、その結果、最良のパフォーマンスを実現できます。  
  
         使用可能な型指定されたアクセサー メソッドには、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetDateTime%2A>、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetDouble%2A>、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetInt32%2A> などがあります。 型指定されたアクセサー メソッドの一覧については、「<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>」を参照してください。  
  
3.  **リーダーを閉じます。**  
  
     <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.Close%2A> オブジェクトの使用が終了したら、常に <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> メソッドを呼び出す必要があります。 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> オブジェクトのインスタンスを開いている間は、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> は <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> によって排他的に使用されています。 元の <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> を閉じるまで、別の <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> または `System.Xml.XmlReader` の作成など、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> のインスタンスではどのコマンドも実行できません。  
  
### <a name="example-of-retrieving-data-from-the-adomddatareader"></a>AdomdDataReader からのデータ取得の例  
 次のコード例は、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> オブジェクトを反復処理し、最初の 2 つの値を文字列として各列から返します。  
  
```vb  
If Reader.HasRows Then  
    Do While objReader.Read()  
        Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _  
            objReader.GetString(0), objReader.GetString(1))  
    Loop  
Else  
  Console.WriteLine("No rows returned.")  
End If  
  
objReader.Close()  
```  
  
```csharp  
if (objReader.HasRows)  
  while (objReader.Read())  
    Console.WriteLine("\t{0}\t{1}", _  
        objReader.GetString(0), objReader.GetString(1));  
else  
  Console.WriteLine("No rows returned.");  
  
objReader.Close();  
```  
  
## <a name="retrieving-metadata-from-the-adomddatareader"></a>AdomdDataReader からのメタデータの取得  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> オブジェクトのインスタンスが開いている場合、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetSchemaTable%2A> メソッドを使用して現在のレコードセットに関するスキーマ情報 (メタデータ) を取得できます。 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetSchemaTable%2A>返します、`DataTable`オブジェクトを現在のレコード セットのスキーマ情報が格納されます。 `DataTable` は、レコードセットの各列に対して 1 つの行を含みます。 スキーマ テーブル行の各列は、セルセットに返される列のプロパティにマップされます。ここで、`ColumnName` はプロパティの名前で、列の値はプロパティの値です。  
  
### <a name="example-of-retrieving-metadata-from-the-adomddatareader"></a>AdomdDataReader からのメタデータ取得の例  
 次のコード例では、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> オブジェクトのスキーマ情報を書き出しています。  
  
```vb  
Dim schemaTable As DataTable = objReader.GetSchemaTable()  
  
Dim objRow As DataRow  
Dim objColumn As DataColumn  
  
For Each objRow In schemaTable.Rows  
  For Each objColumn In schemaTable.Columns  
    Console.WriteLine(objColumn.ColumnName & " = " & objRow(objColumn).ToString())  
  Next  
  Console.WriteLine()  
Next  
DataTable schemaTable = objReader.GetSchemaTable();  
```  
  
```csharp  
foreach (DataRow objRow in schemaTable.Rows)  
{  
  foreach (DataColumn objColumn in schemaTable.Columns)  
    Console.WriteLine(objColumn.ColumnName + " = " + objRow[objColumn]);  
  Console.WriteLine();  
}  
```  
  
## <a name="retrieving-multiple-result-sets"></a>複数の結果セットの取得  
 データ マイニングは入れ子になったテーブルの概念をサポートします。入れ子になったテーブルは、ADOMD.NET では入れ子になった行セットとして示されます。 各行に関連付けられた入れ子になった行セットを取得するには、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetDataReader%2A> メソッドを呼び出します。  
  
## <a name="see-also"></a>参照  
 [分析データ ソースからデータを取得します。](retrieving-data-from-an-analytical-data-source.md)   
 [セルセットを使用してデータを取得します。](retrieving-data-using-the-cellset.md)   
 [XmlReader を使用したデータの取得](retrieving-data-using-the-xmlreader.md)  
  
  