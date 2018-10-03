---
title: '例 : &lt;row&gt; 要素の名前を変更する | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, renaming <row> example
ms.assetid: b042292a-0b6e-40a3-b254-71c06e626706
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 92308ee94df30ad14b752b6cd55877dc784ab22b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48057112"
---
# <a name="example-renaming-the-ltrowgt-element"></a>例 : &lt;row&gt; 要素の名前を変更する
  結果セットの各行では、RAW モードによって `<row>`要素が生成されます。 次のクエリに示すように、必要に応じて、RAW モードへの省略可能な引数を指定することにより、この要素に別の名前を指定できます。 クエリでは、行セットの行ごとに <`ProductModel`> 要素が返されます。  
  
## <a name="example"></a>例  
  
```  
SELECT ProductModelID, Name   
FROM Production.ProductModel  
WHERE ProductModelID=122  
FOR XML RAW ('ProductModel'), ELEMENTS  
GO  
```  
  
 結果は次のとおりです。 `ELEMENTS` ディレクティブがクエリに追加されたので、結果は要素中心になります。  
  
```  
<ProductModel>  
  <ProductModelID>122</ProductModelID>  
  <Name>All-Purpose Bike Stand</Name>  
</ProductModel>   
```  
  
## <a name="see-also"></a>参照  
 [FOR XML での RAW モードの使用](use-raw-mode-with-for-xml.md)  
  
  
