---
title: プロバイダーに必要なデータの整形 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], data shaping
- data shaping [ADO], providers required
ms.assetid: d49d48d2-ac2d-4c11-895c-5a149b444620
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b95d6e42174cbce4357562ac3b866f49f0b58fef
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66701796"
---
# <a name="required-providers-for-data-shaping"></a>データ シェイプに必要なプロバイダー
データ シェイプと、2 つのプロバイダー通常必要があります。 サービス プロバイダー、 [for OLE DB Data Shaping Service](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)、機能、および、OLE DB Provider for SQL Server などのデータ プロバイダーの整形データ提供、形状に表示するデータの行を提供[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 値として、サービス プロバイダー (MSDataShape) の名前を指定することができます、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト[プロバイダー](../../../ado/reference/ado-api/provider-property-ado.md)プロパティまたは接続文字列キーワード"プロバイダー = MSDataShape;"します。  
  
 値として、データ プロバイダーの名前を指定することができます、**データ プロバイダー**動的プロパティに追加される、**接続**オブジェクト[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションOLE DB、または接続文字列キーワードの Data Shaping Service"**データ プロバイダー =** _プロバイダー_"。  
  
 データ プロバイダーは必要な場合、**レコード セット**は設定されません (などのように、暴露**レコード セット**列が新しいキーワードを使用して作成されます)。 その場合は、指定"**データ プロバイダー =** none;"します。  
  
## <a name="example"></a>例  
  
```  
Dim cnn As New ADODB.Connection  
cnn.Provider = "MSDataShape"  
cnn.Open "Data Provider=SQLOLEDB;Integrated Security=SSPI;Database=Northwind"  
```  
  
## <a name="see-also"></a>参照  
 [データ シェイプの例](../../../ado/guide/data/data-shaping-example.md)   
 [Shape の正式文法](../../../ado/guide/data/formal-shape-grammar.md)   
 [一般的な Shape コマンド](../../../ado/guide/data/shape-commands-in-general.md)
