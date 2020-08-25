---
description: 階層レコードセットの作成
title: 造詣階層レコードセット |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset fabrication [ADO]
- hierarchical Recordsets [ADO]
- fabricating hierarchical Recordsets [ADO]
- data shaping [ADO], hierarchical Recordsets
ms.assetid: a584e642-a4a3-418e-bc20-3aff81a5625a
author: rothja
ms.author: jroth
ms.openlocfilehash: e1bf51c8d7d6db2ac898787c3a649a0ecb0610cb
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806852"
---
# <a name="fabricating-hierarchical-recordsets"></a>階層レコードセットの作成
次の例では、データシェイプの文法を使用して、親、子、および孫 **レコードセット**の列を定義することで、基になるデータソースのない階層レコードセットを作成する方法を示します。  
  
 階層**レコードセット**を作成するには、 [OLE DB (ADO サービスプロバイダー) (MSDataShape) 用の Microsoft データ整形サービス](../appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)を指定する必要があります。また、 [connection](../../reference/ado-api/connection-object-ado.md)オブジェクトの[OPEN](../../reference/ado-api/open-method-ado-connection.md)メソッドの接続文字列パラメーターで NONE の Data Provider 値を指定できます。 詳細については、「 [データシェイプの必須プロバイダー](./required-providers-for-data-shaping.md)」を参照してください。  
  
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
  
 **レコードセット**が作成されるとすぐに、データセットの設定、操作、またはファイルへの保存を行うことができます。  
  
## <a name="see-also"></a>参照  
 [階層レコードセット内の行へのアクセス](./accessing-rows-in-a-hierarchical-recordset.md)   
 [仮形の文法](./formal-shape-grammar.md)   
 [データシェイプに必要なプロバイダー](./required-providers-for-data-shaping.md)   
 [Shape APPEND 句](./shape-append-clause.md)   
 [一般的な Shape コマンド](./shape-commands-in-general.md)