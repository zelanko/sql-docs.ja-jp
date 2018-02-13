---
title: "SQLXML 4.0 でのデータを変更するアップデート グラムの使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQLXML, updategrams
- data insertions [SQLXML]
- data deletions [SQLXML]
- updating data [SQLXML]
- modifying data [SQLXML]
- OPENXML function
- updategrams [SQLXML]
- database modifications [SQLXML]
- data updates [SQLXML]
- modifying databases
- data modifications [SQLXML]
- deleting data
- inserting data
ms.assetid: b8b3b892-cb73-41d0-b945-bce148d81d9b
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8d34964877464c7520f56fff59e3e2c232d27545
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="using-updategrams-to-modify-data-in-sqlxml-40"></a>SQLXML 4.0 での、アップデートグラムを使用したデータ変更
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
変更することができます (挿入、更新、または削除) のデータベースに[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]アップデート グラムまたは OPENXML を使用してドキュメントの既存の XML から[!INCLUDE[tsql](../../../includes/tsql-md.md)]関数。  
  
 ここでは、アップデートグラムについての情報と、その使用例を示します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [アップデート グラム &#40; の概要SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/introduction-to-updategrams-sqlxml-4-0.md)  
 アップデートグラムについての基本情報と使用例を示します。  
  
 [アップデート グラム &#40; で、注釈付きマッピング スキーマの指定SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)  
 アップデートグラムの注釈付きマッピング スキーマについて説明し、使用例を示します。  
  
 [NULL の処理 &#40;です。SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/null-handling-sqlxml-4-0.md)  
 要素値と属性値に NULL を指定する方法について説明します。  
  
 [XML アップデート グラム &#40; を使用してデータを挿入します。SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)  
 アップデートグラムを使用したデータの挿入について説明し、例を示します。  
  
 [XML アップデート グラム &#40; を使用してデータを削除します。SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/deleting-data-using-xml-updategrams-sqlxml-4-0.md)  
 アップデートグラムを使用したデータの削除について説明し、例を示します。  
  
 [XML アップデート グラム &#40; を使用してデータの更新SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/updating-data-using-xml-updategrams-sqlxml-4-0.md)  
 アップデートグラムを使用した既存データの変更について説明し、例を示します。  
  
 [アップデート グラム &#40; へのパラメーターの引き渡しSQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/passing-parameters-to-updategrams-sqlxml-4-0.md)  
 アップデートグラムへのパラメーターの引き渡しについて説明し、例を示します。  
  
 [アップデート グラムでデータベースの同時実行の問題 &#40; の処理SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/handling-database-concurrency-issues-in-updategrams-sqlxml-4-0.md)  
 アップデートグラムでの同時実行の問題に対応するために可能なさまざまなレベルの保護について説明し、例を示します。  
  
 [アップデート グラムのサンプル アプリケーション &#40;です。SQLXML 4.0 &#41;](http://msdn.microsoft.com/library/d2287e10-4007-4ba4-ad84-4e2b6adfede5)  
 アップデートグラムを使用したサンプル アプリケーションを提供します。  
  
 [XML アップデート グラム &#40; のガイドラインと制限SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/guidelines-and-limitations-of-xml-updategrams-sqlxml-4-0.md)  
 アップデートグラムを使用する場合の注意点をいくつか挙げます。  
  
  
