---
title: SQLXML 4.0 でのデータ型のサポートを xml |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLXML, xml data type support
- xml data type [SQL Server], SQLXML
ms.assetid: 9a6f5ad8-4a8f-4de7-ac17-81d5ccf78459
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 68cb00ced8f77b5921be07a3f6383d4436f0bade
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="xml-data-type-support-in-sqlxml-40"></a>SQLXML 4.0 での xml データ型のサポート
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  以降で[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サポート XML を使用してデータに型指定された、 **xml**データ型。 このトピックは、SQLXML 4.0 でのインスタンスを認識する方法に関する情報を提供、 **xml**それらのデータ型と実装をサポートします。  
  
## <a name="working-with-xml-data-types"></a>xml データ型の使用  
 SQL テーブルの実装を使用する方法の詳細を理解する**xml**データ型の列、次の例が提供されます。  
  
|タスク|例|トピック|  
|----------|-------------|-----------|  
|マップを含める方法、 **xml** XML ビューの列|"XML 要素を XML データ型の列にマップする"|[XSD 要素および属性からテーブルと列の既定のマッピング&#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)|  
|データを挿入する方法、 **xml**アップデート グラムで列|"XML データ型列にデータを挿入する"|[XML アップデート グラムを使用してデータを挿入する&#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)|  
|XML データを一括読み込み、 **xml**列|"xml データ型の列に一括読み込みを行う"|[XML 一括読み込みの例 & #40 です。SQLXML 4.0 & #41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md)|  
  
## <a name="guidelines-and-limitations"></a>ガイドラインと制限  
  
-   **\<xsd: 任意 >** 含む列にマップすることはできません、 **xml**データ型。 このシナリオは、によって提供される SQLXML でのサポート、 **sql:overflow-フィールド**注釈。 別の回避策は、マップする、 **xml**データ型のフィールドの要素として**xsd:anyType**です。 この方法は、上の表の例 "XML 要素を XML データ型の列にマップする" に示されています。  
  
-   XPath クエリの内容に**xml**データ型の列はサポートされていません。  
  
-   使用して、 **xml**サポートされていない注釈でのデータ型の列 (など**sql:relationship**と**sql:key-フィールド**) と、許可されているは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQLXML 4.0 を実装する中間層コンポーネントでトラップされませんはエラーです。 これは、SQLXML で SQL 型の情報が必要とされないためです。 この動作は、BLOB やバイナリ型などその他のデータ型に対する SQLXML の動作と同様です。  
  
-   マッピング**xml**列は XSD スキーマに対してのみサポートされます。 XDR スキーマはマッピングをサポートしていません**xml**列です。  
  
-   SQLXML 4.0 は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で提供される XML 解析サポートに依存しています。 **Xml**型指定された XML と型指定されていない XML か、列をマップすることができます。 どちらの場合も、SQLXML 4.0 で入力 XML は検証されません。  入力 XML が有効でないか、適切な形式でない場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から SQLXML にそのことがレポートされ、サーバーによって返された関連エラー情報がある場合はユーザーに伝達されます。  
  
-   SQLXML 4.0 は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で提供される DTD の制限付きサポートに依存しています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により、内部 DTD **xml**データ型のデータで、既定値を指定して、エンティティ参照に置き換えるの拡張コンテンツに使用することができます。 SQLXML では、サーバーに XML データが "そのまま" (内部 DTD を含めて) 渡されます。 ここで、サード パーティのツールを使用して DTD を XML スキーマ (XSD) ドキュメントに変換し、データをインライン XSD スキーマと共にデータベースに読み込むことができます。  
  
-   SQLXML 4.0 では保持されません XML 宣言の処理命令 (など) の動作に基づいて[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 代わりに、XML 宣言がするディレクティブとして扱われます、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML パーサーとその属性 (バージョン、エンコーディング、およびスタンドアロン) が失われるデータに変換されます、 **xml**データ型。 XML データは内部的に UCS-2 として保存されます。 XML インスタンスの場合は、他のすべての処理命令は保持されます。許可されているが、 **xml**列 SQLXML でサポートされていることができます。  
  
## <a name="see-also"></a>参照  
 [XML データ &#40;SQL Server&#41;](../../relational-databases/xml/xml-data-sql-server.md)  
  
  
