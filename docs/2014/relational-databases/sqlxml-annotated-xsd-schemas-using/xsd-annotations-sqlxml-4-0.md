---
title: XSD 注釈 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, annotations listed
- XSD schemas [SQLXML], annotations
ms.assetid: c62a6785-8d66-40a2-9c5d-80c73d600a3b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1b9e50cc418ef1fa2076b3207d7d3429694f160a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66013545"
---
# <a name="xsd-annotations-sqlxml-40"></a>XSD 注釈 (SQLXML 4.0)
  次の表では、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] で導入された XSD 注釈の一覧を示し、これらを [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] で導入された XDR 注釈と比較します。  
  
|XSD 注釈|説明|トピックリンク|XDR 注釈|  
|--------------------|-----------------|----------------|--------------------|  
|`sql:encode`|XML 要素または属性を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] BLOB 列にマップするときに、参照 URI を要求します。 この URI は、後で BLOB データを返すために使用できます。|[Sql: encode &#40;SQLXML 4.0&#41;を使用した BLOB データへの URL 参照の要求](requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)|`url-encode`|  
|`sql:guid`|列に対し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により生成される GUID 値を使用するか、アップデートグラムで提供される値を使用するかを指定します。|[sql:identity 注釈と sql:guid 注釈の使用](using-the-sql-identity-and-sql-guid-annotations.md)|サポートされていません。|  
|`sql:hide`|スキーマで指定されている要素または属性を、結果の XML ドキュメントで表示しないようにします。|[sql:hide を使用した要素と属性の非表示](hiding-elements-and-attributes-by-using-sql-hide.md)|サポートされていません。|  
|`sql:identity`|IDENTITY 型のデータベース列にマップされる任意のノードに指定できます。 この注釈に指定した値によって、データベース内の対応する IDENTITY 型列の更新方法が決まります。|[sql:identity 注釈と sql:guid 注釈の使用](using-the-sql-identity-and-sql-guid-annotations.md)|サポートされていません。|  
|`sql:inverse`|アップデートグラムロジックに対して、 ** \<sql: relationship>** を使用して指定されている親子リレーションシップの解釈を逆に指示します。|[Sql: relationship での sql: 逆属性の指定 &#40;SQLXML 4.0&#41;](specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)|サポートされていません。|  
|`sql:is-constant`|どのテーブルにもマップされない XML 要素を作成します。 要素は、クエリ出力に表示されます。|[Sql を使用した定数要素の作成: &#40;SQLXML 4.0&#41;](creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)|同じ|  
|`sql:key-fields`|テーブル内の行を一意に識別する列を指定します。|[Sql: キーフィールド &#40;SQLXML 4.0&#41;を使用したキー列の識別](identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)|同じ|  
|`sql:limit-field`<br /><br /> `sql:limit-value`|制限値に基づいて、返される値を制限します。|[Sql: limit-field および sql: limit-value &#40;SQLXML 4.0&#41;を使用した値のフィルター処理](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-limit-field-and-sql-limit-value.md)|同じ|  
|`sql:mapped`|スキーマのアイテムを結果から除外します。|[Sql: マップト &#40;SQLXML 4.0&#41;を使用した結果の XML ドキュメントからのスキーマ要素の除外](excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)|`map-field`|  
|`sql:max-depth`|スキーマで指定される再帰リレーションシップの深さを指定します。|[sql:max-depth を使用した、再帰リレーションシップの深さの指定](specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)|サポートされていません。|  
|`sql:overflow-field`|オーバーフローしたデータを含むデータベース列を識別します。|[Sql: overflow フィールドを使用した未使用データの取得 &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md)|同じ|  
|`sql:prefix`|有効な XML ID、IDREF、および IDREFS を作成します。 ID、IDREF、および IDREFS の値の前に文字列を付加します。|[Sql: prefix &#40;SQLXML 4.0&#41;を使用した有効な ID、IDREF、IDREFS 型の属性の作成](creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)|同じ|  
|`sql:relationship`|XML 要素間のリレーションシップを指定します。 リレーションシップの確立には、`parent`、`child`、`parent-key` および `child-key` 属性を使用します。|[Sql: relationship を使用したリレーションシップの指定 &#40;SQLXML 4.0&#41;](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)|属性名は次のように異なります。<br /><br /> `key-relation`<br /><br /> `foreign-relation`<br /><br /> `key`<br /><br /> `foreign-key`|  
|`sql:use-cdata`|XML ドキュメント内の特定の要素に、CDATA セクションを使用するよう指定します。|[Sql を使用した CDATA セクションの作成: &#40;SQLXML 4.0&#41;](creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)|同じ|  
  
> [!NOTE]  
>  XSD ネイティブの `targetNamespace` 属性は、[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] の XDR マッピング スキーマで導入された `target-namespace` 注釈に代わるものです。  
  
## <a name="see-also"></a>参照  
 [TargetNamespace 属性を使用してターゲットの名前空間を指定する &#40;SQLXML 4.0&#41;](specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
  
  
