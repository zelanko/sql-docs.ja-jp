---
title: データ シェイプに必要なプロバイダー |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], data shaping
- data shaping [ADO], providers required
ms.assetid: d49d48d2-ac2d-4c11-895c-5a149b444620
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ce88a316a1ef31baf083032e31023d36a3e3fff4
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="required-providers-for-data-shaping"></a>データ シェイプに必要なプロバイダー
データ シェイプと、2 つのプロバイダー通常必要があります。 サービス プロバイダー [for OLE DB Data Shaping Service](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)、整形を行う機能、および、OLE DB Provider for SQL Server などのデータ プロバイダーのデータを提供、形状に表示するデータの行を渡します[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 値として、サービス プロバイダー (MSDataShape) の名前を指定することができます、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト[プロバイダー](../../../ado/reference/ado-api/provider-property-ado.md)プロパティまたは接続文字列キーワード"プロバイダー = MSDataShape;"です。  
  
 値として、データ プロバイダーの名前を指定することができます、**データ プロバイダー**動的プロパティに追加されている、**接続**オブジェクト[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)によるコレクションOLE DB、または接続文字列キーワードの Data Shaping Service"**Data Provider = * * * プロバイダー*"です。  
  
 データ プロバイダーは必要な場合、**レコード セット**は設定されません (などのように、用意された**レコード セット**列が新しいキーワードを使用して作成されます)。 その場合は、指定"**Data Provider =**none;"です。  
  
## <a name="example"></a>例  
  
```  
Dim cnn As New ADODB.Connection  
cnn.Provider = "MSDataShape"  
cnn.Open "Data Provider=SQLOLEDB;Integrated Security=SSPI;Database=Northwind"  
```  
  
## <a name="see-also"></a>参照  
 [データ シェイプの例](../../../ado/guide/data/data-shaping-example.md)   
 [図形の正式な文法](../../../ado/guide/data/formal-shape-grammar.md)   
 [一般的な Shape コマンド](../../../ado/guide/data/shape-commands-in-general.md)
