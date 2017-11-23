---
title: "アップデート グラムのセキュリティに関する注意点 (SQLXML 4.0) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
- SQLXML, updategrams
- security [SQLXML], updategrams
- updategrams [SQLXML], security
ms.assetid: 00dc6cf4-a2e8-4cca-bdd6-d5122102a82d
caps.latest.revision: "22"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3b6379e6407e8e2821ed34fc8f2137b9b1d170ee
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="updategram-security-considerations-sqlxml-40"></a>アップデートグラムのセキュリティに関する注意点 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]アップデート グラムを使用するためのセキュリティ ガイドラインを次に示します。  
  
-   アップデートグラムを使用してデータを更新する場合、既定のマッピングは使用しないでください。 既定のマッピングを使用すると、アップデートグラム内の要素名はテーブル名にマップされ、属性名は列にマップされます。 この方法では、データベース内のデータベース テーブルと列の情報が公開され、セキュリティが脅かされる可能性があります。 代わりに、独自のマッピング スキーマでアップデートグラムの要素および属性をデータベース テーブルおよび列にマップすれば、アップデートグラムの要素および属性には任意の名前を指定でき、スキーマによってこれらの名前のデータベース テーブルおよび列への必要なマッピングが行われます。 こうすると、アップデートグラムでデータベース情報は公開されません。  
  
-   アップデートグラムの作成と実行をユーザーに許可しないでください。 アップデートグラムはテンプレートとしてサーバーに置いておくことをお勧めします。ASP 型のアプリケーションでアップデートグラムを動的に作成すると、データベースのデータが保護されない危険性があります。 ユーザーには、アップデートグラムをテンプレートとして提供し、このアップデートグラム経由でのみデータへのアクセスを許可すれば、この危険を回避できます。  
  
## <a name="see-also"></a>参照  
 [SQLXML 4.0 でのアップデートグラムを使用したデータの変更](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/using-updategrams-to-modify-data-in-sqlxml-4-0.md)  
  
  
