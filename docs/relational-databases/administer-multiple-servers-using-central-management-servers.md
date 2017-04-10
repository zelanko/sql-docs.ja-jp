---
title: "中央管理サーバーを使用した複数のサーバーの管理 | Microsoft Docs"
ms.custom: ""
ms.date: "08/12/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "マルチサーバー クエリ"
  - "中央管理サーバー"
  - "マルチサーバー管理 [SQL Server]"
  - "マスター サーバー [SQL Server], 中央管理サーバー"
  - "対象構成 [SQL Server]"
  - "サーバー構成 [SQL Server]"
ms.assetid: 427911a7-57d4-4542-8846-47c3267a5d9c
caps.latest.revision: 27
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 27
---
# 中央管理サーバーを使用した複数のサーバーの管理
  中央管理サーバーを指定し、サーバー グループを作成することで、複数のサーバーを管理できます。  
  
## 中央管理サーバーおよびサーバー グループとは  
 中央管理サーバーとして指定した SQL Server のインスタンスは、1 つ以上のインスタンスの接続情報を含むサーバー グループを管理します。 [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントおよびポリシー ベースの管理ポリシーをサーバー グループに対して同時に実行できます。 中央管理サーバーを通じて管理されているインスタンスのログ ファイルを表示することもできます。 
 
 基本的に、中央管理サーバーは管理対象サーバーのリストが含まれる中央リポジトリです。 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] より前のバージョンでは、中央管理サーバーを指定できません。  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントは、登録済みサーバー内のローカル サーバー グループに対しても実行できます。  
  
## 中央管理サーバーおよびサーバー グループを作成する 
 中央管理サーバーとサーバー グループを作成するには、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] の **[登録済みサーバー]** ウィンドウを使用します。 中央管理サーバーを、それ自体が管理するグループのメンバーにすることはできません。 
 
 中央管理サーバーとサーバー グループの作成方法については、「[中央管理サーバーおよびサーバー グループの作成 &#40;SQL Server Management Studio&#41;](../tools/sql-server-management-studio/create-a-central-management-server-and-server-group.md)」をご覧ください。  
  
## 参照  
 [ポリシー ベースの管理を使用したサーバーの管理](../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  