---
title: 注釈の解釈 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, XML Bulk Load
- XML Bulk Load [SQLXML], annotation intepretations
- annotations [SQLXML]
- bulk load [SQLXML], annotation interpretations
- annotated XDR schemas, XML Bulk Load
ms.assetid: 1c46bdb6-2812-4a13-b60b-7101c04b299f
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 80db781d32c8d48f9df48c27baa1807eef5a9f7b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68054392"
---
# <a name="annotation-interpretation-sqlxml-40"></a>注釈の解釈 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  ここでは、XML 一括読み込みで XSD スキーマの注釈がどのように解釈されるかを説明します。 ここで説明する動作は、XDR スキーマの注釈にも当てはまります。  
  
> [!NOTE]  
>  ここで提供する情報は、XML 一括読み込みの処理で使用される注釈に関するものだけです。 SQLXML 4.0 でサポートされている XSD スキーマの注釈の一覧は、次を参照してください。 [XSD スキーマで注釈を使用して&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/using-annotations-in-xsd-schemas-sqlxml-4-0.md)します。 XDR スキーマでサポートされる注釈の一覧は、次を参照してください。[注釈付き XDR スキーマ&#40;SQLXML 4.0 では非推奨&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [sql:relationship とキーの順序付け規則&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-relationship-and-key-ordering-rule.md)  
 について説明しますが、どのように**sql:relationship** XML 一括読み込みで注釈が解釈されます。  
  
 [sql: マップ&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-mapped.md)  
 について説明しますが、どのように**sql: マップ**XML 一括読み込みで注釈が解釈されます。  
  
 [sql:limit-フィールドおよび -値&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 について説明しますが、どのように**sql:limit-フィールド**と**sql:limit-値**注釈は、XML 一括読み込みで解釈されます。  
  
 [sql:overflow-フィールド&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md)  
 について説明しますが、どのように**sql:overflow** XML 一括読み込みで注釈が解釈されます。  
  
 [その他の注釈&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-other-annotations.md)  
 XML 一括読み込みで、次の注釈を解釈する方法について説明します**sql:id-プレフィックス**、 **sql:use-cdata**、 **sql:url-エンコード**、 **sql:。マッピング スキーマ**、 **sql:key-フィールド**します。  
  
  
