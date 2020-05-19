---
title: XSD スキーマでの注釈の使用 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, about annotated XSD schemas
- annotations [SQLXML]
- relationships [SQLXML]
- relationships [SQLXML], hierarchical relationships
- hierarchical relationships [SQLXML]
- mapping schema [SQLXML], scenarios for using
ms.assetid: 78f318a4-7a36-473b-9852-a4bae6940ce5
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 56a8d0daaa7eb64600c7e3a06f4121c45ce25a23
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82703498"
---
# <a name="using-annotations-in-xsd-schemas-sqlxml-40"></a>XSD スキーマでの注釈の使用 (SQLXML 4.0)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML 4.0 では、XML-Data Reduced (XDR) スキーマ言語で導入された注釈と同様に、XSD スキーマ言語で注釈がサポートされます。 XSD では、XDR でサポートされない追加の注釈も導入されています。  
  
 XSD スキーマでこれらの注釈を使用して、XML とリレーショナルのマッピングを指定できます。 これには、XSD スキーマ内の要素および属性から、データベース内のテーブル (ビュー) および列へのマッピングが含まれます。  
  
 注釈を指定しない場合は、既定のマッピングが行われます。 既定では、複合型の XSD 要素は指定したデータベースのテーブルまたはビュー名にマップされ、単純型の要素または属性は、要素または属性と同じ名前の列にマップされます。  
  
 これらの注釈を使用して、XML 内の階層リレーションシップを指定することもできます。これは、XSD スキーマがリレーショナルデータの XML ビューであるためです。  
  
 ここでは、XSD スキーマで使用できる注釈について説明し、それらの使用例を示します。  
  
> [!NOTE]  
>  すべての例では、それぞれの注釈付き XSD スキーマに対して、単純な XPath クエリを指定します。 前提条件として、XPath 言語について理解していることが必要です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [&#40;SQLXML 4.0&#41;の XSD 注釈](xsd-annotations-sqlxml-4-0.md)  
 XSD スキーマで使用できる注釈と、その説明、および同等の XDR 注釈を一覧で示します。  
  
 [テーブルおよび列への XSD 要素と属性の既定のマッピング &#40;SQLXML 4.0&#41;](default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
 既定のマッピングについて説明し、既定のマッピングに関連するタスクの例を示します。  
  
 [テーブルおよび列への XSD 要素と属性の明示的なマッピング &#40;SQLXML 4.0&#41;](explicit-mapping-xsd-elements-and-attributes-to-tables-and-columns.md)  
 `sql:relation` 注釈と `sql:field` 注釈の明示的なマッピングについて説明し、例を示します。  
  
 [Sql: relationship を使用したリレーションシップの指定 &#40;SQLXML 4.0&#41;](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
 `sql:relationship` 注釈について説明し、例を示します。  
  
 [Sql: relationship での sql: 逆属性の指定 &#40;SQLXML 4.0&#41;](specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)  
 `sql:inverse` 注釈について説明します。  
  
 [Sql を使用した定数要素の作成: &#40;SQLXML 4.0&#41;](creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)  
 `sql:is-constant` 注釈について説明し、例を示します。  
  
 [Sql: マップト &#40;SQLXML 4.0&#41;を使用した結果の XML ドキュメントからのスキーマ要素の除外](excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)  
 `sql:mapped` 注釈について説明し、例を示します。  
  
 [Sql: limit-field および sql: limit-value &#40;SQLXML 4.0&#41;を使用した値のフィルター処理](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 `sql:limit-field` 注釈と `sql:limit-value` 注釈について説明し、例を示します。  
  
 [Sql: キーフィールド &#40;SQLXML 4.0&#41;を使用したキー列の識別](identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)  
 `sql:key-fields` 注釈について説明し、例を示します。  
  
 [TargetNamespace 属性を使用してターゲットの名前空間を指定する &#40;SQLXML 4.0&#41;](specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
 について説明し、 **targetNamespace**属性の例を示します。  
  
 [Sql: prefix &#40;SQLXML 4.0&#41;を使用した有効な ID、IDREF、IDREFS 型の属性の作成](creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)  
 `sql:prefix` 注釈について説明し、例を示します。  
  
 [データ型の強制型変換と sql: datatype 注釈 &#40;SQLXML 4.0&#41;](data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)  
 `sql:datatype` 注釈について説明し、例を示します。  
  
 [XSD データ型から XPath データ型へのマッピング &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md)  
 XSD、XDR、および XPath のデータ型の対照表と、関連する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 変換の一覧を示します。  
  
 [Sql を使用した CDATA セクションの作成: &#40;SQLXML 4.0&#41;](creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)  
 `sql:use-data` 注釈について説明し、例を示します。  
  
 [Sql: encode &#40;SQLXML 4.0&#41;を使用した BLOB データへの URL 参照の要求](requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)  
 `sql:encode` 注釈について説明し、例を示します。  
  
 [Sql: overflow フィールドを使用した未使用データの取得 &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md)  
 `sql:overflow-field` 注釈について説明し、例を示します。  
  
 [sql:hide を使用した要素と属性の非表示](hiding-elements-and-attributes-by-using-sql-hide.md)  
 `sql:hide` 注釈について説明し、例を示します。  
  
 [sql:identity 注釈と sql:guid 注釈の使用](using-the-sql-identity-and-sql-guid-annotations.md)  
 `sql:identity` 注釈と `sql:guid` 注釈について説明し、例を示します。  
  
 [sql:max-depth を使用した、再帰リレーションシップの深さの指定](specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)  
 `sql:max-depth` 注釈について説明し、例を示します。  
  
## <a name="see-also"></a>参照  
 [SQLXML 4.0&#41;&#40;注釈付きスキーマのセキュリティに関する考慮事項](../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md)  
  
  
