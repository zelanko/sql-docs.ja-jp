---
title: "XSLT 変換 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XSLT transformations in ADO
ms.assetid: 1a46196e-839f-4734-a59e-2c64609ffb9e
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7dc90399ec31c921bfebbd342bbc082365dc238d
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="xslt-transformations"></a>XSLT 変換
XSLT は、別の形式に変換する、生成された XML に適用できます。 ADO では、XML 形式を理解することは、わかりやすい形式に変換できる XSLT テンプレートの開発に役立ちます。  
  
 たとえば、レコード セットの各行を rs: データ要素の内部 z: 行要素として保存することがわかります。 同様に、レコード セットの各フィールドは、この要素の属性値のペアとして保存されます。  
  
## <a name="remarks"></a>解説  
 次の XSLT スクリプトは、ブラウザーに表示される HTML テーブルに変換する前のセクションで示した XML を適用できます。  
  
```  
<?xml version="1.0" encoding="ISO-8859-1"?>  
<html xmlns:xsl="http://www.w3.org/TR/WD-xsl">  
<body STYLE="font-family:Arial, helvetica, sans-serif; font-size:12pt; background-color:white">  
<table border="1" style="table-layout:fixed" width="600">  
  <col width="200"></col>  
  <tr bgcolor="teal">  
    <th><font color="white">CustomerId</font></th>  
    <th><font color="white">CompanyName</font></th>  
    <th><font color="white">ContactName</font></th>  
  </tr>  
<xsl:for-each select="xml/rs:data/z:row">  
  <tr bgcolor="navy">  
    <td><font color="white"><xsl:value-of select="@CustomerID"/></font></td>  
    <td><font color="white"><xsl:value-of select="@CompanyName"/></font></td>  
    <td><font color="white"><xsl:value-of select="@ContactName"/></font></td>   
  </tr>  
</xsl:for-each>  
</table>  
</body>  
</html>  
```  
  
 XSLT では、テーブルの見出しとレコード セットの各フィールドを表示する HTML テーブルに、ADO Save メソッドによって生成された XML ストリームに変換します。 テーブルの見出しおよび行も、割り当てられている異なるフォントと色。  
  
## <a name="see-also"></a>参照  
 [レコードを XML 形式で保持する](../../../ado/guide/data/persisting-records-in-xml-format.md)
