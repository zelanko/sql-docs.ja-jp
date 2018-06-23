---
title: アップグレードの問題を解決する |Microsoft ドキュメント
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
- installing Upgrade Advisor
- Upgrade Advisor [SQL Server], reference
- component issue resolution [Upgrade Advisor]
- resolving upgrade issues
- upgrade blocks [Upgrade Advisor]
- detecting upgrade issues
- finding upgrade issues
- Upgrade Advisor [SQL Server], blocking issues
- configurations preventing upgrading [Upgrade Advisor]
- locating upgrade issues
- blocking issues [Upgrade Advisor]
- issues preventing upgrading [Upgrade Advisor]
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, reference
- analyzing system [Upgrade Advisor], resolving issues
- settings preventing upgrading [Upgrade Advisor]
- upgrade issue reference [Upgrade Advisor]
- identifying upgrade issues
- fixing upgrade issues [Upgrade Advisor]
ms.assetid: 113eb435-8d36-4ed6-9790-b5e4c14809c8
caps.latest.revision: 37
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6072fb3c1d52048832bd6d07f34828c84eb2d491
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083779"
---
# <a name="resolving-upgrade-issues"></a>アップグレードに関する問題とその対処方法
  このセクションのトピックでは、アップグレードに関連する検出可能な問題と、検出できずアップグレードまたはアップグレード後の動作に影響することが考えられる問題について説明します。 これらの問題は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントごとにまとめられています。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [最新のアップグレードに関する問題](../../../2014/sql-server/install/late-breaking-upgrade-issues.md)  
  
-   [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
-   [フルテキスト検索のアップグレードに関する問題](../../../2014/sql-server/install/full-text-search-upgrade-issues.md)  
  
-   [レプリケーションのアップグレードに関する問題](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
-   [Reporting Services のアップグレード問題&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
-   [SQL Server エージェントのアップグレードに関する問題](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
## <a name="issues-that-prevent-upgrading"></a>アップグレードを妨げる問題  
 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の構成または設定が原因で、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードできなくなる場合があります。 セットアップでは、インストールするときにこれらの問題が検出された場合[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]セットアップがアップグレード プロセスを停止し、アップグレード アドバイザーを実行して、ブロックの問題を修正するを要求します。  
  
### [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
 以下のタスクが[!INCLUDE[ssDE](../../includes/ssde-md.md)]のアップグレード レポートに表示された場合は、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードする前に必要な操作を実行する必要があります。  
  
-   [データベース ID 32767 をデタッチします。](../../../2014/sql-server/install/detach-database-id-32767.md)  
  
-   [固定サーバー ロールの名前と一致するログインの名前を変更します。](../../../2014/sql-server/install/rename-logins-matching-fixed-server-role-names.md)  
  
-   [ユーザー sys の名前を変更します。](../../../2014/sql-server/install/rename-user-sys.md)  
  
-   [Sp_rename を使用して、重複するインデックス名を変更するには](../../../2014/sql-server/install/use-sp-rename-to-rename-duplicate-index-name.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
