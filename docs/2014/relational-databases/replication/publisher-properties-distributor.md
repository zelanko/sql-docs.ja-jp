---
title: '[パブリッシャーのプロパティ - ディストリビューター] | Microsoft Docs'
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
- sql12.rep.configdistwizard.distpubproperties.f1
helpviewer_keywords:
- Publisher Properties dialog box
ms.assetid: ab6ada76-0f99-43fe-b524-baac7b1bc483
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 721b2030285f50ca2f7a1212b8589ebcb05957cd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37164123"
---
# <a name="publisher-properties---distributor"></a>[パブリッシャーのプロパティ - ディストリビューター]
  **[パブリッシャーのプロパティ]** ダイアログ ボックスを使用すると、パブリッシャーとそのディストリビューター間のリレーションシップに関連するプロパティの表示と修正を行うことができます。  
  
## <a name="options"></a>および  
 **[パブリッシャーへのエージェント接続]**  
 次のエージェントがディストリビューターからパブリッシャーへの接続を確立するためのコンテキストを指定します。  
  
-   キュー リーダー エージェント (キュー更新サブスクリプションを許可するトランザクション パブリケーション用)  
  
-   スナップショット エージェントとログ リーダー エージェント (Oracle パブリケーション用)  
  
 **[エージェント プロセス アカウントを借用する]** を選択して、これらのエージェントを実行する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントのコンテキストを使用してパブリッシャーへの接続を作成するか、 **[SQL Server 認証]** を指定して、 **[ログイン]** と **[パスワード]** に値を入力します。 **[エージェント プロセス アカウントを借用する]** を選択することをお勧めします。 エージェントのセキュリティの詳細については、「[レプリケーション エージェントのセキュリティ モデル](security/replication-agent-security-model.md)」を参照してください。  
  
 これらのエージェントを実行する Windows アカウントは、パブリケーションの新規作成ウィザードで指定します。 これらのアカウントは次のダイアログ ボックスで変更できます。  
  
-   **[ディストリビューターのプロパティ]** ダイアログ ボックス (キュー リーダー エージェント)  
  
-   **[パブリケーションのプロパティ]** ダイアログ ボックス (スナップショット エージェントとログ リーダー エージェント)  
  
 **その他**  
 **[パブリッシャーの種類]** プロパティと **[ディストリビューション データベース名]** プロパティは読み取り専用です。 **[既定のスナップショット フォルダー]** プロパティは変更できます。 スナップショット フォルダーの詳細については、「[スナップショット フォルダーのセキュリティ保護](security/secure-the-snapshot-folder.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Create a Publication](publish/create-a-publication.md)   
 [View and Modify Distributor and Publisher Properties (ディストリビューターとパブリッシャーのプロパティの表示および変更)](view-and-modify-distributor-and-publisher-properties.md)   
 [プロパティ リファレンス &#40;レプリケーション&#41;](properties-reference-replication.md)  
  
  
