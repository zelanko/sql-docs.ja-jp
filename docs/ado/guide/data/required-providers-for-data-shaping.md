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
manager: craigg
ms.openlocfilehash: 482139f8aa3dc42bbd17593b58fcc8510f1fc9a8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47713840"
---
# <a name="required-providers-for-data-shaping"></a>データ シェイプに必要なプロバイダー
データ シェイプと、2 つのプロバイダー通常必要があります。 サービス プロバイダー、 [for OLE DB Data Shaping Service](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)、機能、および、OLE DB Provider for SQL Server などのデータ プロバイダーの整形データ提供、形状に表示するデータの行を提供[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 値として、サービス プロバイダー (MSDataShape) の名前を指定することができます、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト[プロバイダー](../../../ado/reference/ado-api/provider-property-ado.md)プロパティまたは接続文字列キーワード"プロバイダー = MSDataShape;"します。  
  
 値として、データ プロバイダーの名前を指定することができます、**データ プロバイダー**動的プロパティに追加される、**接続**オブジェクト[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションOLE DB、または接続文字列キーワードの Data Shaping Service"**データ プロバイダー = * * * プロバイダー*"。  
  
 データ プロバイダーは必要な場合、**レコード セット**は設定されません (などのように、暴露**レコード セット**列が新しいキーワードを使用して作成されます)。 その場合は、指定"**データ プロバイダー =** none;"します。  
  
## <a name="example"></a>例  
  
```  
Dim cnn As New ADODB.Connection  
cnn.Provider = "MSDataShape"  
cnn.Open "Data Provider=SQLOLEDB;Integrated Security=SSPI;Database=Northwind"  
```  
  
## <a name="see-also"></a>関連項目  
 [データ シェイプの例](../../../ado/guide/data/data-shaping-example.md)   
 [Shape の正式文法](../../../ado/guide/data/formal-shape-grammar.md)   
 [一般的な Shape コマンド](../../../ado/guide/data/shape-commands-in-general.md)
