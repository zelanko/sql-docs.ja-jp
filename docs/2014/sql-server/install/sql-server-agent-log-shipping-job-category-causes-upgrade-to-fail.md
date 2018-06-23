---
title: SQL Server エージェントのログ配布ジョブ カテゴリが原因で失敗するアップグレード |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- log shipping [SQL Server Agent]
- job categories [SQL Server Agent]
ms.assetid: ef05ce53-c6ce-42ec-9df8-46c951626424
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 47d7d5024d234478b8b54e3c05b3c22335758782
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083564"
---
# <a name="sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail"></a>SQL Server エージェントのログ配布ジョブ カテゴリが原因でアップグレードに失敗する
  "ログ配布" という名前の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブ カテゴリがある場合、アップグレード プロセスは失敗します。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント  
  
## <a name="description"></a>説明  
 "ログ配布" という名前のシステム ジョブ カテゴリがあります。 アップグレード対象のインストールにユーザーが作成した "ログ配布" という名前のジョブ カテゴリが含まれている場合、アップグレードする前にそのジョブ カテゴリの名前を変更する必要があります。名前を変更しないと、アップグレード プロセスは失敗します。  
  
## <a name="see-also"></a>参照  
 [アップグレード後にログ配布は実行されません。](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md)   
 [アップグレード、SQL Server エージェント ユーザー プロキシ アカウントが一時的な UpgradedProxyAccount に変更されます。](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md)   
 [SQL Server エージェントのアップグレードに関する問題](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  