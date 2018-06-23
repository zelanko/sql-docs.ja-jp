---
title: Xs:QName 型 | Microsoft Docs
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
- xs:QName type
ms.assetid: 72c5bfde-b0b2-4372-bf36-97ba930dea06
caps.latest.revision: 8
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 393130177c3597a9681e784e09be29fa8c2341fa
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173888"
---
# <a name="the-xsqname-type"></a>The xs:QName Type
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、XML スキーマ制約要素を使用する **xs:QName** から派生した型はサポートしません。 また、現在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、メンバー型に **QName** を指定した共用体型をサポートしません。  
  
## <a name="example"></a>例  
 次の `CREATE XML SCHEMA COLLECTION` ステートメントでは、共用体のメンバー型に `xs:QName` 型を指定しているため、XML スキーマを読み込めません。  
  
```  
CREATE XML SCHEMA COLLECTION QNameLimitation1 AS N'  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="myUnion">  
        <xs:union memberTypes="xs:int xs:QName"/>  
    </xs:simpleType>  
</xs:schema>'  
GO  
  
CREATE XML SCHEMA COLLECTION QNameLimitation2 AS N'  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="myUnion">  
        <xs:union memberTypes="xs:integer">  
   <xs:simpleType>  
    <xs:list itemType="xs:QName"/>  
   </xs:simpleType>  
  </xs:union>  
    </xs:simpleType>  
</xs:schema>'  
GO  
```  
  
 これらのステートメントはどちらも、エラーが発生して失敗します。  
  
## <a name="see-also"></a>参照  
 [サーバー上の XML スキーマ コレクションの要件と制限](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  