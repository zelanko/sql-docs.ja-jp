---
title: "例 : ELEMENTS ディレクティブで XSINIL を指定する | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: RAW mode, specifying XSINIL example
ms.assetid: 07c873ff-1f9d-480e-8536-862c39eb8249
caps.latest.revision: "11"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 277d79a76cac65d132c925e4cd91ee1a77ade46f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="example-specifying-xsinil-with-the-elements-directive"></a>例 : ELEMENTS ディレクティブで XSINIL を指定する
  次のクエリでは、 `ELEMENTS` ディレクティブを指定し、クエリ結果から要素中心の XML を生成します。  
  
## <a name="example"></a>例  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductID, Name, Color  
FROM Production.Product  
FOR XML RAW, ELEMENTS;  
GO  
```  
  
 次に結果の一部を示します。  
  
```  
<row>  
  <ProductID>1</ProductID>  
  <Name>Adjustable Race</Name>  
</row>  
...  
<row>  
  <ProductID>317</ProductID>  
  <Name>LL Crankarm</Name>  
  <Color>Black</Color>  
</row>  
```  
  
 一部の製品では `Color` 列に NULL 値が含まれるので、その結果の XML では対応する <`Color`> 要素が生成されません。 `XSINIL` と共に `ELEMENTS` ディレクティブを追加することにより、結果セット内の Color 列が NULL 値の行も <`Color`> 要素を生成できます。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductID, Name, Color  
FROM Production.Product  
FOR XML RAW, ELEMENTS XSINIL ;  
```  
  
 結果の一部を次に示します。  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <ProductID>1</ProductID>  
  <Name>Adjustable Race</Name>  
  <Color xsi:nil="true" />  
</row>  
...  
<row>  
  <ProductID>317</ProductID>  
  <Name>LL Crankarm</Name>  
  <Color>Black</Color>  
</row>  
```  
  
## <a name="see-also"></a>参照  
 [FOR XML での RAW モードの使用](../../relational-databases/xml/use-raw-mode-with-for-xml.md)  
  
  
