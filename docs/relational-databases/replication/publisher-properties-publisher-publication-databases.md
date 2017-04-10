---
title: "[パブリッシャーのプロパティ - パブリッシャー]、[パブリケーション データベース] | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.configdistwizard.pubproperties.pubdb.f1"
helpviewer_keywords: 
  - "[パブリッシャーのプロパティ] ダイアログ ボックス"
ms.assetid: 574ea2e7-4e7b-4733-ab52-429ca93c7b0a
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# [パブリッシャーのプロパティ - パブリッシャー]、[パブリケーション データベース]
  **[パブリッシャーのプロパティ]** ダイアログ ボックスの **[パブリケーション データベース]** ページを使用すると、 **sysadmin** 固定サーバー ロール内のユーザーはデータベースをレプリケーションに対して有効にすることができます。 データベースを有効にするがそのデータベースは公開されません。任意のユーザーを代わりに、これにより、 **db_owner** データベースに 1 つまたは複数のパブリケーションを作成するには、そのデータベースの固定データベース ロール。  
  
## オプション  
 **トランザクション**  
 内のユーザーを許可するには、このチェック ボックスを選択して、 **db_owner** 固定データベース ロール、データベース内のスナップショット パブリケーションまたはトランザクション パブリケーションを作成します。  
  
 **Merge**  
 内のユーザーを許可するには、このチェック ボックスを選択して、 **db_owner** 固定データベース ロール、データベースにマージ パブリケーションを作成します。  
  
## 参照  
 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [プロパティのリファレンスと #40 です。レプリケーションと #41 です。](../../relational-databases/replication/properties-reference-replication.md)  
  
  