---
title: テンプレート、XSL、およびスキーマ (SQLXML 4.0) をキャッシュします。マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, caching
- cache [SQLXML]
- memory [SQLXML]
ms.assetid: 80b4fa79-243f-442c-9f22-74ad66186501
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 86777a00c7382ce9a1b8d67f06a6cd222f983a11
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62856533"
---
# <a name="caching-templates-xsl-and-schemas-sqlxml-40"></a>テンプレート、XSL、およびスキーマのキャッシュ (SQLXML 4.0)
  パフォーマンス向上のため、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 ではテンプレート、XSL、およびスキーマのキャッシュがサポートされています。  
  
 SQLXML 4.0 ではすべてのスキーマとテンプレート、および (http:// または ftp:// にあるファイルを除く) XSL ファイルをキャッシュでき、 キャッシュされたファイルは処理が実行されている間メモリに残ります。 処理が終了すると、すべてのキャッシュは失われます。 したがって、クエリごとに 1 つの処理を実行する場合は、キャッシュがそれほどメリットにならない場合もあります。  
  
 ここでは、キャッシュの詳細について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [テンプレートのキャッシュ&#40;SQLXML 4.0&#41;](template-caching-sqlxml-4-0.md)  
 テンプレートのキャッシュ用のレジストリ キーについて説明します。  
  
 [XSL のキャッシュ&#40;SQLXML 4.0&#41;](xsl-caching-sqlxml-4-0.md)  
 XSL のキャッシュ用のレジストリ キーについて説明します。  
  
 [スキーマ キャッシュ&#40;SQLXML 4.0&#41;](schema-caching-sqlxml-4-0.md)  
 スキーマのキャッシュに関する SQLXML サイド バイ サイド インストールについて説明し、スキーマのキャッシュ用のレジストリ キーを提供します。  
  
  
