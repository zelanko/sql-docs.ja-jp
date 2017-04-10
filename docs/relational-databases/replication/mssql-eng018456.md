---
title: "MSSQL_ENG018456 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG018456 エラー"
ms.assetid: 3daa8144-d81f-445a-b6c3-4bb3e9fd1526
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# MSSQL_ENG018456
    
## メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|18456|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|ユーザーはログインできませんでした '. * ls'.%\*。%.*ls|  
  
## 説明  
 ログインの試行が失敗するたびに、エラー MSSQL_ENG018456 が発生します。 エラー メッセージには、アカウントが含まれている場合 **distributor_admin** (ユーザー ログインできませんでした 'distributor_admin' です。)、レプリケーションで使用されるアカウントで問題が発生します。 リモート サーバーを作成するレプリケーション **repl_distributor**, 、ディストリビューターとパブリッシャーの間の通信を許可します。 ログイン **distributor_admin** このリモート サーバーに関連付けられており、有効なパスワードを持つ必要があります。  
  
## ユーザーの操作  
 このアカウントに対するパスワードを指定したことを確認します。 詳細については、次を参照してください。 [ディストリビューターのセキュリティ保護](../../relational-databases/replication/security/secure-the-distributor.md)します。  
  
## 参照  
 [エラーとイベントのリファレンスと #40 です。レプリケーションと #41 です。](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  