---
title: '[パブリッシャーのプロパティ - ディストリビューター] | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.rep.configdistwizard.distpubproperties.f1
helpviewer_keywords:
- Publisher Properties dialog box
ms.assetid: ab6ada76-0f99-43fe-b524-baac7b1bc483
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d6ed39a7bcfd48cbcaddbc0bfb90effd3b36d212
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="publisher-properties---distributor"></a>[パブリッシャーのプロパティ - ディストリビューター]
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **[パブリッシャーのプロパティ]** ダイアログ ボックスを使用すると、パブリッシャーとそのディストリビューター間のリレーションシップに関連するプロパティの表示と修正を行うことができます。  
  
## <a name="options"></a>および  
 **[パブリッシャーへのエージェント接続]**  
 次のエージェントがディストリビューターからパブリッシャーへの接続を確立するためのコンテキストを指定します。  
  
-   キュー リーダー エージェント (キュー更新サブスクリプションを許可するトランザクション パブリケーション用)  
  
-   スナップショット エージェントとログ リーダー エージェント (Oracle パブリケーション用)  
  
 **[エージェント プロセス アカウントを借用する]** を選択して、これらのエージェントを実行する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントのコンテキストを使用してパブリッシャーへの接続を作成するか、 **[SQL Server 認証]**を指定して、 **[ログイン]** と **[パスワード]**に値を入力します。 **[エージェント プロセス アカウントを借用する]**を選択することをお勧めします。 エージェントのセキュリティの詳細については、「[レプリケーション エージェントのセキュリティ モデル](../../relational-databases/replication/security/replication-agent-security-model.md)」を参照してください。  
  
 これらのエージェントを実行する Windows アカウントは、パブリケーションの新規作成ウィザードで指定します。 これらのアカウントは次のダイアログ ボックスで変更できます。  
  
-   **[ディストリビューターのプロパティ]** ダイアログ ボックス (キュー リーダー エージェント)  
  
-   **[パブリケーションのプロパティ]** ダイアログ ボックス (スナップショット エージェントとログ リーダー エージェント)  
  
 **その他**  
 **[パブリッシャーの種類]** プロパティと **[ディストリビューション データベース名]** プロパティは読み取り専用です。 **[既定のスナップショット フォルダー]** プロパティは変更できます。 スナップショット フォルダーの詳細については、「[スナップショット フォルダーのセキュリティ保護](../../relational-databases/replication/security/secure-the-snapshot-folder.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [View and Modify Distributor and Publisher Properties (ディストリビューターとパブリッシャーのプロパティの表示および変更)](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [プロパティ リファレンス &#40;レプリケーション&#41;](../../relational-databases/replication/properties-reference-replication.md)  
  
  
