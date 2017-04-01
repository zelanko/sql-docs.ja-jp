---
title: "Oracle パブリッシャー | Microsoft Docs"
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
  - "sql13.rep.newpubwizard.selectoraclepublisher.f1"
ms.assetid: 019b7c49-dcca-445d-8969-5982a8ccbc1a
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# Oracle パブリッシャー
  始まる [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], 、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スナップショットおよびトランザクション レプリケーションを使用して Oracle データベースからデータをパブリッシュすることができます。 詳細については、次を参照してください。 [発行の概要は Oracle](../../relational-databases/replication/non-sql/oracle-publishing-overview.md)します。  
  
 Oracle パブリッシャーでは、リモート [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ディストリビューターを使用する必要があります。そのため、このウィザードは、必要な Oracle ネットワーク ソフトウェアのインストールとテストが行われた後のサーバーで実行する必要があります。 詳細については、次を参照してください。 [Oracle パブリッシャーを構成する](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)です。  
  
> [!IMPORTANT]  
>  別の管理者をクリックすると、パブリッシャーとして Oracle データベースを構成かどうか **次** Oracle データベースへの接続に使用されるレプリケーション ログインのパスワードを入力するように求められます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 現在のログインと Oracle データベースへのリンク サーバー接続間のマッピングを作成します。 以降の Oracle データベースへの接続にパスワードの入力が求められることはありません。  
  
## オプション  
 **Oracle パブリッシャー**  
 一覧から Oracle パブリッシャーを選択します。 この一覧には、ウィザードがディストリビューターとして実行されているサーバーを使用するように、以前に構成されたことのある Oracle パブリッシャーが表示されます。 リストが空か、Oracle パブリッシャーする場合をクリックして使用が一覧にない **[Oracle パブリッシャーの**です。  
  
 **[Oracle パブリッシャーの追加]**  
 クリックする、 **ディストリビューターのプロパティ** ] ダイアログ ボックス。 このダイアログ ボックスで、クリックして **追加**, 、] をクリックし、 **[Oracle パブリッシャーの**です。  **サーバーへの接続** ] ダイアログ ボックスで、Oracle サーバー名、およびログインとレプリケーション管理ユーザー スキーマ用のパスワードを指定します。 詳細については、次を参照してください。 [サーバー & #40";"Oracle"&"#41 への接続、; ログイン](../../relational-databases/replication/connect-to-server-oracle-login.md)します。  
  
> [!NOTE]  
>  このウィザードが実行されているサーバーがディストリビューターとしてまだ構成されていない場合、ディストリビューターを構成するように要求されます。  
  
## 参照  
 [Create a Publication from an Oracle Database](../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md)   
 [プロパティのリファレンスと #40 です。レプリケーションと #41 です。](../../relational-databases/replication/properties-reference-replication.md)  
  
  