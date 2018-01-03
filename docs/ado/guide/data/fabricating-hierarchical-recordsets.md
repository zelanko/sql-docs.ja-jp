---
title: "階層レコード セットを製造 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Recordset fabrication [ADO]
- hierarchical Recordsets [ADO]
- fabricating hierarchical Recordsets [ADO]
- data shaping [ADO], hierarchical Recordsets
ms.assetid: a584e642-a4a3-418e-bc20-3aff81a5625a
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 91871ae51f53b9330228db1b64bab422dfef0d4b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="fabricating-hierarchical-recordsets"></a>製造階層レコード セット
次の例は、親、子、および孫の列の定義に文法を整形するデータを使用して、基になるデータ ソースが存在しない階層のレコード セットを作成する方法を示しています。**レコード セット**です。  
  
 階層構造を作成する**Recordset**を指定する必要があります、 [Microsoft Data Shaping Service for OLE DB (ADO サービス プロバイダー)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (MSDataShape)、none でデータ プロバイダーの値を指定することができます、接続文字列パラメーター、[開く](../../../ado/reference/ado-api/open-method-ado-connection.md)のメソッド、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト。 詳細については、次を参照してください。[データ シェイプに必要なプロバイダー](../../../ado/guide/data/required-providers-for-data-shaping.md)です。  
  
```  
Dim cn As New ADODB.Connection  
Dim rsCustomers As New ADODB.Recordset  
  
cn.Open "Provider=MSDataShape;Data Provider=NONE;"  
  
strShape = _  
"SHAPE APPEND NEW adInteger AS CustID," & _  
            " NEW adChar(25) AS FirstName," & _  
            " NEW adChar(25) AS LastName," & _  
            " NEW adChar(12) AS SSN," & _  
            " NEW adChar(50) AS Address," & _  
         " ((SHAPE APPEND NEW adChar(80) AS VIN_NO," & _  
                        " NEW adInteger AS CustID," & _  
                        " NEW adChar(20) AS BodyColor, " & _  
                     " ((SHAPE APPEND NEW adChar(80) AS VIN_NO," & _  
                                    " NEW adChar(20) AS Make, " & _  
                                    " NEW adChar(20) AS Model," & _  
                                    " NEW adChar(4) AS Year) " & _  
                        " AS VINS RELATE VIN_NO TO VIN_NO))" & _  
            " AS Vehicles RELATE CustID TO CustID) "  
  
rsCustomers.Open strShape, cn, adOpenStatic, adLockOptimistic, -1  
```  
  
 すぐに、 **Recordset**された作成、設定、操作、または、そのファイルに保存します。  
  
## <a name="see-also"></a>参照  
 [階層のレコード セット内の行にアクセスします。](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [図形の正式な文法](../../../ado/guide/data/formal-shape-grammar.md)   
 [データ シェイプに必要なプロバイダー](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [図形の APPEND 句](../../../ado/guide/data/shape-append-clause.md)   
 [一般的な Shape コマンド](../../../ado/guide/data/shape-commands-in-general.md)
