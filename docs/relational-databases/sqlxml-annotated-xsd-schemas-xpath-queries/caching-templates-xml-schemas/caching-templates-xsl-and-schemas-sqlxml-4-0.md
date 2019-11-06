---
title: テンプレート、XSL、およびスキーマ (SQLXML 4.0) をキャッシュします。マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, caching
- cache [SQLXML]
- memory [SQLXML]
ms.assetid: 80b4fa79-243f-442c-9f22-74ad66186501
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ab740322ff0cf8847e12905cd0545667e7ae6f9b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68001354"
---
# <a name="caching-templates-xsl-and-schemas-sqlxml-40"></a>テンプレート、XSL、およびスキーマのキャッシュ (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  パフォーマンス向上のため、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 ではテンプレート、XSL、およびスキーマのキャッシュがサポートされています。  
  
 すべてのスキーマ、テンプレート、および XSL ファイル (https:// または ftp からファイルを除く://場所) が実行されます。 キャッシュされたファイルは処理が実行されている間メモリに残ります。 処理が終了すると、すべてのキャッシュは失われます。 したがって、クエリごとに 1 つの処理を実行する場合は、キャッシュがそれほどメリットにならない場合もあります。  
  
 ここでは、キャッシュの詳細について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [テンプレートのキャッシュ&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/template-caching-sqlxml-4-0.md)  
 テンプレートのキャッシュ用のレジストリ キーについて説明します。  
  
 [XSL のキャッシュ&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/xsl-caching-sqlxml-4-0.md)  
 XSL のキャッシュ用のレジストリ キーについて説明します。  
  
 [スキーマ キャッシュ&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/schema-caching-sqlxml-4-0.md)  
 スキーマのキャッシュに関する SQLXML サイド バイ サイド インストールについて説明し、スキーマのキャッシュ用のレジストリ キーを提供します。  
  
  
