---
title: SharePoint 共有サービスがサイドバイサイドでインストールされている Microsoft SQL Server Reporting Services (アップグレードアドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6ae1017e-129b-4702-9ea7-00ac9b024062
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b8a26fedd892dfb26dea4616efd46d3b3748b508
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85035989"
---
# <a name="microsoft-sql-server-reporting-services-sharepoint-shared-service-is-installed-side-by-side-upgrade-advisor"></a>Microsoft SQL Server Reporting Services SharePoint 共有サービスがサイド バイ サイドでインストールされている (アップグレード アドバイザー)
  アップグレードアドバイザーに [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] よって、SharePoint 共有サービスが以前のバージョンのとサイドバイサイドでインストールされていることが検出されました [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint モード。|  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>説明  
 アップグレードアドバイザーによって、sharepoint 共有サービス [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] が [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sharepoint 共有サービスアーキテクチャに基づいていない以前のバージョンのとサイドバイサイドでインストールされていることが検出されました。 新旧両方の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 関連テクノロジがサイド バイ サイドでコンピューターにインストールされているため、アップグレードはブロックされます。  
  
## <a name="corrective-action"></a>修正措置  
 アップグレードを続行するには、既存の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インストールのうちの 1 つをアンインストールする必要があります。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインストールのうちの 1 つを削除した後、アップグレード アドバイザーを再実行して、他にアップグレードに関する問題がないことを確認します。  
  
  
