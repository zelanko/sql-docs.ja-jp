---
title: 空間データ型を使用して |Microsoft Docs
ms.custom: ''
ms.date: 07/30/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cc330f8d5dbc2a0f6c09adac0f61d4f603b4c02f
ms.sourcegitcommit: 2f9cafc1d7a3773a121bdb78a095018c8b7c149f
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39662304"
---
# <a name="using-spatial-datatypes"></a>空間データ型の使用

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

空間データ型 (Geometry と Geography) は、プレビュー リリースの JDBC Driver 6.5.0 を起動サポートします。 空間データ型は、現在はストアド プロシージャ、テーブル値パラメーター (TVP)、BulkCopy、および Always Encrypted でサポートされません。 このページでは、JDBC ドライバーで Geometry と Geography データ型のケースを使用して、さまざまな表示されます。 空間データ型の概要については、確認[空間データ型の概要](https://docs.microsoft.com/en-us/sql/relational-databases/spatial/spatial-data-types-overview)ページ。

## <a name="creating-a-geometry--geography-object"></a>Geometry の作成/Geography オブジェクト

Geometry / Geography オブジェクトを作成する主な方法は 2 つあります - Well-Known Text (WKT) または、Well-Known Binary (WKB) のいずれかから変換します。

### <a name="creating-from-wkt"></a>WKT から作成します。

```java
String geoWKT = "LINESTRING(1 0, 0 1, -1 0)";
Geometry geomWKT = Geometry.STGeomFromText(geoWKT, 0);
Geography geogWKT = Geography.STGeomFromText(geoWKT, 4326);
```

SRID が 4326 LINESTRING Geometry オブジェクトをシステム識別子 SRID (Spatial Reference)、0 と Geography オブジェクトが作成されます。

### <a name="creating-from-wkb"></a>WKB から作成します。

```java
byte[] geomWKB = Hex.decodeHex("00000000010403000000000000000000F03F00000000000000000000000000000000000000000000F03F000000000000F0BF000000000000000001000000010000000001000000FFFFFFFF0000000002".toCharArray());
byte[] geogWKB = Hex.decodeHex("E61000000104030000000000000000000000000000000000F03F000000000000F03F00000000000000000000000000000000000000000000F0BF01000000010000000001000000FFFFFFFF0000000002".toCharArray());

Geometry geomWKT = Geometry.deserialize(geomWKB);
Geography geogWKT = Geography.deserialize(geogWKB);
```

これにより、以前、WKT から作成したものに相当する Geometry と Geography オブジェクトが作成されます。

## <a name="working-with-a-geometry--geography-object"></a>ジオメトリの使用/Geography オブジェクト

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

Geography 列を使用して、Geography 対応の同様の手法と**setGeography()** メソッド。

Geometry を読み取り/Geography 列。

```java
try(SQLServerResultSet rs = (SQLServerResultSet)stmt.executeQuery("select * from geomTable")) {
    while(rs.next()){
        rs.getGeometry(1);
    }
}
```

Geography 列を使用して、Geography 対応の同様の手法と**getGeography()** メソッド。

## <a name="newly-introduced-apis"></a>新しく導入された Api

これらは、クラスでこの追加で導入された新しいパブリック Api **SQLServerPreparedStatement**、 **SQLServerResultSet**、 **Geometry**、および**Geography**します。

### <a name="sqlserverpreparedstatement"></a>SQLServerPreparedStatement

|方法|[説明]|
|:------|:----------|
|void setGeometry (int n、Geometry x)| 指定された microsoft.sql.Geometry クラスのオブジェクトを指定されたパラメーターを設定します。
|void setGeography (int n、Geography x)| 指定された microsoft.sql.Geography クラスのオブジェクトを指定されたパラメーターを設定します。

### <a name="sqlserverresultset"></a>SQLServerResultSet

|方法|[説明]|
|:------|:----------|
|Geometry getGeometry (int colunIndex)| この結果セット オブジェクトの現在の行で指定された列の値を Java プログラミング言語で com.microsoft.sqlserver.jdbc.Geometry オブジェクトとして返します。
|Geometry getGeometry (文字列 columnName)| この結果セット オブジェクトの現在の行で指定された列の値を Java プログラミング言語で com.microsoft.sqlserver.jdbc.Geometry オブジェクトとして返します。
|Geography getGeography (int colunIndex)| この結果セット オブジェクトの現在の行で指定された列の値を Java プログラミング言語で com.microsoft.sqlserver.jdbc.Geography オブジェクトとして返します。
|Geography getGeography (文字列 columnName)| この結果セット オブジェクトの現在の行で指定された列の値を Java プログラミング言語で com.microsoft.sqlserver.jdbc.Geography オブジェクトとして返します。

### <a name="geometry"></a>Geometry

|方法|[説明]|
|:------|:----------|
|Geometry STGeomFromText (文字列 wkt、int SRID)| インスタンスに格納されている Z (標高) 値と M (メジャー) 値で補完された、Open Geospatial Consortium (OGC) の Well-Known Text (WKT) 表現からの Geometry インスタンス用のコンストラクター。
|Geometry STGeomFromWKB (byte wkb)| Open Geospatial Consortium (OGC) の Well-Known Binary (WKB) 表現からの Geometry インスタンス用のコンストラクター。
|ジオメトリ (byte wkb) を逆シリアル化します。| 空間データの SQL Server 内部形式からの Geometry インスタンスのコンス トラクター。
|ジオメトリの解析 (文字列 wkt)| Open Geospatial Consortium (OGC) の Well-Known Text (WKT) 表現からの Geometry インスタンス用のコンストラクター。 空間参照識別子は、0 を既定値は。
|ジオメトリのポイント (double x、y の二重、int SRID)| その X と Y 値および空間参照識別子から Point インスタンスを表す Geometry インスタンスのコンス トラクター。
|文字列:stastext()| Geometry インスタンスにおける Open Geospatial Consortium (OGC) の Well-Known Text (WKT) 表現を返します。 このテキストは、インスタンスに格納されている Z (標高) 値または M (メジャー) 値を含みません。
|byte[] STAsBinary()| Geometry インスタンスにおける Open Geospatial Consortium (OGC) の Well-Known Binary (WKB) 表現を返します。 この値には、インスタンスに格納されている Z 値または M 値が含まれません。
|バイト [serialize()| Geometry 型の内部 SQL Server 形式を表すバイトを返します。
|ブール hasM()| オブジェクトに M (メジャー) 値が含まれているかどうかを返します。
|ブール hasZ()| オブジェクトには、Z (標高) 値が含まれている場合を返します。
|二重 getX()| X 座標の値を返します。
|二重 getY()| Y 座標の値を返します。
|二重 getM()| オブジェクトの M (メジャー) 値を返します。
|二重 getZ()| オブジェクトの Z (標高) 値を返します。
|int getSrid()| 空間参照識別子 (SRID) の値を返します。
|ブール isNull()| Geometry オブジェクトのかどうかは null を返します。
|int STNumPoints()| Geometry オブジェクト内の地点の数を返します。
|文字列 STGeometryType()| geometry インスタンスで表される Open Geospatial Consortium (OGC) の型名を返します。
|文字列 asTextZM()| Geometry オブジェクトの Well-Known Text (WKT) 表現を返します。
|文字列の toString()| Geometry オブジェクトの文字列表現を返します。

### <a name="geography"></a>Geography

|方法|[説明]|
|:------|:----------|
|Geography STGeomFromText (文字列 wkt、int SRID)| インスタンスに格納されている Z (標高) 値と M (メジャー) 値で補完された、Open Geospatial Consortium (OGC) の Well-Known Text (WKT) 表現からの Geography インスタンス用のコンストラクター。
|Geography STGeomFromWKB (byte wkb)| Open Geospatial Consortium (OGC) の Well-Known Binary (WKB) 表現からの Geography インスタンス用のコンストラクター。
|Geography が (byte wkb) を逆シリアル化します。| 空間データの SQL Server 内部形式からの Geography インスタンスのコンス トラクター。
|Geography の解析 (文字列 wkt)| Open Geospatial Consortium (OGC) の Well-Known Text (WKT) 表現からの Geography インスタンス用のコンストラクター。 空間参照識別子は、0 を既定値は。
|地理的ポイント (lat, lon の二重、int SRID を二重)| Point インスタンスを緯度、経度、SRID (spatial reference identifier) で表す Geography インスタンス用のコンストラクター。
|文字列:stastext()| Geography インスタンスにおける Open Geospatial Consortium (OGC) の Well-Known Text (WKT) 表現を返します。 このテキストは、インスタンスに格納されている Z (標高) 値または M (メジャー) 値を含みません。
|byte[] STAsBinary())| Geography インスタンスにおける Open Geospatial Consortium (OGC) の Well-Known Binary (WKB) 表現を返します。 この値には、インスタンスに格納されている Z 値または M 値が含まれません。
|バイト [serialize()| Geography 型の内部 SQL Server 形式を表すバイトを返します。
|ブール hasM()| オブジェクトに M (メジャー) 値が含まれているかどうかを返します。
|ブール hasZ()| オブジェクトには、Z (標高) 値が含まれている場合を返します。
|二重 getLatitude()| 緯度の値を返します。
|二重 getLongitude()| 経度値を返します。
|二重 getM()| オブジェクトの M (メジャー) 値を返します。
|二重 getZ()| オブジェクトの Z (標高) 値を返します。
|int getSrid()| 空間参照識別子 (SRID) の値を返します。
|ブール isNull()| Geography オブジェクトのかどうかは null を返します。
|int STNumPoints()| Geography オブジェクト内の地点の数を返します。
|文字列 STGeographyType()| geography インスタンスで表される Open Geospatial Consortium (OGC) の型名を返します。
|文字列 asTextZM()| Geography オブジェクトの Well-Known Text (WKT) 表現を返します。
|文字列の toString()| Geography オブジェクトの文字列表現を返します。

## <a name="limitations-of-spatial-datatypes"></a>空間データ型の制限事項

1. 空間のサブ型**CircularString**、 **CompoundCurve**、 **CurvePolygon**、および**FullGlobe**以降のみサポートされますSQL server 2012 以降。

2. 常に暗号化は空間データ型では使用できません。

3. ストアド プロシージャ、TVP、BulkCopy 空間データ型を持つ現在は操作はできません。

## <a name="see-also"></a>参照

[空間データ型のサンプル (JDBC)](../../connect/jdbc/spatial-data-types-sample.md)
