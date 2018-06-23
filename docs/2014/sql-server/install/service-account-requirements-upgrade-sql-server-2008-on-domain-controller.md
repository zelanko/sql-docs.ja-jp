---
title: サービスのドメイン コント ローラーで、SQL Server 2008 にアップグレードするためのアカウントの要件 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- domain controllers
- service accounts
- network service accounts
- local service accounts
ms.assetid: 574245b6-11e2-4849-b0ca-836d673ecd0d
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 06b1143fc205b7afc933369abeed32d9599c7d5b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164707"
---
# <a name="service-account-requirements-for-upgrading-to-sql-server-2008-on-a-domain-controller"></a>ドメイン コントローラーで SQL Server 2008 へのアップグレードを実行するためのサービス アカウント要件
  インスタンスを検出しました[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で Network Service や Local Service アカウントで実行されている、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]ドメイン コント ローラー。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ドメイン コントローラーに [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] がインストールされている場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを Local Service アカウントまたは Network Service アカウントの特権を使用して実行することはできません。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>修正措置  
 すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントが Domain アカウントまたは Local System アカウントに割り当てられていることを確認してください。 このように変更してからアップグレードしないと、セットアップがブロックされます。 サービス アカウントの SQL ライター、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、および Active Directory Helper サービスは、Network Service アカウントにハードコードされていて変更できないため例外となります。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
