---
title: 空間データ型の使用 | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f133fa066ef2c486cf7bb40c5b653c99e077bc46
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "69026942"
---
# <a name="using-spatial-datatypes"></a>空間データ型の使用

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

空間データ型 (Geometry および Geography) は、JDBC Driver プレビュー リリース 6.5.0 以降でサポートされています。 空間データ型は、ストアド プロシージャ、テーブル値パラメーター (TVP)、BulkCopy、および Always Encrypted では、現在サポートされていません。 このページでは、JDBC Driver を使用した Geometry データ型と Geography データ型のさまざまなユース ケースを示します。 空間データ型の概要については、「[空間データ型の概要](https://docs.microsoft.com/sql/relational-databases/spatial/spatial-data-types-overview)」ページをご覧ください。

## <a name="creating-a-geometry--geography-object"></a>Geometry オブジェクトと Geography オブジェクトの作成

Geometry / Geography オブジェクトを作成する主な方法は 2 つあります - Well-Known Text (WKT) または、Well-Known Binary (WKB) のいずれかから変換します。

### <a name="creating-from-wkt"></a>WKT から作成

```java
String geoWKT = "LINESTRING(1 0, 0 1, -1 0)";
Geometry geomWKT = Geometry.STGeomFromText(geoWKT, 0);
Geography geogWKT = Geography.STGeomFromText(geoWKT, 4326);
```

これにより、SRID (空間参照システム識別子) 0 を持つ LINESTRING Geometry オブジェクトと、SRID 4326 を持つ Geography オブジェクトが作成されます。

### <a name="creating-from-wkb"></a>WKB から作成

```java
byte[] geomWKB = Hex.decodeHex("00000000010403000000000000000000F03F00000000000000000000000000000000000000000000F03F000000000000F0BF000000000000000001000000010000000001000000FFFFFFFF0000000002".toCharArray());
byte[] geogWKB = Hex.decodeHex("E61000000104030000000000000000000000000000000000F03F000000000000F03F00000000000000000000000000000000000000000000F0BF01000000010000000001000000FFFFFFFF0000000002".toCharArray());

Geometry geomWKT = Geometry.deserialize(geomWKB);
Geography geogWKT = Geography.deserialize(geogWKB);
```

これにより、前に WKT から作成されたものと同等の Geometry オブジェクトと Geography オブジェクトが作成されます。

## <a name="working-with-a-geometry--geography-object"></a>Geometry オブジェクトまたは Geography オブジェクトの使用

ユーザーは SQL Server に次のようなテーブルを持つと仮定します。

```sql
CREATE TABLE sampleTable (c1 geometry)  
```

Geometry 値を挿入するサンプル スクリプトは次のようになります。

```java
String geoWKT = "LINESTRING(1 0, 0 1, -1 0)";
Geometry geomWKT = Geometry.STGeomFromText(geoWKT, 0);
SQLServerPreparedStatement pstmt = (SQLServerPreparedStatement) connection.prepareStatement("insert into sampleTable values (?)");
pstmt.setGeometry(1, geomWKT);  
pstmt.execute();
```

Geography 列と **setGeography()** メソッドを使用して、対応する Geography にも同じことができます。

Geometry 列または Geography 列を読み取るには、次のようにします。

```java
try(SQLServerResultSet rs = (SQLServerResultSet)stmt.executeQuery("select * from geomTable")) {
    while(rs.next()){
        rs.getGeometry(1);
    }
}
```

Geography 列と **getGeography()** メソッドを使用して、対応する Geography にも同じことができます。

## <a name="newly-introduced-apis"></a>新しく導入された API

これらは、この追加により、**SQLServerPreparedStatement**、**SQLServerResultSet**、**Geometry**、および **Geography** の各クラスに導入された新しいパブリック API です。

### <a name="sqlserverpreparedstatement"></a>SQLServerPreparedStatement

|Method|説明|
|:------|:----------|
|void setGeometry(int n, Geometry x)| 指定されたパラメーターを、所定の microsoft.sql.Geometry クラス オブジェクトに設定します。
|void setGeography(int n, Geography x)| 指定されたパラメーターを、所定の microsoft.sql.Geography クラス オブジェクトに設定します。

### <a name="sqlserverresultset"></a>SQLServerResultSet

|Method|説明|
|:------|:----------|
|Geometry getGeometry(int colunIndex)| この ResultSet オブジェクトの現在の行にある指定された列の値を、Java プログラミング言語の com.microsoft.sqlserver.jdbc.Geometry オブジェクトとして返します。
|Geometry getGeometry(String columnName)| この ResultSet オブジェクトの現在の行にある指定された列の値を、Java プログラミング言語の com.microsoft.sqlserver.jdbc.Geometry オブジェクトとして返します。
|Geography getGeography(int colunIndex)| この ResultSet オブジェクトの現在の行にある指定された列の値を、Java プログラミング言語の com.microsoft.sqlserver.jdbc.Geography オブジェクトとして返します。
|Geography getGeography(String columnName)| この ResultSet オブジェクトの現在の行にある指定された列の値を、Java プログラミング言語の com.microsoft.sqlserver.jdbc.Geography オブジェクトとして返します。

### <a name="geometry"></a>ジオメトリ

|Method|説明|
|:------|:----------|
|Geometry STGeomFromText(String wkt, int SRID)| インスタンスに格納されている Z (標高) 値と M (メジャー) 値で補完された、Open Geospatial Consortium (OGC) の Well-Known Text (WKT) 表現からの Geometry インスタンス用のコンストラクター。
|Geometry STGeomFromWKB(byte[] wkb)| Open Geospatial Consortium (OGC) の Well-Known Binary (WKB) 表現からの Geometry インスタンス用のコンストラクター。
|Geometries deserialize(byte[] wkb)| 空間データの内部 SQL Server 形式からの Geometry インスタンス用のコンストラクター。
|Geometry parse(String wkt)| Open Geospatial Consortium (OGC) の Well-Known Text (WKT) 表現からの Geometry インスタンス用のコンストラクター。 空間参照識別子は既定値の 0 になります。
|Geometry point(double x, double y, int SRID)| X 値と Y 値および SRID から Point インスタンスを表す Geometry インスタンス用のコンストラクター。
|String STAsText()| Geometry インスタンスにおける Open Geospatial Consortium (OGC) の Well-Known Text (WKT) 表現を返します。 このテキストは、インスタンスに格納されている Z (標高) 値または M (メジャー) 値を含みません。
|byte[] STAsBinary()| Geometry インスタンスにおける Open Geospatial Consortium (OGC) の Well-Known Binary (WKB) 表現を返します。 この値には、インスタンスに格納されている Z 値または M 値が含まれません。
|byte[] serialize()| Geometry 型の内部 SQL Server 形式を表すバイトを返します。
|boolean hasM()| オブジェクトに M (メジャー) 値が含まれているかどうかを返します。
|boolean hasZ()| オブジェクトに Z (標高) 値が含まれているかどうかを返します。
|Double getX()| X 座標値を返します。
|Double getY()| Y 座標値を返します。
|Double getM()| オブジェクトの M (メジャー) 値を返します。
|Double getZ()| オブジェクトの Z (標高) 値を返します。
|int getSrid()| SRID (空間参照識別子) 値を返します。
|boolean isNull()| Geometry オブジェクトが null かどうかを返します。
|int STNumPoints()| Geometry オブジェクト内のポイントの数を返します。
|String STGeometryType()| geometry インスタンスで表される Open Geospatial Consortium (OGC) の型名を返します。
|String asTextZM()| Geometry オブジェクトの Well-known Text (WKT) 表現を返します。
|String toString()| Geometry オブジェクトの文字列表現を返します。

### <a name="geography"></a>[地理的な場所]

|Method|説明|
|:------|:----------|
|Geography STGeomFromText(String wkt, int SRID)| インスタンスに格納されている Z (標高) 値と M (メジャー) 値で補完された、Open Geospatial Consortium (OGC) の Well-Known Text (WKT) 表現からの Geography インスタンス用のコンストラクター。
|Geography STGeomFromWKB(byte[] wkb)| Open Geospatial Consortium (OGC) の Well-Known Binary (WKB) 表現からの Geography インスタンス用のコンストラクター。
|Geography deserialize(byte[] wkb)| 空間データの内部 SQL Server 形式からの Geography インスタンス用のコンストラクター。
|Geography parse(String wkt)| Open Geospatial Consortium (OGC) の Well-Known Text (WKT) 表現からの Geography インスタンス用のコンストラクター。 空間参照識別子は既定値の 0 になります。
|Geography point(double lon, double lat, int SRID)| Point インスタンスを経度、緯度、空間参照識別子 (SRID) で表す Geography インスタンス用のコンストラクター。
|String STAsText()| Geography インスタンスにおける Open Geospatial Consortium (OGC) の Well-Known Text (WKT) 表現を返します。 このテキストは、インスタンスに格納されている Z (標高) 値または M (メジャー) 値を含みません。
|byte[] STAsBinary())| Geography インスタンスにおける Open Geospatial Consortium (OGC) の Well-Known Binary (WKB) 表現を返します。 この値には、インスタンスに格納されている Z 値または M 値が含まれません。
|byte[] serialize()| Geography 型の内部 SQL Server 形式を表すバイトを返します。
|boolean hasM()| オブジェクトに M (メジャー) 値が含まれているかどうかを返します。
|boolean hasZ()| オブジェクトに Z (標高) 値が含まれているかどうかを返します。
|Double getLatitude()| 緯度の値を返します。
|Double getLongitude()| 経度の値を返します。
|Double getM()| オブジェクトの M (メジャー) 値を返します。
|Double getZ()| オブジェクトの Z (標高) 値を返します。
|int getSrid()| SRID (空間参照識別子) 値を返します。
|boolean isNull()| Geography オブジェクトが null かどうかを返します。
|int STNumPoints()| Geography オブジェクト内のポイントの数を返します。
|String STGeographyType()| geography インスタンスで表される Open Geospatial Consortium (OGC) の型名を返します。
|String asTextZM()| Geography オブジェクトの Well-known Text (WKT) 表現を返します。
|String toString()| Geography オブジェクトの文字列表現を返します。

## <a name="limitations-of-spatial-datatypes"></a>空間データ型の制限

1. 空間サブデータ型の **CircularString**、**CompoundCurve**、**CurvePolygon**、および **FullGlobe** は、SQL Server 2012 以降でのみサポートされています。

2. Always Encrypted を空間データ型で使用することはできません。

3. ストアド プロシージャ、TVP、および BulkCopy 操作は、現在、空間データ型ではサポートされていません。

## <a name="see-also"></a>参照

[空間データ型のサンプル (JDBC)](../../connect/jdbc/spatial-data-types-sample.md)
