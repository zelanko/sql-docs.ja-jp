---
title: "ADO の動的プロパティ |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dynamic properties [ADO]
- properties [ADO], dynamic
ms.assetid: d7b06d72-f792-4328-93a2-5006b9e2c581
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fca9f032f5a72df58b18206c8441365ce3c8a746
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="ado-dynamic-properties"></a>ADO の動的プロパティ
動的なプロパティに追加することができます、[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)のコレクション、[接続](../../../ado/reference/ado-api/connection-object-ado.md)、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)、または[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。 これらのプロパティのソースは、データ プロバイダーではなど、 [OLE DB Provider for SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)、またはサービス プロバイダーなど、 [OLE DB 用の Microsoft カーソル サービス](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)です。 適切なデータ プロバイダーまたは特定の動的プロパティの詳細についてはサービス プロバイダーのマニュアルを参照してください。  
  
 [ADO の動的プロパティ インデックス](../../../ado/reference/ado-api/ado-dynamic-property-index.md)プロパティごとに標準的な OLE DB プロバイダー動的 ADO および OLE DB 名の間の相互参照を提供します。  
  
 次の動的なプロパティは、特に興味深い前述したソースにも記載されています。 ADO の特別な機能は、次の一覧で、ADO のヘルプ トピックに記載されています。  
  
|||  
|-|-|  
|[最適化](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)|このフィールドにインデックスを作成する必要があるかどうかを指定します。|  
|[プロンプト](../../../ado/reference/ado-api/prompt-property-dynamic-ado.md)|OLE DB プロバイダーが初期化情報のユーザーの入力を求める必要があるかどうかを指定します。|  
|[名前の形状変更します。](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md)|名前を指定、 **Recordset**オブジェクト。|  
|[コマンドを再同期します。](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md)|文字列をユーザーが指定したコマンドを指定します、**再同期**でという名前のテーブル内のデータを更新するメソッドの問題、**一意テーブル**動的なプロパティです。|  
|[一意テーブル、一意なスキーマ、固有のカタログ](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|**一意テーブル**更新、挿入、および削除を許可する基になるベース テーブルの名前を指定します。<br /><br /> **一意なスキーマ**スキーマ、またはテーブルの所有者の名前を指定します。<br /><br /> **固有のカタログ**カタログ、またはテーブルを含むデータベースの名前を指定します。|  
|[更新プログラムの再同期](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)|指定するかどうか、 **UpdateBatch**メソッドは暗黙的な続けている**再同期**メソッド操作と、そのその操作のスコープです。|  
  
## <a name="see-also"></a>参照  
 [ADO の API リファレンス](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO コレクション](../../../ado/reference/ado-api/ado-collections.md)   
 [ADO 列挙定数](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [付録 b: ADO エラー](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [ADO イベント](../../../ado/reference/ado-api/ado-events.md)   
 [ADO メソッド](../../../ado/reference/ado-api/ado-methods.md)   
 [ADO オブジェクト モデル](../../../ado/reference/ado-api/ado-object-model.md)   
 [ADO オブジェクトとインターフェイス](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [ADO のプロパティ](../../../ado/reference/ado-api/ado-properties.md)

