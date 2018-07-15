---
title: 名前のない列 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns without
ms.assetid: 440de44e-3a56-4531-b4e4-1533ca933cac
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 723ee2f2c9d9da6665c6a9a4b530e3deb247ff2d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37292162"
---
# <a name="columns-without-a-name"></a>名前のない列
  名前のない列はインラインになります。 たとえば、計算列または入れ子になったスカラー クエリで列の別名を指定しないと、名前のない列が生成されます。 場合は、列`xml`型、そのデータ型のインスタンスの内容が挿入されます。 それ以外の型の場合は、列の内容がテキスト ノードとして挿入されます。  
  
```  
SELECT 2+2  
FOR XML PATH  
```  
  
 上のクエリは、次の XML を生成します。 既定では、行セットの行ごとに 1 つの <`row`> 要素が、結果の XML に生成されます。 これは RAW モードと同じ動作です。  
  
 `<row>4</row>`  
  
 次のクエリは 3 列の行セットを返します。 3 番目の名前がない列には、XML データが含まれています。 PATH モードにより、xml 型のインスタンスが挿入されます。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID,  
       Name,  
       Instructions.query('declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
                /MI:root/MI:Location   
              ')   
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH ;  
GO  
```  
  
 結果の一部を次に示します。  
  
 `<row>`  
  
 `<ProductModelID>7</ProductModelID>`  
  
 `<Name>HL Touring Frame</Name>`  
  
 `<MI:Location ...LocationID="10" ...></MI:Location>`  
  
 `<MI:Location ...LocationID="20" ...></MI:Location>`  
  
 `...`  
  
 `</row>`  
  
## <a name="see-also"></a>参照  
 [FOR XML での PATH モードの使用](use-path-mode-with-for-xml.md)  
  
  
