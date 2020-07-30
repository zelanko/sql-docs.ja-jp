---
title: ADO 動的プロパティ |Microsoft Docs
ms.prod: sql
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- dynamic properties [ADO]
- properties [ADO], dynamic
ms.assetid: d7b06d72-f792-4328-93a2-5006b9e2c581
author: rothja
ms.author: jroth
ms.openlocfilehash: c727f73abed5fe9a30ebf191e2c6da60f8baa13a
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242892"
---
# <a name="ado-dynamic-properties"></a>ADO の動的プロパティ
動的プロパティは、[接続](../../../ado/reference/ado-api/connection-object-ado.md)、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)、または[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトの[properties](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションに追加できます。 これらのプロパティのソースは、データプロバイダー ( [SQL Server の OLE DB プロバイダー](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)、 [OLE DB 用の Microsoft Cursor service](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)などのサービスプロバイダー) のいずれかです。 特定の動的プロパティの詳細については、適切なデータプロバイダーまたはサービスプロバイダーのドキュメントを参照してください。  
  
 [Ado 動的プロパティインデックス](../../../ado/reference/ado-api/ado-dynamic-property-index.md)は、各標準 OLE DB プロバイダー動的プロパティの ado と OLE DB 名の間の相互参照を提供します。  
  
 次の動的プロパティは特に興味深いものであり、前述のソースにも記載されています。 ADO を使用した特殊な機能については、次の一覧の ADO ヘルプトピックを参照してください。  
  
|動的プロパティ|説明|  
|-|-|  
|[最適化](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)|このフィールドにインデックスを作成するかどうかを指定します。|  
|[プロンプト](../../../ado/reference/ado-api/prompt-property-dynamic-ado.md)|OLE DB プロバイダーがユーザーに初期化情報の入力を求めるかどうかを指定します。|  
|[名前のリシェイプ](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md)|**レコードセット**オブジェクトの名前を指定します。|  
|[再同期コマンド](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md)|**一意のテーブル**動的プロパティに指定されたテーブル内のデータを更新するために再**同期**メソッドによって発行される、ユーザーが指定したコマンド文字列を指定します。|  
|[一意のテーブル、一意のスキーマ、一意のカタログ](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|**一意のテーブル**更新、挿入、および削除が許可されるベーステーブルの名前を指定します。<br /><br /> **一意のスキーマ**スキーマ、またはテーブルの所有者の名前を指定します。<br /><br /> **一意のカタログ**カタログ、またはテーブルを含むデータベースの名前を指定します。|  
|[再同期の更新](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)|**UpdateBatch**メソッドの後に暗黙の再**同期**メソッド操作を実行するかどうかを指定します。それを行う場合は、その操作のスコープを指定します。|
| &nbsp; | &nbsp; |

## <a name="see-also"></a>参照  
 [ADO API リファレンス](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO コレクション](../../../ado/reference/ado-api/ado-collections.md)   
 [ADO 列挙定数](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [付録 B: ADO エラー](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [ADO イベント](../../../ado/reference/ado-api/ado-events.md)   
 [ADO メソッド](../../../ado/reference/ado-api/ado-methods.md)   
 [ADO オブジェクトモデル](../../../ado/reference/ado-api/ado-object-model.md)   
 [ADO オブジェクトとインターフェイス](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [ADO のプロパティ](../../../ado/reference/ado-api/ado-properties.md)
