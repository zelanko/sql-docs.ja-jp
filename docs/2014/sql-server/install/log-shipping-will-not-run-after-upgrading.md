---
title: アップグレード後にログ配布が実行されない |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server]
ms.assetid: 6727cb7d-ac01-4972-a730-dbb7cdc29705
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 952a47eaa2028819908ef7e93326c31a289a0cc2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66093980"
---
# <a name="log-shipping-will-not-run-after-upgrading"></a>アップグレード後にログ配布が実行されない
  アップグレード アドバイザーによって、ログ配布を使用していることが検出されました。 
  [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] のログ配布は [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のログ配布と互換性がなく、直接アップグレードできません。 
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードした後、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] またはストアド プロシージャを使用してログ配布を再構成します。  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェントログ配布ジョブカテゴリによってアップグレードが失敗する](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md)   
 [アップグレードすると、SQL Server エージェントユーザープロキシアカウントが一時的な UpgradedProxyAccount に変更されます](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md)   
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
