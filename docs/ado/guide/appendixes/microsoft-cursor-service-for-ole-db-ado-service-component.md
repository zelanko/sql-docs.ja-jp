---
title: "OLE DB (ADO サービス コンポーネント) 用 Microsoft カーソル サービス |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: H1Hack27Feb2017
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- providers [ADO], cursor service for OLE DB
- cursor service for OLE DB [ADO]
ms.assetid: 420d0989-7cfb-4c66-a7b5-f4199d13165d
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d7a1f8568b633417196c6c9dda3e8a3615146603
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="microsoft-cursor-service-for-ole-db-overview"></a>OLE DB の概要の Microsoft カーソル サービス
OLE DB 用の Microsoft カーソル サービスは、データ プロバイダーのカーソル サポート機能を補完します。 その結果、ユーザーは、すべてのデータ プロバイダーで比較的一定な機能を認識します。

 カーソル サービスは、動的なプロパティを使用できるようにし、特定のメソッドの動作が向上します。 たとえば、[最適化](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)動的プロパティなど、特定の操作を容易に一時インデックスの作成を使用して、[検索](../../../ado/reference/ado-api/find-method-ado.md)メソッド。

 カーソル サービスは、常にバッチを更新するためのサポートを有効します。 データ プロバイダーのみを提供する静的カーソルなどの低機能のカーソルと動的カーソルの場合より高機能な種類のカーソルをシミュレートします。

## <a name="keyword"></a>Keyword
 このサービス コンポーネントを呼び出すには、設定、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)または[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトの[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティを**adUseClient**です。

```
connection.CursorLocation=adUseClient
recordset.CursorLocation=adUseClient
```

## <a name="dynamic-properties"></a>動的プロパティ
 次の動的なプロパティを追加の OLE DB カーソル サービスが呼び出されたときに、 **Recordset**オブジェクトの[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクション。 完全な一覧**接続**と**Recordset**オブジェクトの動的プロパティの一覧は、 [ADO の動的プロパティのインデックス](../../../ado/reference/ado-api/ado-dynamic-property-index.md)です。 関連付けられている OLE DB プロパティの名前、適切な場所は、かっこ内に含ま ADO プロパティ名の後にします。

 カーソル サービスを呼び出した後に、いくつかの動的プロパティへの変更を基になるデータ ソースに表示されません。 たとえば、設定、*コマンド タイムアウト*プロパティを**レコード セット**は基になるデータ プロバイダーに表示されません。

```

Recordset1.CursorLocation = adUseClient     'invokes cursor service
Recordset1.Open "authors", _
    "Provider=SQLOLEDB;Data Source=DBServer;User Id=MyUserID;" & _
    "Password=MyPassword;Initial Catalog=pubs;",,adCmdTable
Recordset1.Properties.Item("Command Time out") = 50
' 'Command Time out' property on DBServer is still default (30).

```

 基になるプロバイダーの動的なプロパティを設定する必要がありますが、アプリケーションには、カーソル サービスが必要ですが場合、は、カーソルのサービスを呼び出す前にプロパティを設定します。 コマンド オブジェクトのプロパティの設定は常に、カーソルの場所に関係なく、基になるデータ プロバイダーに渡されます。 そのため、いつでもプロパティを設定するのにコマンド オブジェクトを使用することもできます。

> [!NOTE]
>  基になるデータ プロバイダーによってサポートされている場合でも、DBPROP_SERVERDATAONINSERT 動的プロパティは、カーソル サービスによってサポートされていません。

|プロパティ名|Description|
|-------------------|-----------------|
|自動再計算 (DBPROP_ADC_AUTORECALC)|この値がどのくらいの頻度を示します Data Shaping Service で作成されたレコード セットの集計と計算列が計算されます。 既定値 (値 = 1) を Data Shaping Service では、値が変更されたことを決定するたびに再計算されます。 値が 0 の場合、階層の最初にビルド時に、計算列または集計列はのみ計算されます。|
|バッチ サイズ (DBPROP_ADC_BATCHSIZE)|データ ストアに送信される前にバッチ処理できる update ステートメントの数を示します。 バッチ内の複数のステートメント、データを少ないラウンド トリップを格納します。|
|子の行をキャッシュする (DBPROP_ADC_CACHECHILDROWS)|レコード セットの Data Shaping Service で作成された場合、この値は、子のレコード セットが後で使用できるキャッシュに格納されているかどうかを示します。|
|カーソル エンジンのバージョン (DBPROP_ADC_CEVER)|使用されているカーソル サービスのバージョンを示します。|
|変更の状態 (DBPROP_ADC_MAINTAINCHANGESTATUS) の管理します。|複数のテーブルの結合の 1 つまたは複数の行の再同期に使用されるコマンドのテキストを示します。|
|[最適化](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)|インデックスを作成するかどうかを示します。 設定すると**True**、一時的な特定の操作の実行を向上させるためにインデックスの作成を許可します。|
|[名前の形状変更します。](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md)|名前を示す、 **Recordset**です。 現在、内で参照されているまたはそれ以降、データ シェイプ コマンド。|
|[コマンドを再同期します。](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md)|によって使用されるカスタム コマンド文字列を示します、[再同期](../../../ado/reference/ado-api/resync-method.md)メソッドときに、[一意テーブル](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)プロパティが有効になっています。|
|[固有のカタログ](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|参照されているテーブルを含むデータベースの名前を示す、**一意テーブル**プロパティです。|
|[一意なスキーマ](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|参照されるテーブルの所有者の名前を示す、**一意テーブル**プロパティです。|
|[一意テーブル](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|1 つのテーブルの名前を示す、**レコード セット**挿入、更新、または削除によって変更できる複数のテーブルから作成します。|
|更新基準 (DBPROP_ADC_UPDATECRITERIA)|どのフィールドを示す、**場所**句は、更新中に発生した競合の処理に使用します。|
|[再同期を更新](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)(DBPROP_ADC_UPDATERESYNC)|示すかどうか、**再同期**メソッドが後に暗黙的に呼び出されます、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)メソッド (とその動作) ときに、**一意テーブル**プロパティが有効になってです。|

 設定またはのインデックスとしての名前を指定して動的なプロパティを取得することができますも、**プロパティ**コレクション。 たとえば、取得しての現在の値を出力、[最適化](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)動的プロパティは、新しい値が次のように設定し、します。

```
Debug.Print rs.Properties("Optimize")
rs.Properties("Optimize") = True
```

## <a name="built-in-property-behavior"></a>組み込みのプロパティの動作
 OLE DB のカーソル サービスは、特定の組み込みのプロパティの動作にも影響します。

|プロパティ名|Description|
|-------------------|-----------------|
|[カーソル。](../../../ado/reference/ado-api/cursortype-property-ado.md)|利用可能なカーソルの種類を補足するもの、 **Recordset**です。|
|[ロック。](../../../ado/reference/ado-api/locktype-property-ado.md)|使用可能なロックの種類を補足するもの、 **Recordset**です。 一括更新を可能にします。|
|[Sort](../../../ado/reference/ado-api/sort-property.md)|1 つまたは複数のフィールドの名前を指定します、**レコード セット**並べ替えは、各フィールドが昇順または降順で並べ替えられたかどうか、およびです。|

## <a name="method-behavior"></a>メソッドの動作
 OLE DB のカーソルのサービスを有効またはの動作に影響、[フィールド](../../../ado/reference/ado-api/field-object.md)オブジェクトの[Append](../../../ado/reference/ado-api/append-method-ado.md)メソッドおよび**レコード セット**オブジェクトの[を開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)、[再同期](../../../ado/reference/ado-api/resync-method.md)、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)、および[保存](../../../ado/reference/ado-api/save-method.md)メソッドです。

