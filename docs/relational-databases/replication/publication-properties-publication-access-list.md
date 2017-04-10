---
title: "[パブリケーションのプロパティ]、[パブリケーション アクセス リスト] | Microsoft Docs"
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
  - "sql13.rep.newpubwizard.pubproperties.publicationaccesslist.f1"
ms.assetid: 9587bb9e-c66c-4e70-8171-09b943ec2d50
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# [パブリケーションのプロパティ]、[パブリケーション アクセス リスト]
   **パブリケーション アクセス リスト** のページ、 **パブリケーションのプロパティ** ダイアログ ボックスでは、追加およびパブリケーション アクセス リスト (PAL) からのログイン、アカウント、およびグループを削除することができます。 PAL は、パブリッシャーの安全を確保する主要なメカニズムです。 パブリケーションを作成すると、レプリケーションによってそのパブリケーションから PAL が作成されます。 PAL の機能は [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のアクセス制御リストに似ており、PAL にはパブリケーションへのアクセスを許可されたログイン、アカウント、およびグループの一覧が含まれています。  
  
 サブスクライバーがパブリッシャーまたはディストリビューターに接続してパブリケーションへのアクセスを要求すると、サブスクライバーのログインが PAL 内の認証情報と比較されます。 これにより、クライアント ツールでパブリッシャーおよびディストリビューターのログインが使用されてパブリッシャーでの変更が直接実行されるのを防ぐことができ、パブリッシャーのセキュリティがさらに高まります。 詳細については、次を参照してください。 [パブリッシャーのセキュリティ保護](../../relational-databases/replication/security/secure-the-publisher.md)します。  
  
## オプション  
 **[追加]**  
 一覧に新しいエントリを追加します。 追加できるのは、パブリッシャーとディストリビューターの両方で既に定義されているログイン、アカウント、またはグループの名前だけです。 ドメイン アカウントが使用されるか、ローカル アカウントが両方のサーバーで作成されている場合は、両方のサーバーで定義されています。  
  
 **[削除]**  
 選択されたエントリを一覧から削除します。  
  
 **[すべて削除]**  
 すべてのエントリを一覧から削除します。  
  
## 参照  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [パブリケーション プロパティの表示および変更](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  