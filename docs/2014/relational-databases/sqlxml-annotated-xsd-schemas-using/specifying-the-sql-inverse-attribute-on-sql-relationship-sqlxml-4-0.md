---
title: 'Sql: relationship での sql: 逆属性の指定 (SQLXML 4.0) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 90c2b7836de03369c09d68181fd1cb61b355107b
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82703479"
---
# <a name="specifying-the-sqlinverse-attribute-on-sqlrelationship-sqlxml-40"></a>sql:relationship での sql:inverse 属性の指定 (SQLXML 4.0)
  `sql:inverse` 属性は、一括読み込みまたはアップデートグラムで XSD スキーマが使用される場合にのみ便利です。 この `sql:inverse` 属性は、 ** \< sql: relationship>** 要素で指定できます。 アップデートグラムでは、アップデートグラム ロジックによってスキーマが解釈され、アップデートグラム操作で更新されるテーブルと列が決定されます。 また、スキーマで指定される親子リレーションシップによって、レコードが変更、挿入、または削除される順序が決定されます。  
  
 XSD スキーマを使用しており、そこで指定されている親子リレーションシップが、対応するデータベース列間の主キー/外部キー リレーションシップの逆順である場合は、アップデートグラムで挿入または削除操作を実行すると、主キー/外部キー違反で失敗します。 このような場合、 `sql:inverse` `sql:inverse="true"` ** \< sql: relationship>** 要素で属性が指定されています。また、アップデートグラムのロジック逆は、スキーマで指定されている親子リレーションシップの解釈を指定します。  
  
 `sql:inverse` 属性はブール値 (0 = false、1=true) をとります。 指定できる値は 0、1、true、false です。  
  
 注釈を使用した実際のサンプルについ `sql:inverse` ては、「[アップデートグラムでの注釈付きマッピングスキーマの指定](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Sql: relationship を使用したリレーションシップの指定 &#40;SQLXML 4.0&#41;](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
  
  
