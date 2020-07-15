---
title: パスを data() として指定した列の名前 | Microsoft Docs
description: パスが data() として指定されている列名を含む XML クエリについて説明します。
ms.custom: fresh2019may
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
ms.assetid: 0b738e44-6108-4417-a9a4-abeb7680d899
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 71cddb62a7277d32d9f43f499c83f3df9e9f69d6
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85775589"
---
# <a name="column-names-with-the-path-specified-as-data"></a>パスを data() として指定した列の名前

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

列名として指定したパスが "data()" の場合、生成される XML では列の値がアトミック値として処理されます。 シリアル化時の後続アイテムもアトミック値である場合は、空白文字が XML に追加されます。 これはリスト状の要素値または属性値を作成する場合に有用です。 次のクエリでは、製品モデルの ID および名前と、そのモデルに含まれる製品のリストを取得します。  
  
```sql
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
  
 入れ子の内側の SELECT では、製品 ID のリストを取得しています。 製品 ID の列名が "data()" と指定されています。 PATH モードでは空文字列が行の要素名に指定されるので、ここでは行要素は生成されません。 代わりに、値は親の SELECT の `<ProductModelData>` 行要素の ProductIDs 属性に割り当てられて返されます。 結果を次に示します。  

```sql
<ProductModelData
  ProductModelID="7"
  ProductModelName="HL Touring Frame"
  ProductIDs="885 887 888 889 890 891 892 893"
/>
```

## <a name="see-also"></a>参照  
 [FOR XML での PATH モードの使用](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
