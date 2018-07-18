---
title: '例 : &lt;row&gt; 要素の名前を変更する | Microsoft Docs'
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
- RAW mode, renaming <row> example
ms.assetid: b042292a-0b6e-40a3-b254-71c06e626706
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f339d18e2653897cbc956bb605e60ebf8154dc40
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37244762"
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
  
  
