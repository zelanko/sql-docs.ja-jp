---
title: DDL トリガーに関する情報の取得 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-ddl
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- metadata [SQL Server], triggers
- status information [SQL Server], DDL triggers
- DDL triggers, metadata
ms.assetid: 462becea-292a-4b9e-bb98-533e89733911
caps.latest.revision: 30
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ca1babc45b048802e76bc6aca6290ec4de08eeee
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083599"
---
# <a name="get-information-about-ddl-triggers"></a>DDL トリガーに関する情報の取得
  ここに記載されているカタログ ビューを使用すると、DDL トリガーに関する情報を取得できます。  
  
 **DDL トリガーを起動できるイベントまたはイベント グループに関する情報を取得するには**  
  
-   [sys.trigger_event_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-event-types-transact-sql)  
  
 **トリガーの依存関係を表示するには**  
  
-   [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
-   [sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)  
  
-   [sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql)  
  
## <a name="database-scoped-ddl-triggers"></a>データベース スコープの DDL トリガー  
 **データベース スコープのトリガーに関する情報を取得するには**  
  
-   [sys.triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql)  
  
 **トリガーを起動するデータベース イベントに関する情報を取得するには**  
  
-   [sys.trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql)  
  
 **データベース スコープのトリガーの定義を表示するには**  
  
-   [sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)  
  
 **データベース スコープの CLR トリガーに関する情報を取得するには**  
  
-   [sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql)  
  
## <a name="server-scoped-ddl-triggers"></a>サーバー スコープの DDL トリガー  
 **サーバー スコープのトリガーに関する情報を取得するには**  
  
-   [sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql)  
  
 **トリガーを起動するサーバー イベントに関する情報を取得するには**  
  
-   [sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql)  
  
 **サーバー スコープのトリガーの定義を表示するには**  
  
-   [sys.server_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql)  
  
 **サーバー スコープの CLR トリガーに関する情報を取得するには**  
  
-   [sys.server_assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql)  
  
## <a name="see-also"></a>参照  
 [DDL トリガー](../triggers/ddl-triggers.md)  
  
  
