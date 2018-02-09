---
title: "ADO オブジェクトとインターフェイス |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ADO, objects and interfaces
- objects [ADO]
ms.assetid: d0b7e254-c89f-4406-b846-a060ef038c30
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 76115318e0205c0b0f0bf4746dd482f39f4a8b89
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="ado-objects-and-interfaces"></a>ADO オブジェクトとインターフェイス
これらのオブジェクト間のリレーションシップがで表される、 [ADO オブジェクト モデル](../../../ado/reference/ado-api/ado-object-model.md)です。  
  
 各オブジェクトは、対応するコレクションに格納できます。 たとえば、[エラー](../../../ado/reference/ado-api/error-object.md)オブジェクトに格納できる、[エラー](../../../ado/reference/ado-api/errors-collection-ado.md)コレクション。 詳細については、次を参照してください。 [ADO コレクション](../../../ado/reference/ado-api/ado-collections.md)」、または特定のコレクション。  
  
|||  
|-|-|  
|[IADOCommandConstruction](https://msdn.microsoft.com/library/windows/desktop/aa965677.aspx)|ADOCommand オブジェクトから、基になる ole DB コマンドを取得するために使用します。|  
|[ADORecordConstruction](../../../ado/reference/ado-api/adorecordconstruction-interface.md)|ADO を構築**レコード**オブジェクトを OLE DB から**行**C/C++ アプリケーション内のオブジェクト。|  
|[ADORecordsetConstruction](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)|ADO を構築**Recordset**オブジェクトを OLE DB から**行セット**C/C++ アプリケーション内のオブジェクト。|  
|[ADOStreamConstruction インターフェイス](../../../ado/reference/ado-api/adostreamconstruction-interface.md)|ADO を構築**ストリーム**オブジェクトを OLE DB から**IStream** C/C++ アプリケーション内のオブジェクト。|  
|[Command](../../../ado/reference/ado-api/command-object-ado.md)|データ ソースに対して実行しようとする特定のコマンドを定義します。<br /><br /> **コマンド**オブジェクトはスクリプトを実行しても安全ではありません。|  
|[接続](../../../ado/reference/ado-api/connection-object-ado.md)|データ ソースへの接続を開くを表します。<br /><br /> **接続**オブジェクトにスクリプトを実行しても安全です。|  
|[IDSOShapeExtensions インターフェイス](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)|SHAPE プロバイダーの基になる ole DB データ ソース オブジェクトを取得します。|  
|[[エラー]](../../../ado/reference/ado-api/error-object.md)|プロバイダーを含む 1 つの操作に関連するデータ アクセス エラーの詳細が含まれています。<br /><br /> **エラー**オブジェクトはスクリプトを実行しても安全ではありません。|  
|[フィールド](../../../ado/reference/ado-api/field-object.md)|一般的なデータ型のデータの列を表します。|  
|[パラメーター](../../../ado/reference/ado-api/parameter-object.md)|パラメーターまたはに関連付けられている引数を表します、**コマンド**オブジェクトがパラメーター化されたクエリまたはストアド プロシージャに基づいています。<br /><br /> **パラメーター**オブジェクトはスクリプトを実行しても安全ではありません。|  
|[プロパティ](../../../ado/reference/ado-api/property-object-ado.md)|プロバイダーによって定義されている ADO オブジェクトの動的な特性を表します。|  
|[レコード](../../../ado/reference/ado-api/record-object-ado.md)|行を表し、 **Recordset**、ディレクトリまたはファイル システム内のファイルです。 **レコード**オブジェクトにスクリプトを実行しても安全です。|  
|[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)|ベース テーブル、または実行されたコマンドの結果から、レコードのセットを表します。 いつでも、 **Recordset**オブジェクトとして現在のレコード セット内で 1 つのレコードのみを参照します。<br /><br /> **Recordset**オブジェクトにスクリプトを実行しても安全です。|  
|[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)|データのバイナリ ストリームを表します。<br /><br /> **ストリーム**オブジェクトにスクリプトを実行しても安全です。|  
  
## <a name="see-also"></a>参照  
 [ADO の API リファレンス](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO コレクション](../../../ado/reference/ado-api/ado-collections.md)   
 [ADO の動的プロパティ](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [ADO 列挙定数](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [付録 b: ADO エラー](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [ADO イベント](../../../ado/reference/ado-api/ado-events.md)   
 [ADO メソッド](../../../ado/reference/ado-api/ado-methods.md)   
 [ADO オブジェクト モデル](../../../ado/reference/ado-api/ado-object-model.md)   
 [ADO のプロパティ](../../../ado/reference/ado-api/ado-properties.md)
