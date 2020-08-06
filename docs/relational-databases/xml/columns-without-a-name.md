---
title: 名前のない列 | Microsoft Docs
description: XML を生成するときに、SQL Server で名前のない列を処理する方法について学習します。
ms.custom: ''
ms.date: 08/01/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns without
ms.assetid: 440de44e-3a56-4531-b4e4-1533ca933cac
author: rothja
ms.author: jroth
ms.openlocfilehash: 878f1a89240f8df02eaafb34cef09540b884b614
ms.sourcegitcommit: 7035d9471876c70b99c58bf9b46af5cce6e9c66c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2020
ms.locfileid: "87523444"
---
# <a name="columns-without-a-name"></a>名前のない列
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  名前のない列はインラインになります。 たとえば、計算列または入れ子になったスカラー クエリで列の別名を指定しないと、名前のない列が生成されます。 列が **xml** 型の場合、そのデータ型のインスタンスの内容が挿入されます。 それ以外の型の場合は、列の内容がテキスト ノードとして挿入されます。  
  
```sql
SELECT 2+2  
FOR XML PATH  
```  
  
 上のクエリは、次の XML を生成します。 既定では、行セットの行ごとに 1 つの `<row>` 要素が、結果の XML に生成されます。 これは RAW モードと同じ動作です。  
  
 `<row>4</row>`  
  
 次のクエリは 3 列の行セットを返します。 3 番目の名前がない列には、XML データが含まれています。 PATH モードにより、xml 型のインスタンスが挿入されます。  
  
```sql
USE AdventureWorks2012;  
GO  
SELECT ProductModelID,  
       Name,  
       Instructions.query(
           'declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
            /MI:root/MI:Location   
           ')   
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH ;  
GO  
```  
  
 結果の一部を次に示します。  
  
```xml
<row>
  <ProductModelID>7</ProductModelID>
  <Name>HL Touring Frame</Name>
  <MI:Location ...LocationID="10" ...></MI:Location>
  <MI:Location ...LocationID="20" ...></MI:Location>
  ...
</row>
```

## <a name="see-also"></a>参照  
 [FOR XML での PATH モードの使用](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
