---
title: DataSource プロパティ (ADO) |Microsoft ドキュメント
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
apitype: COM
f1_keywords:
- Recordset20::DataSource
helpviewer_keywords:
- DataSource property [ADO]
ms.assetid: 300a702a-3544-48c5-b759-83b511fe97e0
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6bd018a74b39e644710ede5e5f002d543dac3f2c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="datasource-property-ado"></a>DataSource プロパティ (ADO)
として表現されているデータを格納しているオブジェクトを示す、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。  
  
## <a name="remarks"></a>解説  
 このプロパティは、データ環境とデータ バインド コントロールを作成する使用されます。 として表されるオブジェクト (データ メンバー) をという名前を含むデータ (データ ソース) のコレクションを管理、 **Recordset**オブジェクト*です。*  
  
 [DataMember](../../../ado/reference/ado-api/datamember-property.md)と**データソース**プロパティを組み合わせて使用する必要があります。  
  
 参照先のオブジェクトを実装する必要があります、 **IDataSource**インターフェイスし、含める必要があります、 **IRowset**インターフェイスです。  
  
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
