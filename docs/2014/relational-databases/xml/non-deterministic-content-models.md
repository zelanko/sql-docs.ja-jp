---
title: 非決定的コンテンツ モデル | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- non-deterministic content models
- content models [XML in SQL Server]
ms.assetid: 9d4513e7-dd19-4491-b7c7-28bc7c2f8589
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 1f88981a6fb97eb3ddf4112027845cdf68639c74
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174421"
---
# <a name="non-deterministic-content-models"></a>非決定的コンテンツ モデル
  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 1 (SP1) よりも前の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、非決定的コンテンツ モデルを含む XML スキーマは拒否されていました。  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP1 以降では、オカレンス制約が 0、1、または unbounded の場合、非決定的コンテンツ モデルが許容されます。  
  
## <a name="example-non-deterministic-content-model-rejected"></a>例 : 拒否される非決定的コンテンツ モデル  
 次の例では、非決定的コンテンツ モデルを含む XML スキーマの作成を試みています。 このコードは、 `<root>` 要素には 2 つの `<a>` 要素で構成されたシーケンスが 1 つ必要なのか、 `<root>` 要素にはそれぞれ `<a>` 要素を含む 2 つのシーケンスが必要なのかが明確ではないので失敗します。  
  
```  
CREATE XML SCHEMA COLLECTION MyCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
    <element name="root">  
        <complexType>  
            <sequence minOccurs="1" maxOccurs="2">  
                <element name="a" type="string" minOccurs="1" maxOccurs="2"/>  
            </sequence>  
        </complexType>  
    </element>  
</schema>  
'  
GO  
```  
  
 このスキーマは、オカレンス制約を固有の位置に移動することにより修正できます。 たとえば、親要素であるシーケンス パーティクルに制約を移動できます。  
  
```  
<sequence minOccurs="1" maxOccurs="4">  
    <element name="a" type="string" minOccurs="1" maxOccurs="1"/>  
</sequence>  
```  
  
 または、子要素に制約を移動することもできます。  
  
```  
<sequence minOccurs="1" maxOccurs="1">  
     <element name="a" type="string" minOccurs="1" maxOccurs="4"/>  
</sequence>  
```  
  
## <a name="example-non-deterministic-content-model-accepted"></a>例 : 許容される非決定的コンテンツ モデル  
 次のスキーマは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SP1 よりも前のバージョンの [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] では拒否されます。  
  
```  
CREATE XML SCHEMA COLLECTION MyCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
    <element name="root">  
        <complexType>  
            <sequence minOccurs="0" maxOccurs="unbounded">  
                <element name="a" type="string" minOccurs="0" maxOccurs="1"/>  
                <element name="b" type="string" minOccurs="1" maxOccurs="unbounded"/>  
            </sequence>  
        </complexType>  
    </element>  
</schema>  
'  
GO  
```  
  
## <a name="see-also"></a>参照  
 [サーバー上の XML スキーマ コレクションの要件と制限](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  