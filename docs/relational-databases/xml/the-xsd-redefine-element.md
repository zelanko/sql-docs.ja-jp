---
title: "&lt;xsd:redefine&gt; 要素 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "xsd:redefine 要素"
ms.assetid: 5f3e9b65-f10e-4db2-a62c-b270ac11d04e
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# &lt;xsd:redefine&gt; 要素
  W3C XSD の **redefine** 要素は、スキーマ コンポーネントの再定義をサポートします。 ただし、このディレクティブのサポートはパフォーマンスの点で高コストになる可能性があるうえ、再定義したスキーマに関連付けられた **xml** データ型のインスタンスはすべて [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で再検証する必要があります。 このため、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではこれらの要素をサポートしません。 **\<xsd:redefine>** 要素を含む XML スキーマはサーバーに拒否されます。  
  
 スキーマまたはスキーマ コンポーネントを更新するには、代わりに次の方法を使用できます。  
  
1.  変更されたスキーマ コンポーネントを使用して新しい XML スキーマ コレクションを作成します。  
  
2.  再定義する XML スキーマ コレクションを使用しているすべての **xml** データ型 (XML DT) の型を再指定して、新しい XML スキーマ コレクションを使用するようにします。 そのためには、ALTER TABLE コマンドの ALTER COLUMN オプションを使用して列の型を再指定するか、変数やパラメーターの XML スキーマ コレクション制約を変更します。  
  
3.  古いバージョンの XML スキーマ コレクションを削除します。  
  
## 参照  
 [サーバー上の XML スキーマ コレクションの要件と制限](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  