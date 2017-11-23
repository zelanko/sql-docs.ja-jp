---
title: "キャッシュ テンプレート、XSL、およびスキーマ (SQLXML 4.0) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQLXML, caching
- cache [SQLXML]
- memory [SQLXML]
ms.assetid: 80b4fa79-243f-442c-9f22-74ad66186501
caps.latest.revision: "25"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ff7cd22dbe87f5fc73a99c13d8b8761dc8cc456d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="caching-templates-xsl-and-schemas-sqlxml-40"></a>テンプレート、XSL、およびスキーマのキャッシュ (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]パフォーマンスを向上させるために[!INCLUDE[msCoName](../../../includes/msconame-md.md)]SQLXML 4.0 には、テンプレート、XSL、およびスキーマのキャッシュがサポートしています。  
  
 SQLXML 4.0 ではすべてのスキーマとテンプレート、および (http:// または ftp:// にあるファイルを除く) XSL ファイルをキャッシュでき、 キャッシュされたファイルは処理が実行されている間メモリに残ります。 処理が終了すると、すべてのキャッシュは失われます。 したがって、クエリごとに 1 つの処理を実行する場合は、キャッシュがそれほどメリットにならない場合もあります。  
  
 ここでは、キャッシュの詳細について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [テンプレートのキャッシュ (&) #40 です。SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/template-caching-sqlxml-4-0.md)  
 テンプレートのキャッシュ用のレジストリ キーについて説明します。  
  
 [XSL のキャッシュ (&) #40 です。SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/xsl-caching-sqlxml-4-0.md)  
 XSL のキャッシュ用のレジストリ キーについて説明します。  
  
 [スキーマのキャッシュ (&) #40 です。SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/schema-caching-sqlxml-4-0.md)  
 スキーマのキャッシュに関する SQLXML サイド バイ サイド インストールについて説明し、スキーマのキャッシュ用のレジストリ キーを提供します。  
  
  
