---
title: "XSINIL パラメーターを使用した NULL 値に対する要素の生成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FOR XML 句, null 値"
  - "null 値 [SQL Server], XML"
  - "ELEMENTS ディレクティブ"
  - "XSINIL パラメーター"
ms.assetid: 2dbc4e48-1cae-4d83-b371-3265da9687cc
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# XSINIL パラメーターを使用した NULL 値に対する要素の生成
  **ELEMENTS** ディレクティブにより構成される XML では、各列の値が XML の要素にマップされます。 列の値が NULL の場合、要素は追加されません。 ELEMENTS ディレクティブでオプションの **XSINIL** パラメーターを指定すると、NULL 値に対しても要素を作成するように要求できます。 この場合、値が NULL の各列に対して、TRUE に設定された **xsi:nil** 属性を持つ要素が返されます。  
  
## 参照  
 [FOR XML での RAW モードの使用](../../relational-databases/xml/use-raw-mode-with-for-xml.md)  
  
  