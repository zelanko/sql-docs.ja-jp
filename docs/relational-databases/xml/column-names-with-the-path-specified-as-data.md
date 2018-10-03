---
title: パスを data() として指定した列の名前 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
ms.assetid: 0b738e44-6108-4417-a9a4-abeb7680d899
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e3825e186fcebf2995050b7f32c6c2de38b09dcb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47772410"
---
# <a name="column-names-with-the-path-specified-as-data"></a>パスを data() として指定した列の名前
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  列名として指定したパスが "data()" の場合、生成される XML では列の値がアトミック値として処理されます。 シリアル化時の後続アイテムもアトミック値である場合は、空白文字が XML に追加されます。 これはリスト状の要素値または属性値を作成する場合に有用です。 次のクエリでは、製品モデルの ID および名前と、そのモデルに含まれる製品のリストを取得します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID       AS "@ProductModelID",  
       Name                 AS "@ProductModelName",  
      (SELECT ProductID AS "data()"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
      FOR XML PATH (''))    AS "@ProductIDs"  
FROM  Production.ProductModel  
WHERE ProductModelID= 7   
FOR XML PATH('ProductModelData');  
```  
  
 入れ子の内側の SELECT では、製品 ID のリストを取得しています。 製品 ID の列名が "data()" と指定されています。 PATH モードでは空文字列が行の要素名に指定されるので、ここでは行要素は生成されません。 代わりに、親の SELECT で指定した <`ProductModelData`> 行要素の ProductIDs 属性に設定された値が返されます。 結果を次に示します。  
  
 `<ProductModelData ProductModelID="7"`  
  
 `ProductModelName="HL Touring Frame"`  
  
 `ProductIDs="885 887 888 889 890 891 892 893" />`  
  
## <a name="see-also"></a>参照  
 [FOR XML での PATH モードの使用](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
