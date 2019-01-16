---
title: XSLT 変換 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- XSLT transformations in ADO
ms.assetid: 1a46196e-839f-4734-a59e-2c64609ffb9e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c522a8d278080d9249761309d29f465befe217d8
ms.sourcegitcommit: bfa10c54e871700de285d7f819095d51ef70d997
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2019
ms.locfileid: "54255057"
---
# <a name="xslt-transformations"></a>XSLT 変換
XSLT は、別の形式に変換して、生成される XML に適用できます。 ADO での XML 形式を理解することよりユーザー フレンドリな形式に変換する XSLT テンプレートの開発に役立ちます。  
  
 たとえば、rs: データ要素内の z: 行要素として、レコード セットの各行が保存されているを認識します。 同様に、レコード セットの各フィールドは、この要素の属性値のペアとして保存されます。  
  
## <a name="remarks"></a>コメント  
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
  
 XSLT では、テーブルの見出しとレコード セットの各フィールドを表示する HTML テーブルに、ADO の Save メソッドによって生成される XML ストリームに変換します。 テーブルの見出しおよび行も割り当てられているさまざまなフォントおよび色。  
  
## <a name="see-also"></a>参照  
 [レコードを XML 形式で保持する](../../../ado/guide/data/persisting-records-in-xml-format.md)
