---
title: "資格情報 (データベース エンジン) | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プリンシパル [SQL Server], 資格情報"
  - "スキーマ [SQL Server], 資格情報"
  - "アクセス許可 [SQL Server], 資格情報"
  - "グループ [SQL Server], 資格情報"
  - "ALTER ANY CREDENTIAL 権限"
  - "セキュリティ [SQL Server], 資格情報"
  - "資格情報の認証 [SQL Server]"
  - "ユーザー [SQL Server], 資格情報"
  - "資格情報 [SQL Server], 資格情報について"
  - "資格情報 [SQL Server]"
ms.assetid: c8df6022-e0b4-46b8-9670-3f86938d3177
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 30
---
# 資格情報 (データベース エンジン)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../../includes/tsql-appliesto-ss2008-all-md.md)]

  資格情報は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 外部のリソースへの接続に必要な認証情報 (資格情報) を含むレコードです。 この情報は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] によって内部的に使用されます。 通常、資格情報には Windows ユーザー名とパスワードが含まれます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証経由で接続しているユーザーは、資格情報に格納された情報によって、サーバー インスタンスの外部のリソースにアクセスできるようになります。 外部リソースが Windows である場合、ユーザーは、資格情報に指定されている Windows ユーザーとして認証されます。 1 つの資格情報を複数の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインにマッピングすることもできます。 ただし、1 つの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインは 1 つの資格情報にしかマップできません。  
  
 マスター データベースに保存され、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンス全体で使用できる資格情報については、「[CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../../t-sql/statements/create-credential-transact-sql.md)」を参照してください。 特定のデータベースで使用され、そのデータベースとともに移植可能な資格情報については、「[CREATE DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../../t-sql/statements/create-database-scoped-credential-transact-sql.md)」を参照してください。  
  
 システム資格情報は、自動的に作成され、特定のエンドポイントに関連付けられます。 システム資格情報の名前は 2 つのシャープ記号 (##) で始まります。  
  
 資格情報の詳細については、[sys.credentials](../../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md) カタログ ビューおよび [sys.database_credentials &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-database-credentials-transact-sql.md) カタログ ビューを参照してください。  
  
## 関連コンテンツ  
 [資格情報の作成](../../../relational-databases/security/authentication-access/create-a-credential.md) [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../../t-sql/statements/create-credential-transact-sql.md) [CREATE DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../../t-sql/statements/create-database-scoped-credential-transact-sql.md)  
  
 [SQL Server の保護](../../../relational-databases/security/securing-sql-server.md)  
  
  