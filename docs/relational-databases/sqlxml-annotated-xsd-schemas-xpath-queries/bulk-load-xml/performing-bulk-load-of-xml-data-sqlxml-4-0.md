---
title: XML データ (SQLXML 4.0) の一括読み込みを実行する |Microsoft ドキュメント
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
- XML Bulk Load [SQLXML]
- bulk load [SQLXML]
- data insertions [SQLXML]
- SQLXML, bulk loading
- XSD schemas [SQLXML], XML Bulk Load
- XDR schemas [SQLXML], XML Bulk Load
- inserting data
ms.assetid: 3708b493-322e-4f3c-9b27-441d0c0ee346
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c4087c97debb92415c9a4e72a4fc29ffeaf81713
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34708180"
---
# <a name="performing-bulk-load-of-xml-data-sqlxml-40"></a>XML データの一括読み込みの実行 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  XML 一括読み込みはスタンドアロン COM オブジェクトであり、これを使用すると、半構造化された XML データを Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] テーブルに読み込むことができます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [XML 一括読み込みの概要&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/introduction-to-xml-bulk-load-sqlxml-4-0.md)  
 XML 一括読み込みユーティリティで XML データの一括読み込みを実行する際の一般的な情報を提供します。 たとえば、XML データ ストリーミングや、トランザクション モードとトランザクション以外のモードでの一括読み込み操作について説明します。  
  
 [レコード生成処理&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/record-generation-process-sqlxml-4-0.md)  
 XML 一括読み込みのレコードが生成されるプロセスと規則について説明します。  
  
 [注釈の解釈&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sqlxml-4-0.md)  
 XML 一括読み込みで XSD および XDR スキーマ内の注釈がどのように解釈されるかについて説明します。  
  
 [SQL Server XML 一括読み込みオブジェクト モデル&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/sql-server-xml-bulk-load-object-model-sqlxml-4-0.md)  
 SQLXMLBulkLoad オブジェクトとそのメソッドおよびプロパティについて説明します。  
  
 [XML 一括読み込みの例&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md)  
 XML 一括読み込みを使用したコードの例を提供します。  
  
 [データ型と XML 一括読み込み動作&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/data-types-and-xml-bulk-load-behavior-sqlxml-4-0.md)  
 XSD と XDR での、さまざまな XML 一括読み込み動作について説明します。  
  
 [XML のガイドラインと制限、一括読み込み&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/guidelines-and-limitations-of-xml-bulk-load-sqlxml-4-0.md)  
 XML 一括読み込みを扱うときに注意すべき問題をいくつか示します。  
  
  
