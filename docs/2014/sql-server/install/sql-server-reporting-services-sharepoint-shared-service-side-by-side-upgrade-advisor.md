---
title: Microsoft SQL Server Reporting Services SharePoint 共有サービスがインストールされているサイド バイ サイド (アップグレード アドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6ae1017e-129b-4702-9ea7-00ac9b024062
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: cfa2eb99a475cb8f8bce8a0a1101edd767997aef
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66091856"
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
  
  
