---
title: '[パブリケーションのプロパティ]、[パブリケーション アクセス リスト] | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.newpubwizard.pubproperties.publicationaccesslist.f1
ms.assetid: 9587bb9e-c66c-4e70-8171-09b943ec2d50
caps.latest.revision: 20
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f84b32e2d1a96d0416f1f5b8d6a73580a76af4ba
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="publication-properties-publication-access-list"></a>[パブリケーションのプロパティ]、[パブリケーション アクセス リスト]
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **[パブリケーション プロパティ]** ダイアログ ボックスの **[パブリケーション アクセス リスト]** ページを使用すると、パブリケーション アクセス リスト (PAL) のログイン、アカウント、およびグループを追加したり削除したりできます。 PAL は、パブリッシャーの安全を確保する主要なメカニズムです。 パブリケーションを作成すると、レプリケーションによってそのパブリケーションから PAL が作成されます。 PAL の機能は [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のアクセス制御リストに似ており、PAL にはパブリケーションへのアクセスを許可されたログイン、アカウント、およびグループの一覧が含まれています。  
  
 サブスクライバーがパブリッシャーまたはディストリビューターに接続してパブリケーションへのアクセスを要求すると、サブスクライバーのログインが PAL 内の認証情報と比較されます。 これにより、クライアント ツールでパブリッシャーおよびディストリビューターのログインが使用されてパブリッシャーでの変更が直接実行されるのを防ぐことができ、パブリッシャーのセキュリティがさらに高まります。 詳細については、「[パブリッシャーのセキュリティ保護](../../relational-databases/replication/security/secure-the-publisher.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[追加]**  
 一覧に新しいエントリを追加します。 追加できるのは、パブリッシャーとディストリビューターの両方で既に定義されているログイン、アカウント、またはグループの名前だけです。 ドメイン アカウントが使用されるか、ローカル アカウントが両方のサーバーで作成されている場合は、両方のサーバーで定義されています。  
  
 **[削除]**  
 選択されたエントリを一覧から削除します。  
  
 **[すべて削除]**  
 すべてのエントリを一覧から削除します。  
  
## <a name="see-also"></a>参照  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [パブリケーション プロパティの表示および変更](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
