---
title: 列挙ファセット | Microsoft Docs
description: SQL Server で列挙ファセットを使用して、XML スキーマを検証する方法について学習します。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- enumeration facets
ms.assetid: dec23a79-ddd6-4701-9721-55a2c435a34d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e8939b3c8654452f50b280ad66fe221f94220754
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85633138"
---
# <a name="enumeration-facets"></a>列挙ファセット
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ファセットに違反するパターン ファセットや列挙を含む型を使用する XML スキーマを拒否します。  
  
## <a name="example"></a>例  
 次のスキーマで示す列挙値には大文字と小文字が混在する値が使用されているので、このスキーマは拒否されます。 また、この値はパターン値 (小文字のみに制限) に違反しているという理由からも拒否されます。  
  
```  
CREATE XML SCHEMA COLLECTION MySampleCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="http://ns" xmlns:ns="http://ns">  
    <simpleType name="MyST">  
       <restriction base="string">  
          <pattern value="[a-z]*"/>  
       </restriction>  
    </simpleType>  
  
    <simpleType name="MyST2">  
       <restriction base="ns:MyST">  
           <enumeration value="mYstring"/>  
       </restriction>  
    </simpleType>  
</schema>'  
GO  
```  
  
## <a name="see-also"></a>参照  
 [サーバー上の XML スキーマ コレクションの要件と制限](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
