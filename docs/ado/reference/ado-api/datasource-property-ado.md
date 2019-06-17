---
title: データ ソースのプロパティ (ADO) |Microsoft Docs
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
manager: jroth
ms.openlocfilehash: f913d6ef342a110d6484e05a2f1925e47d5abdac
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718485"
---
# <a name="datasource-property-ado"></a>DataSource プロパティ (ADO)
として表されるデータを格納しているオブジェクトを示す、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。  
  
## <a name="remarks"></a>コメント  
 このプロパティは、データ環境でのデータ バインド コントロールの作成に使用されます。 データ環境の保持を含むデータ (データ ソース) のコレクションの名前付きのオブジェクト (データ メンバー) として表される、 **Recordset**オブジェクト*します。*  
  
 [DataMember](../../../ado/reference/ado-api/datamember-property.md)と**DataSource**プロパティを組み合わせて使用する必要があります。  
  
 参照先のオブジェクトを実装する必要があります、 **IDataSource**インターフェイスを含める必要があります、 **IRowset**インターフェイス。  
  
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
