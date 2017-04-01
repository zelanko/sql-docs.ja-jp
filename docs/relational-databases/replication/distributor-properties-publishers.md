---
title: "[ディストリビューターのプロパティ]、[パブリッシャー] | Microsoft Docs"
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
  - "sql13.rep.configdistwizard.distproperties.publishers.f1"
helpviewer_keywords: 
  - "[ディストリビューターのプロパティ] ダイアログ ボックス"
ms.assetid: 31c81898-11ca-4d2f-afea-2fbc71e19ce4
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# [ディストリビューターのプロパティ]、[パブリッシャー]
  **[ディストリビューターのプロパティ]** ダイアログ ボックスの **[パブリッシャー]** ページを使用すると、パブリッシャーでこのディストリビューターを使用できるように設定できます。 さらに、このパブリッシャーに関連付けられているプロパティも設定できます。 パブリッシャーがサーバーをパブリッシャーのリモート ディストリビューターとして使用しても、そのサーバーがパブリッシャーにならないことに注意してください。 パブリッシャーに接続し、パブリッシュするための構成を行って、このサーバーをディストリビューターとして選択する必要があります。 パブリケーションの新規作成ウィザードを使用して、パブリッシャーを構成し、ディストリビューターを選択できます。  
  
## オプション  
 **パブリッシャー**  
 このディストリビューターの使用を許可するサーバーを選択します。 [プロパティ] ボタンをクリックして **(...)** 表示し、追加のプロパティを設定するパブリッシャーの横にあります。  
  
 **[追加]**  
 許可するサーバーが表示されない場合クリックして **追加** を追加する、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャーまたは Oracle パブリッシャーを使用可能なパブリッシャーの一覧です。 追加したサーバーが、最初にこのディストリビューターをリモート ディストリビューターとして使用するサーバーである場合、管理用リンク パスワードを入力するように求められます。  
  
 **[管理用リンク パスワード]**  
 指定または接続のレプリケーションのパスワードは、パブリッシャーとリモート ディストリビューターを使用して、間、更新、 **distributor_admin** ログインします。  
  
-   ディストリビューターがローカル ディストリビューターとしてのみ動作する場合、このパスワードはランダムに生成され、自動的に設定されます。  
  
-   既にディストリビューターにリモート パブリッシャーがある場合、パスワードはディストリビューションの構成ウィザードのこのページまたは **[ディストリビューター パスワード]** ページで最初に指定されています。  
  
-   このディストリビューターの最初のリモート パブリッシャーを有効にすると、パスワードを入力するように求められます。  
  
 ディストリビューターのセキュリティの詳細については、次を参照してください。 [ディストリビューターのセキュリティ保護](../../relational-databases/replication/security/secure-the-distributor.md)します。  
  
## 参照  
 [ディストリビューションの構成](../../relational-databases/replication/configure-distribution.md)   
 [Configure Publishing and Distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)  
  
  