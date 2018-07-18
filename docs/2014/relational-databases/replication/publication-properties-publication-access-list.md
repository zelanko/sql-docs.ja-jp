---
title: '[パブリケーションのプロパティ]、[パブリケーション アクセス リスト] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.pubproperties.publicationaccesslist.f1
ms.assetid: 9587bb9e-c66c-4e70-8171-09b943ec2d50
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: df9ebce6e148c90298f226dd2cb13ae27b98fe11
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37232945"
---
# <a name="publication-properties-publication-access-list"></a>[パブリケーションのプロパティ]、[パブリケーション アクセス リスト]
  **[パブリケーション プロパティ]** ダイアログ ボックスの **[パブリケーション アクセス リスト]** ページを使用すると、パブリケーション アクセス リスト (PAL) のログイン、アカウント、およびグループを追加したり削除したりできます。 PAL は、パブリッシャーの安全を確保する主要なメカニズムです。 パブリケーションを作成すると、レプリケーションによってそのパブリケーションから PAL が作成されます。 PAL の機能は [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のアクセス制御リストに似ており、PAL にはパブリケーションへのアクセスを許可されたログイン、アカウント、およびグループの一覧が含まれています。  
  
 サブスクライバーがパブリッシャーまたはディストリビューターに接続してパブリケーションへのアクセスを要求すると、サブスクライバーのログインが PAL 内の認証情報と比較されます。 これにより、クライアント ツールでパブリッシャーおよびディストリビューターのログインが使用されてパブリッシャーでの変更が直接実行されるのを防ぐことができ、パブリッシャーのセキュリティがさらに高まります。 詳細については、「[パブリッシャーのセキュリティ保護](security/secure-the-publisher.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[追加]**  
 一覧に新しいエントリを追加します。 追加できるのは、パブリッシャーとディストリビューターの両方で既に定義されているログイン、アカウント、またはグループの名前だけです。 ドメイン アカウントが使用されるか、ローカル アカウントが両方のサーバーで作成されている場合は、両方のサーバーで定義されています。  
  
 **[削除]**  
 選択されたエントリを一覧から削除します。  
  
 **[すべて削除]**  
 すべてのエントリを一覧から削除します。  
  
## <a name="see-also"></a>参照  
 [Create a Publication](publish/create-a-publication.md)   
 [パブリケーション プロパティの表示および変更](publish/view-and-modify-publication-properties.md)   
 [データとデータベース オブジェクトのパブリッシュ](publish/publish-data-and-database-objects.md)  
  
  
