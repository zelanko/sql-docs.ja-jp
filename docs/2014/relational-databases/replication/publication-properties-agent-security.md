---
title: '[パブリケーションのプロパティ]、[エージェント セキュリティ] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rep.newpubwizard.pubproperties.agentsecurity.f1
ms.assetid: 03945aac-66f2-4370-b5d1-c1de694bc4c1
caps.latest.revision: 20
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 2b72ec15e139ee164e74589ce70db4e193972ee0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174898"
---
# <a name="publication-properties-agent-security"></a>[パブリケーションのプロパティ]、[エージェント セキュリティ]
  **[パブリケーションのプロパティ]** ダイアログ ボックスの **[エージェント セキュリティ]** ページを使用すると、次のエージェントが実行されるアカウントの設定にアクセスし、レプリケーション トポロジのコンピューターへの接続を作成することができます。  
  
-   すべてのパブリケーションに対応する、スナップショット エージェント。  
  
-   すべてのトランザクション パブリケーションに対応する、ログ リーダー エージェント。 トランザクション レプリケーション用にパブリッシュされるデータベースには、それぞれ 1 つのログ リーダー エージェントがあります。 ログ リーダー エージェントの設定を変更すると、データベース内のすべてのトランザクション パブリケーションに影響します。  
  
-   キュー リーダー エージェント (キュー更新サブスクリプションを許可するトランザクション パブリケーション用) ディストリビューション データベースには、それぞれ 1 つのキュー リーダー エージェントがあります。 キュー リーダー エージェントの設定を変更すると、同じディストリビューション データベースを使用するキュー更新サブスクリプションを持つ、すべてのトランザクション パブリケーションに影響します。 キュー リーダー エージェントのセキュリティ設定の詳細については、「[レプリケーションのセキュリティ設定の表示および変更](security/view-and-modify-replication-security-settings.md)」を参照してください。  
  
 各エージェントに必要なセキュリティ設定および権限の詳細については、「 [Replication Agent Security Model](security/replication-agent-security-model.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[セキュリティ設定]** または **[エージェントの作成]**  
 エージェント ジョブが作成されている場合、 **[セキュリティ設定]** をクリックして、エージェントのセキュリティ設定を変更できるダイアログ ボックスにアクセスします。 エージェント ジョブが作成されていない場合、 **[エージェントの作成]** をクリックしてエージェントの作成とセキュリティ設定を指定します。  
  
## <a name="see-also"></a>参照  
 [Create a Publication](publish/create-a-publication.md)   
 [パブリケーション プロパティの表示および変更](publish/view-and-modify-publication-properties.md)   
 [データとデータベース オブジェクトのパブリッシュ](publish/publish-data-and-database-objects.md)   
 [Replication Security Best Practices](security/replication-security-best-practices.md)   
 [セキュリティと保護 &#40;レプリケーション&#41;](security/security-and-protection-replication.md)  
  
  