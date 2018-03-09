---
title: "注釈の解釈 (SQLXML 4.0) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, XML Bulk Load
- XML Bulk Load [SQLXML], annotation intepretations
- annotations [SQLXML]
- bulk load [SQLXML], annotation interpretations
- annotated XDR schemas, XML Bulk Load
ms.assetid: 1c46bdb6-2812-4a13-b60b-7101c04b299f
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7f2d066414f6835f0803d6530e0ea1fa187c04ff
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="annotation-interpretation-sqlxml-40"></a>注釈の解釈 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
ここでは、XML 一括読み込みで XSD スキーマの注釈がどのように解釈されるかを説明します。 ここで説明する動作は、XDR スキーマの注釈にも当てはまります。  
  
> [!NOTE]  
>  ここで提供する情報は、XML 一括読み込みの処理で使用される注釈に関するものだけです。 SQLXML 4.0 でサポートされている XSD スキーマの注釈の一覧については、次を参照してください[注釈 XSD スキーマ &#40; の使用。SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/using-annotations-in-xsd-schemas-sqlxml-4-0.md). XDR スキーマでサポートされる注釈の一覧は、次を参照してください。[注釈付き XDR スキーマ &#40; SQLXML 4.0 &#41; で推奨されなくなった](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [sql:relationship とキーの順序付け規則 &#40;です。SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-relationship-and-key-ordering-rule.md)  
 について説明しますが、どのように**sql:relationship** XML 一括読み込みで注釈が解釈されます。  
  
 [sql: マップ &#40;です。SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-mapped.md)  
 について説明しますが、どのように**sql: マップ**XML 一括読み込みで注釈が解釈されます。  
  
 [sql:limit-フィールドと sql:limit-値 &#40;です。SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 について説明します、 **sql:limit-フィールド**と**sql:limit-値**注釈は、XML 一括読み込みで解釈されます。  
  
 [sql:overflow-フィールド &#40;です。SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md)  
 について説明しますが、どのように**sql:overflow** XML 一括読み込みで注釈が解釈されます。  
  
 [その他の注釈と #40 です。SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-other-annotations.md)  
 XML 一括読み込みで、次の注釈を解釈する方法について説明します**sql:id-プレフィックス**、 **sql:use-cdata**、 **sql:url-エンコード**、 **sql:。マッピング スキーマ**、 **sql:key-フィールド**です。  
  
  
