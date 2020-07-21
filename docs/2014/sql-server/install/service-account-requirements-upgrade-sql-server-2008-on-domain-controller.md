---
title: ドメインコントローラー上の SQL Server 2008 にアップグレードするためのサービスアカウントの要件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- domain controllers
- service accounts
- network service accounts
- local service accounts
ms.assetid: 574245b6-11e2-4849-b0ca-836d673ecd0d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0680e09548e38760f6ac317fec63152486a4e5fb
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85036510"
---
# <a name="service-account-requirements-for-upgrading-to-sql-server-2008-on-a-domain-controller"></a>ドメイン コントローラーで SQL Server 2008 へのアップグレードを実行するためのサービス アカウント要件
  アップグレードアドバイザーによって、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ドメインコントローラー上のネットワークサービスまたはローカルサービスアカウントで実行されているのインスタンスが検出されました [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ドメイン コントローラーに [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] がインストールされている場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを Local Service アカウントまたは Network Service アカウントの特権を使用して実行することはできません。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>修正措置  
 すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントが Domain アカウントまたは Local System アカウントに割り当てられていることを確認してください。 このように変更してからアップグレードしないと、セットアップがブロックされます。 サービス アカウントの SQL ライター、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、および Active Directory Helper サービスは、Network Service アカウントにハードコードされていて変更できないため例外となります。  
  
## <a name="see-also"></a>参照  
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
