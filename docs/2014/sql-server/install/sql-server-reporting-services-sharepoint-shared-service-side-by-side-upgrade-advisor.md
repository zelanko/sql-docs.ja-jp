---
title: Microsoft SQL Server Reporting Services SharePoint 共有サービスがインストールされているサイド バイ サイド (アップグレード アドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6ae1017e-129b-4702-9ea7-00ac9b024062
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 97e0345a38148e02e7f7e73852284887b66b2ccc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37206392"
---
# <a name="microsoft-sql-server-reporting-services-sharepoint-shared-service-is-installed-side-by-side-upgrade-advisor"></a>Microsoft SQL Server Reporting Services SharePoint 共有サービスがサイド バイ サイドでインストールされている (アップグレード アドバイザー)
  アップグレード アドバイザーが検出された[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 共有サービスが以前のバージョンのサイドでインストールされている[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]します。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モード。|  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>説明  
 アップグレード アドバイザーが検出された[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 共有サービスが以前のバージョンのサイドでインストールされている[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint 共有サービス アーキテクチャに基づくされません。 新旧両方の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 関連テクノロジがサイド バイ サイドでコンピューターにインストールされているため、アップグレードはブロックされます。  
  
## <a name="corrective-action"></a>修正措置  
 アップグレードを続行するには、既存の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インストールのうちの 1 つをアンインストールする必要があります。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインストールのうちの 1 つを削除した後、アップグレード アドバイザーを再実行して、他にアップグレードに関する問題がないことを確認します。  
  
  
