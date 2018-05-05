---
title: データを確認するためのレコード セットのサンプル |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- record location [ADO]
- current record [ADO]
ms.assetid: e770e626-68b1-4ddf-a217-d7b30311e2ee
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ca05161aad6aaaf79f1e1af85d7e83d55e6997ad
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sample-recordset-for-examining-data"></a>データを確認するためのサンプルのレコード セット
最初に、見てみましょう、 **Recordset** Microsoft SQL server ベースの Northwind サンプル データに対して実行される次の SQL クエリを使用して返されるオブジェクトします。  
  
```  
SELECT ProductID,ProductName,UnitPrice   
FROM Products   
WHERE CategoryID = 7    
```  
  
 結果として得られる**Recordset**オブジェクトには、次の表に示すように、データベース内のすべての生成が含まれています。  
  
|ProductID|ProductName|UnitPrice|  
|---------------|-----------------|---------------|  
|7|伯父さん Bob の有機乾燥なし|30.0000|  
|14|階層|23.2500|  
|28|Rssle ザワークラウト|45.6000|  
|51|りんご|53.0000|  
|74|Longlife 階層|10.0000|  
  
 自分でこれらの結果を取得する場合は、次の JScript の例を試してください。  
  
-   [レコード セットを返す JScript の例](../../../ado/guide/data/jscript-code-example-to-return-a-recordset.md)
