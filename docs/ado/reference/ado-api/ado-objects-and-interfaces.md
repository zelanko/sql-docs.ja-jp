---
description: ADO のオブジェクトとインターフェイス
title: ADO オブジェクトとインターフェイス |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, objects and interfaces
- objects [ADO]
ms.assetid: d0b7e254-c89f-4406-b846-a060ef038c30
author: rothja
ms.author: jroth
ms.openlocfilehash: 80a47336bb6453033a28b2d62eeda3700431594a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88451374"
---
# <a name="ado-objects-and-interfaces"></a>ADO のオブジェクトとインターフェイス
これらのオブジェクト間のリレーションシップは、 [ADO オブジェクトモデル](../../../ado/reference/ado-api/ado-object-model.md)で表現されます。  
  
 各オブジェクトは、対応するコレクションに含めることができます。 たとえば、 [エラー](../../../ado/reference/ado-api/error-object.md) オブジェクトを [エラー](../../../ado/reference/ado-api/errors-collection-ado.md) コレクションに含めることができます。 詳細については、「 [ADO コレクション](../../../ado/reference/ado-api/ado-collections.md) 」または「特定のコレクションに関するトピック」を参照してください。  
  
|オブジェクトまたはインターフェイス|説明|  
|-|-|  
|[IADOCommandConstruction](https://msdn.microsoft.com/library/windows/desktop/aa965677.aspx)|ADOCommand オブジェクトから基になる OLEDB コマンドを取得するために使用します。|  
|[ADORecordConstruction](../../../ado/reference/ado-api/adorecordconstruction-interface.md)|C/c + + アプリケーションの OLE DB **Row**オブジェクトから ADO**レコード**オブジェクトを構築します。|  
|[ADORecordsetConstruction](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)|C/c + + アプリケーションの OLE DB**行**セットオブジェクトから ADO**レコードセット**オブジェクトを構築します。|  
|[ADOStreamConstruction インターフェイス](../../../ado/reference/ado-api/adostreamconstruction-interface.md)|C/c + + アプリケーションの OLE DB **IStream**オブジェクトから ADO**ストリーム**オブジェクトを構築します。|  
|[コマンド](../../../ado/reference/ado-api/command-object-ado.md)|データソースに対して実行する特定のコマンドを定義します。<br /><br /> **コマンド**オブジェクトは、スクリプト作成には安全ではありません。|  
|[接続](../../../ado/reference/ado-api/connection-object-ado.md)|データ ソースへの開いた接続を表します。<br /><br /> **接続**オブジェクトは、スクリプトに対して安全です。|  
|[IDSOShapeExtensions インターフェイス](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)|図形プロバイダーの基になる OLEDB データソースオブジェクトを取得します。|  
|[Error](../../../ado/reference/ado-api/error-object.md)|プロバイダーに関連する1つの操作に関連するデータアクセスエラーの詳細が含まれています。<br /><br /> **エラー**オブジェクトは、スクリプト作成には安全ではありません。|  
|[フィールド](../../../ado/reference/ado-api/field-object.md)|共通のデータ型のデータ列を表します。|  
|[パラメーター](../../../ado/reference/ado-api/parameter-object.md)|パラメーター化クエリまたはストアドプロシージャに基づいて **Command** オブジェクトに関連付けられたパラメーターまたは引数を表します。<br /><br /> **パラメーター**オブジェクトは、スクリプト作成には安全ではありません。|  
|[プロパティ](../../../ado/reference/ado-api/property-object-ado.md)|プロバイダーによって定義される ADO オブジェクトの動的特性を表します。|  
|[レコード](../../../ado/reference/ado-api/record-object-ado.md)|**レコードセット**の行、またはファイルシステム内のディレクトリまたはファイルを表します。 **レコード**オブジェクトは、スクリプトに対して安全です。|  
|[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)|ベーステーブルからのレコードのセット、または実行されたコマンドの結果を表します。 **レコードセット**オブジェクトは、常に、セット内の1つのレコードのみを現在のレコードとして参照します。<br /><br /> **レコードセット**オブジェクトは、スクリプトに対して安全です。|  
|[Stream](../../../ado/reference/ado-api/stream-object-ado.md)|データのバイナリストリームを表します。<br /><br /> **ストリーム**オブジェクトは、スクリプトに対して安全です。|  
  
## <a name="see-also"></a>関連項目  
 [ADO API リファレンス](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO コレクション](../../../ado/reference/ado-api/ado-collections.md)   
 [ADO の動的プロパティ](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [ADO 列挙定数](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [付録 B: ADO エラー](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [ADO イベント](../../../ado/reference/ado-api/ado-events.md)   
 [ADO メソッド](../../../ado/reference/ado-api/ado-methods.md)   
 [ADO オブジェクトモデル](../../../ado/reference/ado-api/ado-object-model.md)   
 [ADO のプロパティ](../../../ado/reference/ado-api/ado-properties.md)
