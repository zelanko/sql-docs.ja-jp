---
title: "[サーバーへの接続] (Oracle)、[ログイン] | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.oracleconnection.login.f1"
helpviewer_keywords: 
  - "[サーバーへの接続] ダイアログ ボックス, レプリケーション"
ms.assetid: 86ed91a1-a07c-46f2-a913-67317ef2255e
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# [サーバーへの接続] (Oracle)、[ログイン]
  使用して、 **ログイン** のタブ、 **サーバーへの接続** からの接続が確立されるアカウントを指定する] ダイアログ ボックス、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle パブリッシャーにディストリビューターです。 パブリッシャーの構成時にレプリケーション管理ユーザー スキーマ用に指定したものと同じアカウントを使用する必要があります。 詳細については、次を参照してください。 [Oracle パブリッシャーを構成する](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)です。  
  
## オプション  
 **サーバー インスタンス**  
 ディストリビューターにインストールされた Oracle クライアント ソフトウェアの構成時に指定される、Oracle パブリッシャーの TNS (Transparent Network Substrate) 名です。  
  
 **[認証]**  
 選択 **Oracle 標準認証** (推奨) または **Windows 認証**します。 選択した場合 **Windows 認証**:  
  
-   Oracle サーバーは、Windows 資格情報を使用して接続を許可するように構成する必要があります。 詳細については Oracle のマニュアルを参照してください。  
  
-   現在、レプリケーション管理ユーザー スキーマ用に指定した [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントと同じものを使用してログインしている必要があります。  
  
 **ログイン** と **パスワード**  
 選択した場合は **Oracle 標準認証** の **認証** オプションで、ログインとレプリケーション管理ユーザー スキーマに指定するものと同じである必要がありますが、使用するパスワードを指定します。  
  
## 参照  
 [Oracle パブリッシングの用語](../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)  
  
  