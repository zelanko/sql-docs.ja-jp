---
title: "ディストリビューターでのリモート パブリッシャーの有効化 (SQL Server Management Studio) | Microsoft Docs"
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
  - "リモート ディストリビューター [SQL Server レプリケーション]"
  - "パブリッシャー [SQL Server レプリケーション]"
ms.assetid: 6f8e2831-5c45-4e39-8e51-d37e2813cf3d
caps.latest.revision: 30
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 30
---
# ディストリビューターでのリモート パブリッシャーの有効化 (SQL Server Management Studio)
  **[パブリッシャー]** ページでパブリッシャーを有効にし、リモート ディストリビューターを使用します。 このページは、ディストリビューションの構成ウィザードで使用できる、 **ディストリビューターのプロパティ - \< ディストリビューター>** ] ダイアログ ボックス。 ウィザードを使用して、ダイアログ ボックスへのアクセスに関する詳細については、次を参照してください。 [パブリッシングとディストリビューション](../../relational-databases/replication/configure-publishing-and-distribution.md) と [表示と変更のディストリビューターとパブリッシャーのプロパティ](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)します。  
  
### ディストリビューションの構成ウィザードでパブリッシャーを有効にするには  
  
1.  ディストリビューションの構成ウィザードの **[パブリッシャー]** ページで、 **[追加]**をクリックします。  
  
2.  **[SQL Server パブリッシャーの追加]**をクリックします。 Oracle パブリッシャーを有効にしてディストリビューターを使用する方法については、「 [Create a Publication from an Oracle Database](../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md)」を参照してください。  
  
3.  **[サーバーへの接続]** ダイアログ ボックスで、リモート ディストリビューターを使用するパブリッシャーの接続情報を指定し、 **[接続]**をクリックします。  
  
4.   **ディストリビューター パスワード** ] ページで、 **パスワード** と **パスワードの確認入力** テキスト ボックスの強力なパスワードを指定する、 **distributor_admin** レプリケーションは、パブリッシャーから管理タスクを実行するためにディストリビューターへの接続を使用してアカウントです。  
  
5.  発行元の設定を表示および変更、プロパティ ボタンをクリックします (**...**)。  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### [ディストリビューターのプロパティ] ダイアログ ボックスでパブリッシャーを有効にするには  
  
1.   **パブリッシャー** のページ、 **ディストリビューターのプロパティ - \< ディストリビューター>** ダイアログ ボックスで、をクリックして **追加**します。  
  
2.  **[SQL Server パブリッシャーの追加]**をクリックします。 Oracle パブリッシャーを有効にしてディストリビューターを使用する方法については、「 [Create a Publication from an Oracle Database](../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md)」を参照してください。  
  
3.  **[サーバーへの接続]** ダイアログ ボックスで、リモート ディストリビューターを使用するパブリッシャーの接続情報を指定し、 **[接続]**をクリックします。  
  
4.   **パブリッシャー** ] ページで、 **パスワード** と **パスワードの確認入力** テキスト ボックスの強力なパスワードを指定する、 **distributor_admin** レプリケーションは、パブリッシャーから管理タスクを実行するためにディストリビューターへの接続を使用してアカウントです。  
  
5.  発行元の設定を表示および変更、プロパティ ボタンをクリックします (**...**)。  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## 参照  
 [Configure Publishing and Distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [ディストリビューションの構成](../../relational-databases/replication/configure-distribution.md)   
 [ディストリビューターのセキュリティ保護](../../relational-databases/replication/security/secure-the-distributor.md)  
  
  