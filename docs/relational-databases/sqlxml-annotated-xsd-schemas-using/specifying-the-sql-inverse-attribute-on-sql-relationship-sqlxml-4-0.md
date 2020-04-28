---
title: 'Sql: relationship (SQLXML) での sql: 逆属性の設定'
description: 'Sql: relationship 要素で sql: 逆属性を使用して、アップデートグラム操作でデータベース列間のリレーションシップを指定する方法について説明します。'
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:relationship
- bulk load [SQLXML]
- inverse attribute
- relationships [SQLXML], inverse orders
- relationship annotation
- XSD schemas [SQLXML], relationships
- annotated XSD schemas, relationships
- updategrams [SQLXML], relationships
- sql:inverse
ms.assetid: 08904cbd-9c86-493d-90c3-f5e1d13ce59d
author: MightyPen
ms.author: genemi
ms.reviewer: ''
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fe5409120a3d0c5df3cf05318b0b85fd22d07bdf
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81388096"
---
# <a name="specifying-the-sqlinverse-attribute-on-sqlrelationship-sqlxml-40"></a>sql:relationship での sql:inverse 属性の指定 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  **Sql: 逆**属性は、XSD スキーマが一括読み込みまたはアップデートグラムで使用されている場合にのみ役立ちます。 Sql:**逆**属性は、 ** \<sql: relationship>** 要素で指定できます。 アップデートグラムでは、アップデートグラム ロジックによってスキーマが解釈され、アップデートグラム操作で更新されるテーブルと列が決定されます。 また、スキーマで指定される親子リレーションシップによって、レコードが変更、挿入、または削除される順序が決定されます。  
  
 XSD スキーマを使用しており、そこで指定されている親子リレーションシップが、対応するデータベース列間の主キー/外部キー リレーションシップの逆順である場合は、アップデートグラムで挿入または削除操作を実行すると、主キー/外部キー違反で失敗します。 このような場合は、 **sql: relationship 属性が**指定されています (sql:**逆 = "true"**)、 ** \<sql: relationship>** 要素、アップデートグラムのロジック逆、スキーマで指定されている親子リレーションシップの解釈です。  
  
 **Sql: 逆**属性はブール値 (0 = false、1 = true) をとります。 指定できる値は 0、1、true、false です。  
  
 **Sql: 逆**注釈を使用した実際のサンプルについては、「[アップデートグラムでの注釈付きマッピングスキーマの指定](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Sql: relationship を使用したリレーションシップの指定 &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
  
  
