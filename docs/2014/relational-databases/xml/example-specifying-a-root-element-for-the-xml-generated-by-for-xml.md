---
title: '例 : FOR XML で生成される XML のルート要素の指定 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, specifying root element example
- RAW mode, with FOR XML example
ms.assetid: bcc54b11-0713-4e43-8dbe-d6f3ad1993b5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e98a5918eaff3dcf1cadbff1795ae94a73a789f4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48172034"
---
# <a name="example-specifying-a-root-element-for-the-xml-generated-by-for-xml"></a>例 : FOR XML で生成される XML のルート要素の指定
  次のクエリに示すように、 `ROOT` クエリで `FOR XML` オプションを指定することにより、結果の XML に 1 つのトップレベル要素を要求できます。 `ROOT` ディレクティブに指定した引数で、ルート要素名を指定します。  
  
## <a name="example"></a>例  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name   
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119 or ProductModelID=115  
FOR XML RAW, ROOT('MyRoot')  
go  
```  
  
 結果を次に示します。  
  
```  
<MyRoot>  
  <row ProductModelID="122" Name="All-Purpose Bike Stand" />  
  <row ProductModelID="119" Name="Bike Wash" />  
  <row ProductModelID="115" Name="Cable Lock" />  
</MyRoot>  
```  
  
## <a name="see-also"></a>参照  
 [FOR XML での RAW モードの使用](use-raw-mode-with-for-xml.md)  
  
  
