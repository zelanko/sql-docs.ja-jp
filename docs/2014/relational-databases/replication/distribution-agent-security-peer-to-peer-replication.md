---
title: '[ディストリビューション エージェント セキュリティ] (ピア ツー ピア レプリケーション) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.p2pwizard.DA.f1
ms.assetid: def6bf26-c640-4caf-ad30-05d1e649541d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 78d8baed7783459db79bb9facb0141cc570c4127
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/25/2020
ms.locfileid: "62721383"
---
# <a name="distribution-agent-security-peer-to-peer-replication"></a>[ディストリビューション エージェント セキュリティ] (ピア ツー ピア レプリケーション)
  **[ディストリビューション エージェント セキュリティ]** ページを使用すると、ディストリビューション エージェントを実行するアカウントの指定と、ピア ツー ピア テクノロジによるコンピューターへの接続の作成ができます。 エージェントで必要とされる権限と、レプリケーション セキュリティの推奨事項については、「[レプリケーション エージェントのセキュリティ モデル](security/replication-agent-security-model.md)」と「[レプリケーション セキュリティの推奨事項](security/replication-security-best-practices.md)」を参照してください。  
  
> [!NOTE]  
>  サブスクリプションのディストリビューション エージェントが、このウィザードの以前の実行で既に構成されている場合、使用される資格情報をこのウィザードで変更することはできません。 新しい資格情報を指定した場合は無視されます。 資格情報を変更するには、 **[サブスクリプションのプロパティ]** ダイアログ ボックスを使用します。 詳細については、「[レプリケーションのセキュリティ設定を表示および変更](security/view-and-modify-replication-security-settings.md)する」を参照してください。  
  
## <a name="options"></a>オプション  
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
 [ピアツーピアトポロジの管理 &#40;レプリケーション Transact-sql プログラミング&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [ピアツーピアトランザクションレプリケーション](transactional/peer-to-peer-transactional-replication.md)  
  
  
