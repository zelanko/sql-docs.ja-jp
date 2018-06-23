---
title: '[ディストリビューション エージェント セキュリティ] (ピア ツー ピア レプリケーション) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rep.p2pwizard.DA.f1
ms.assetid: def6bf26-c640-4caf-ad30-05d1e649541d
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 9a1f52e7fba90bcc03da9ca2f135be41013a29fb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174126"
---
# <a name="distribution-agent-security-peer-to-peer-replication"></a>[ディストリビューション エージェント セキュリティ] \(ピア ツー ピア レプリケーション)
  **[ディストリビューション エージェント セキュリティ]** ページを使用すると、ディストリビューション エージェントを実行するアカウントの指定と、ピア ツー ピア テクノロジによるコンピューターへの接続の作成ができます。 エージェントで必要とされる権限と、レプリケーション セキュリティの推奨事項については、「[レプリケーション エージェントのセキュリティ モデル](security/replication-agent-security-model.md)」と「[レプリケーション セキュリティの推奨事項](security/replication-security-best-practices.md)」を参照してください。  
  
> [!NOTE]  
>  サブスクリプションのディストリビューション エージェントが、このウィザードの以前の実行で既に構成されている場合、使用される資格情報をこのウィザードで変更することはできません。 新しい資格情報を指定した場合は無視されます。 資格情報を変更するには、 **[サブスクリプションのプロパティ]** ダイアログ ボックスを使用します。 詳細については、「 [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[ディストリビューション エージェント セキュリティ]** ダイアログ ボックスにアクセスするには、各サブスクライバーの行でプロパティ ボタン ( **[...]** ) をクリックします。 **[ディストリビューション エージェント セキュリティ]** ダイアログ ボックスの **[ヘルプ]** をクリックすると、エージェントによって使用されるアカウントに必要な権限の詳細を参照できます。  
  
 ダイアログ ボックスの 1 つに設定を入力すると、サブスクライバーの接続情報がグリッドに表示されます。  
  
 **[サブスクライバーのエージェント]**  
 各ピアの名前です。  
  
 **[ピア データベース]**  
 パブリケーション データ ベースとサブスクリプション データベースの両方に使用できるピアのデータベースです。  
  
 **[ディストリビューターへの接続]**  
 ディストリビューターに接続するコンテキストを作成します。 ローカル接続は常に、エージェントを実行する Windows アカウントのコンテキストを使用して作成されます。 このウィザードではプッシュ サブスクリプションが作成されるため (ローカル接続はディストリビューターへの接続)、フィールドには常に **['\<Domain>\\<Login\>' の権限を借用する]** または **['\<Computer>\\<Login\>' の権限を借用する]** が表示されます。  
  
 **[サブスクライバーへの接続]**  
 サブスクライバーに接続するコンテキストを作成します。 接続は、エージェントが実行する Windows アカウントのコンテキストの使用、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのコンテキストによって作成できます。 フィールドには、**[ログイン '\<Login>' を使用する]**、**['\<Domain>\\<Login\>' の権限を借用する]**、**['\<Computer>\\<Login\>' の権限を借用する]** のうちの 1 つが表示されます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、Windows アカウントのコンテキストを使用して、すべての接続を作成することをお勧めします。  
  
## <a name="see-also"></a>参照  
 [ピア ツー ピア トポロジの管理 &#40;レプリケーション Transact-SQL プログラミング&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [@loopback_detection](transactional/peer-to-peer-transactional-replication.md)  
  
  