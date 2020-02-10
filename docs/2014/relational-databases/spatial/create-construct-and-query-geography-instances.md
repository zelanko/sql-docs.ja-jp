---
title: geography インスタンスの作成、構築、およびクエリ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geography data type [SQL Server]
- geodetic data type [SQL Server]
- geography data type [SQL Server], about geography data type
ms.assetid: b585851e-d15b-411f-adeb-aeabeb777c0b
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 5dde7575a3f657b89d29fefa0da52002bcd6af28
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66014294"
---
# <a name="create-construct-and-query-geography-instances"></a>geography インスタンスの作成、構築、およびクエリ
  地理空間データ型の `geography` は、球体地球座標系のデータを表します。 この型は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では .NET 共通言語ランタイム (CLR) のデータ型として実装されています。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `geography` データ型は、GPS の緯度経度座標などの楕円体 (球体地球) データを格納します。  
  
 
  `geography` 型は、各データベースで使用できるように事前に定義されています。 
  `geography` 型のテーブル列を作成し、システムが提供する他のデータ型を使用するときと同じように `geography` データを操作できます。  
  
##  <a name="creating"></a>新しい geography インスタンスの作成または構築  
  
###  <a name="existing"></a>既存のインスタンスからの新しい geography インスタンスの作成  
 
  `geography` データ型には、既存のインスタンスに基づいて新しい `geography` インスタンスを作成するために使用できる組み込みメソッドが数多く用意されています。  
  
 **Geography の周りにバッファーを作成するには**  
 [STBuffer &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stbuffer-geography-data-type)  
  
 **Geography の周りにバッファーを作成し、許容範囲を実現するには**  
 [BufferWithTolerance &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/bufferwithtolerance-geography-data-type)  
  
 **2つの geography インスタンスの積集合から geography を作成するには**  
 [STIntersection &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stintersection-geography-data-type)  
  
 **2つの geography インスタンスの和集合から geography を作成するには**  
 [STUnion &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stunion-geography-data-type)  
  
 **ある geography が別の geography と重複しない点から geography を作成するには**  
 [STDifference &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stdifference-geography-data-type)  
  
###  <a name="wkt"></a>Well-known Text 入力からの geography インスタンスの構築  
 
  `geography` データ型には、Open Geospatial Consortium (OGC) WKT 表現から geography を生成する組み込みのメソッドが数多く用意されています。 WKT 標準は geography データをテキスト形式で交換できるテキスト文字列です。  
  
 **WKT 入力から任意の型の geography インスタンスを構築するには**  
 [STGeomFromText &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stgeomfromtext-geography-data-type)  
  
 [&#40;geography データ型&#41;を解析します。](/sql/t-sql/spatial-geography/parse-geography-data-type)  
  
 **WKT 入力から geography Point インスタンスを構築するには**  
 [STPointFromText &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stpointfromtext-geography-data-type)  
  
 **WKT 入力から geography MultiPoint インスタンスを構築するには**  
 [STMPointFromText &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stmpointfromtext-geography-data-type)  
  
 **WKT 入力から geography LineString インスタンスを構築するには**  
 STLineFromText (geography データ型)  
  
 **WKT 入力から geography MultiLineString インスタンスを構築するには**  
 [STMLineFromText &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stmlinefromtext-geography-data-type)  
  
 **WKT 入力から geography Polygon インスタンスを構築するには**  
 [STPolyFromText &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stpolyfromtext-geography-data-type)  
  
 **WKT 入力から geography MultiPolygon インスタンスを構築するには**  
 [STMPolyFromText &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stmpolyfromtext-geography-data-type)  
  
 **WKT 入力から geography GeometryCollection インスタンスを構築するには**  
 [STGeomCollFromText &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stgeomcollfromtext-geography-data-type)  
  
###  <a name="wkb"></a>Well-known Binary 入力からの geography インスタンスの構築  
 WKB は、`Geography` データをアプリケーションと SQL データベース間で交換することができる、OGC で指定されたバイナリ形式です。 次の関数は、WKB 入力を受け入れて geography インスタンスを構築します。  
  
 **WKB 入力から任意の型の geography インスタンスを構築するには**  
 [STGeomFromWKB &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stgeomfromwkb-geography-data-type)  
  
 **WKB 入力から geography Point インスタンスを構築するには**  
 [STPointFromWKB &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stpointfromwkb-geography-data-type)  
  
 **WKB 入力から geography MultiPoint インスタンスを構築するには**  
 [STMPointFromWKB &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stmpointfromwkb-geography-data-type)  
  
 **WKB 入力から geography LineString インスタンスを構築するには**  
 [STLineFromWKB &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stlinefromwkb-geography-data-type)  
  
 **WKB 入力から geography MultiLineString インスタンスを構築するには**  
 [STMLineFromWKB &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stmlinefromwkb-geography-data-type)  
  
 **WKB 入力から geography Polygon インスタンスを構築するには**  
 [STPolyFromWKB &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stpolyfromwkb-geography-data-type)  
  
 **WKB 入力から geography MultiPolygon インスタンスを構築するには**  
 [STMPolyFromWKB &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stmpolyfromwkb-geography-data-type)  
  
 **WKB 入力から geography GeometryCollection インスタンスを構築するには**  
 [Stgeom/Fromwkb &#40;Geography データ型&#41;](/sql/t-sql/spatial-geography/stgeomcollfromwkb-geography-data-type)Stgeom/Fromwkb (geography データ型)  
  
###  <a name="gml"></a>GML テキスト入力からの geography インスタンスの構築  
 データ`geography`型には、GML ( `geography` `geography`インスタンスの XML 表現) からインスタンスを生成するメソッドが用意されています。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、GML のサブセットをサポートします。  
  
 Geography Markup Language の詳細については、OGC の仕様の「 [OGC の仕様、Geography Markup Language](https://go.microsoft.com/fwlink/?LinkId=93629)」を参照してください。  
  
 **GML 入力から任意の型の geography インスタンスを構築するには**  
 [Geomfro、Ml &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/geomfromgml-geography-data-type)  
  
##  <a name="returning"></a>Geography インスタンスからの well-known Text および well-known Binary の取得  
 次のメソッドを使用して、`geography` インスタンスの WKT 形式または WKB 形式のいずれかを取得できます。  
  
 **Geography インスタンスの WKT 表現を取得するには**  
 [STAsText &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stastext-geography-data-type)  
  
 [ToString &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/tostring-geography-data-type)  
  
 **Z 値と M 値を含む geography インスタンスの WKT 表現を取得するには**  
 [AsTextZM &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/astextzm-geography-data-type)  
  
 **Geography インスタンスの WKB 表現を取得するには**  
 [STAsBinary &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stasbinary-geography-data-type)  
  
 **Geography インスタンスの GML 表現を取得するには**  
 [AsGml &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/asgml-geography-data-type)  
  
##  <a name="query"></a>Geography インスタンスのプロパティと動作のクエリ  
 すべて`geography`のインスタンスには、が提供する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メソッドを使用して取得できるいくつかのプロパティがあります。 以下のトピックでは、geography 型のプロパティおよび動作と、geography 型に対するクエリを実行するためのメソッドについて説明します。  
  
###  <a name="valid"></a>有効性、インスタンスの種類、および GeometryCollection 情報  
 `geography`インスタンスが構築された後、次のメソッドを使用してインスタンスの型を返すことができ`GeometryCollection`ます。インスタンスの場合`geography`は、特定のインスタンスを返します。  
  
 **Geography のインスタンスの型を取得するには**  
 [STGeometryType &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stgeometrytype-geography-data-type)  
  
 **Geography が特定のインスタンスの型であるかどうかを調べるには**  
 [InstanceOf &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/instanceof-geography-data-type)  
  
 **Geography インスタンスがそのインスタンスの型に対して適切な形式であるかどうかを確認するには**  
 [STNumGeometries &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stnumgeometries-geography-data-type)  
  
 **GeometryCollection インスタンス内の特定の geography を取得するには**  
 [STGeometryN &#40;Geography データ型&#41;](/sql/t-sql/spatial-geography/stgeometryn-geography-data-type)STGeometryN (geography データ型)  
  
###  <a name="number"></a>ポイント数  
 空`geography`でないすべてのインスタンスは、*ポイント*で構成されます。 これらの点は、`geography` インスタンスが描画される地球の緯度経度座標を表します。 
  `geography` データ型には、インスタンスの点に対するクエリを実行するための組み込みメソッドが数多く用意されています。  
  
 **インスタンスを構成する点の数を取得するには**  
 [STNumPoints &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stnumpoints-geography-data-type)  
  
 **インスタンス内の特定の点を取得するには**  
 [STPointN &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type)  
  
 **インスタンスの始点を取得するには**  
 [STStartPoint &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/ststartpoint-geography-data-type)  
  
 **インスタンスの終点を取得するには**  
 [STEndpoint &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stendpoint-geography-data-type)  
  
###  <a name="dimension"></a>多次元  
 空でない `geography` インスタンスの次元は、0 次元、1 次元、2 次元のいずれかになります。 0次元`geography`のインスタンス ( `Point`や`MultiPoint`など) には、長さや面積はありません。 1 次元のオブジェクト (`LineString, CircularString`、`CompoundCurve`、`MultiLineString` など) には長さがあります。 2 次元のインスタンス (`Polygon, CurvePolygon`、`MultiPolygon` など) には面積と長さがあります。 空のインスタンスの次元は -1 としてレポートされます。`GeometryCollection` ではその内容の最も大きな次元がレポートされます。  
  
 **インスタンスの次元を取得するには**  
 [STDimension &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stdimension-geography-data-type)  
  
 **インスタンスの長さを取得するには**  
 [STLength &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stlength-geography-data-type)  
  
 **インスタンスの面積を取得するには**  
 [STArea &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/starea-geography-data-type)  
  
###  <a name="empty"></a>指定  
 *空*`geography`のインスタンスには点はありません。 空の `LineString, CircularString`、`CompoundCurve`、および `MultiLineString` インスタンスの長さは 0 です。 空の `Polygon, CurvePolygon`、および `MultiPolygon` インスタンスの面積は 0 です。  
  
 **インスタンスが空かどうかを確認するには**  
 [STIsEmpty &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stisempty-geography-data-type)  
  
###  <a name="closure"></a>クローズ  
 *閉じ*`geography`たインスタンスは、始点と終点が同じである図形です。 
  `Polygon` インスタンスは閉じていると見なされます。 
  `Point` インスタンスは閉じていないと見なされます。  
  
 リングは、単純な閉じている `LineString` インスタンスです。  
  
 **インスタンスが閉じているかどうかを確認するには**  
 [STIsClosed &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stisclosed-geography-data-type)  
  
 **Polygon インスタンス内のリングの数を取得するには**  
 [NumRings &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/numrings-geography-data-type)  
  
 **Geography インスタンスの指定したリングを取得するには**  
 [RingN &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/ringn-geography-data-type)  
  
###  <a name="srid"></a>空間参照 ID (SRID)  
 SRID (spatial reference ID) は、`geography` インスタンスがどの楕円体座標系で表されているかを示す識別子です。 SRID が異なる 2 つの `geography` インスタンスを比較することはできません。  
  
 **インスタンスの SRID を設定または取得するには**  
 [STSrid &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stsrid-geography-data-type)  
  
 このプロパティは変更できます。  
  
##  <a name="rel"></a>Geography インスタンス間のリレーションシップの特定  
 
  `geography` データ型には、2 つの `geography` インスタンスの関係を調べるために使用できる組み込みメソッドが数多く用意されています。  
  
 **2つのインスタンスが同じポイントセットを構成しているかどうかを調べるには**  
 [STEquals &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stequals-geometry-data-type)  
  
 **2つのインスタンスが不整合かどうかを調べるには**  
 [STDisjoint &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stdisjoint-geometry-data-type)  
  
 **2つのインスタンスが交差するかどうかを調べるには**  
 [STIntersects geometry データ型&#41;](/sql/t-sql/spatial-geometry/stintersects-geometry-data-type)  
  
 **2つのインスタンスが交差する点を調べるには**  
 [STIntersection &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stintersection-geography-data-type)  
  
 **2つの geography インスタンスの点の間の最短距離を調べるには**  
 [STDistance &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stdistance-geometry-data-type)  
  
 **2つの geography インスタンス間の点の相違を調べるには**  
 [STDifference &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stdifference-geography-data-type)  
  
 **1つの geography インスタンスと別のインスタンスとの間で対称差 (一意の点) を派生させるには**  
 [STSymDifference &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stsymdifference-geography-data-type)  
  
##  <a name="supportedsrid"></a>geography インスタンスはサポートされている SRID を使用する必要があります  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] EPSG 標準に基づく SRID をサポートします。 地理空間データを使用して計算を実行したりメソッドを使用したりする際には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でサポートされている SRID を `geography` インスタンスで使用する必要があります  その SRID が、 **sys.spatial_reference_systems** カタログ ビューに表示される SRID のいずれかに一致する必要があります。 既に説明したように、`geography` データ型を使用して空間データの計算を実行する場合、計算結果は、データの作成に使用された楕円体によって異なります。これは、各楕円体に特定の SRID (spatial reference identifier) が割り当てられているからです。  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用される既定の SRID は 4326 です。SRID 4326 は、`geography` インスタンスのメソッドを使用する際に WGS 84 空間参照系にマップされます。 WGS 84 (SRID 4326) 以外の空間参照系のデータを使用する場合は、その地理空間データの SRID を確認する必要があります。  
  
##  <a name="examples"></a> 使用例  
 次の例は、geography 型のデータの追加方法とクエリ方法を示しています。  
  
-   最初の例では、ID 列と `geography` 型の `GeogCol1`列を含むテーブルを作成します。 3 番目の列で、 `geography` 型の列をその Open Geospatial Consortium (OGC) の Well-Known Text (WKT) 表現で示し、 `STAsText()` メソッドを使用します。 次に 2 つの行が挿入されます。1 つは、 `LineString` の `geography`インスタンスを含む行で、もう 1 つは `Polygon` インスタンスを含む行です。  
  
    ```  
    IF OBJECT_ID ( 'dbo.SpatialTable', 'U' ) IS NOT NULL   
        DROP TABLE dbo.SpatialTable;  
    GO  
  
    CREATE TABLE SpatialTable   
        ( id int IDENTITY (1,1),  
        GeogCol1 geography,   
        GeogCol2 AS GeogCol1.STAsText() );  
    GO  
  
    INSERT INTO SpatialTable (GeogCol1)  
    VALUES (geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326));  
  
    INSERT INTO SpatialTable (GeogCol1)  
    VALUES (geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326));  
    GO  
    ```  
  
-   2 番目の例では、 `STIntersection()` メソッドを使用して、前の例で挿入した 2 つの `geography` インスタンスが交差する点を返します。  
  
    ```  
    DECLARE @geog1 geography;  
    DECLARE @geog2 geography;  
    DECLARE @result geography;  
  
    SELECT @geog1 = GeogCol1 FROM SpatialTable WHERE id = 1;  
    SELECT @geog2 = GeogCol1 FROM SpatialTable WHERE id = 2;  
    SELECT @result = @geog1.STIntersection(@geog2);  
    SELECT @result.STAsText();  
    ```  
  
## <a name="see-also"></a>参照  
 [空間データ &#40;SQL Server&#41;](spatial-data-sql-server.md)  
  
  
