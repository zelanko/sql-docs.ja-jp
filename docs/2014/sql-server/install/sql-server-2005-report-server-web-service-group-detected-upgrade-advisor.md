---
title: SQL Server 2005 レポート サーバー Web サービス グループの検出 (アップグレード アドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- deployment [Reporting Services]
ms.assetid: 699d24eb-7756-4b41-9294-ef1a94b2f267
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 4f379675a4d7b37b9eab69598f7c04bc57306d46
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66092107"
---
# <a name="sql-server-2005-report-server-web-service-group-detected-upgrade-advisor"></a>SQL Server 2005 レポート サーバー Web サービス グループが検出された (アップグレード アドバイザー)
  アップグレード アドバイザーでは、ことが検出されました、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスが関連付けられている、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]レポート サーバー Web サービスのグループ。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のネイティブ モード。|  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>説明  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 使用しない、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]レポート サーバー Web サービスのグループ。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードするときに、このサービス グループは削除され、このグループまたはグループに属するユーザーのカスタムのアクセス制御リスト (ACL) はアップグレード中に保持されません。  
  
## <a name="corrective-action"></a>修正措置  
 アップグレードする前に、すべてのカスタムの ACL または [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] レポート サーバー Web サービス グループに属するユーザーをバックアップします。 これを行うには、使用することができます、 **Icacls.exe**コマンド ライン ツールで[!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]SP2 以降ではより前のバージョンの Windows オペレーティング システムの Cacls.exe コマンド ライン ツールまたは[!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]SP2。 これらのツールの構文の詳細については、Windows の製品マニュアルを参照してください。 セットアップが正常に完了した後、カスタムの ACL またはユーザーを、レポート サーバー インスタンスの [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] レポート サーバー Windows グループに適用します。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]レポート サーバー Windows グループはフォーム sqlserverreportserveruser $\<*computer_name*>$\<*instance_name*>。  
  
## <a name="see-also"></a>参照  
 [Reporting Services のアップグレードに関する問題&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
