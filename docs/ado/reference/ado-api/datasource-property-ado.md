---
title: DataSource プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::DataSource
helpviewer_keywords:
- DataSource property [ADO]
ms.assetid: 300a702a-3544-48c5-b759-83b511fe97e0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fd677e29631e53eeb71c43e8174baff553defc85
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67933248"
---
# <a name="datasource-property-ado"></a>DataSource プロパティ (ADO)
[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトとして表されるデータを格納するオブジェクトを示します。  
  
## <a name="remarks"></a>Remarks  
 このプロパティは、データ環境を使用してデータバインドコントロールを作成するために使用されます。 データ環境では、**レコードセット**オブジェクトとして表される名前付きオブジェクト (データメンバー) を含むデータ (データソース) のコレクションを保持します。  
  
 [DataMember](../../../ado/reference/ado-api/datamember-property.md)プロパティと**DataSource**プロパティは、組み合わせて使用する必要があります。  
  
 参照されるオブジェクトは、 **IDataSource**インターフェイスを実装する必要があり、 **IRowset**インターフェイスを含んでいる必要があります。  
  
## <a name="usage"></a>使用方法  
  
```  
Dim rs as New ADODB.Recordset  
rs.DataMember = "Command"     'Name of the rowset to bind to.  
Set rs.DataSource = myDE      'Name of the object containing an IRowset.  
```  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [DataMember プロパティ](../../../ado/reference/ado-api/datamember-property.md)
