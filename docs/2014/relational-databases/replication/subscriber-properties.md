---
title: '[サブスクライバーのプロパティ] | Microsoft Docs'
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
- sql12.rep.configdistwizard.subscribers.f1
helpviewer_keywords:
- Subscriber Properties dialog box
ms.assetid: 32aa0347-64e4-4aa4-ac57-6bd3e5d52070
caps.latest.revision: 21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 46c53e1f86bcdc21ff2e75d82de6343463f5c6ca
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37262358"
---
# <a name="subscriber-properties"></a>[サブスクライバーのプロパティ]
  **[サブスクライバーのプロパティ]** ダイアログ ボックスには、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] より前のバージョンの [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているサブスクライバーに関連する情報が表示されます。  
  
## <a name="options"></a>および  
 **[サブスクライバーへのエージェント接続]**  
 ディストリビューターからサブスクライバーに、ディストリビューション エージェントとマージ エージェントを接続する際のコンテキストです。これは [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]より前のバージョンにのみ適用されます。  
  
 **[エージェント プロセス アカウントを借用する]** を選択して、ディストリビューターで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのアカウントのコンテキストを使用してサブスクライバーへの接続を作成するか、 **[SQL Server 認証]** を指定して **[ログイン]** および **[パスワード]** の値を入力します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、 **[エージェント プロセス アカウントを借用する]** を選択することをお勧めします。  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンでは、サブスクリプションの新規作成ウィザードで各サブスクリプションについて接続情報を指定します。接続情報の変更は **[サブスクリプションのプロパティ]** ダイアログ ボックスで行います。  
  
 **[既定のエージェントのスケジュール]**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] より前のバージョンの [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]を実行しているサブスクライバーでは、サブスクリプションの新規作成ウィザードで既定のスケジュールが使用されます。  
  
 **その他**  
 サブスクライバーとサブスクライバーの種類に関する情報が含まれています。  
  
## <a name="see-also"></a>参照  
 [View and Modify Distributor and Publisher Properties (ディストリビューターとパブリッシャーのプロパティの表示および変更)](view-and-modify-distributor-and-publisher-properties.md)   
 [プロパティ リファレンス &#40;レプリケーション&#41;](properties-reference-replication.md)   
 [パブリケーションのサブスクライブ](subscribe-to-publications.md)  
  
  
