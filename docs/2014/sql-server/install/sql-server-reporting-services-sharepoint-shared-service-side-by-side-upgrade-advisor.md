---
title: Microsoft SQL Server Reporting Services SharePoint 共有サービスがインストールされているサイド バイ サイド (アップグレード アドバイザー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6ae1017e-129b-4702-9ea7-00ac9b024062
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 79f07ede92ee840ed50631c10d22bf4b015cf29b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075446"
---
# <a name="microsoft-sql-server-reporting-services-sharepoint-shared-service-is-installed-side-by-side-upgrade-advisor"></a>Microsoft SQL Server Reporting Services SharePoint 共有サービスがサイド バイ サイドでインストールされている (アップグレード アドバイザー)
  アップグレード アドバイザーが検出された[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 共有サービスが以前のバージョンのサイド バイ サイドでインストールされている[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]です。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モードです。|  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>説明  
 アップグレード アドバイザーが検出された[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 共有サービスが以前のバージョンのサイド バイ サイドでインストールされている[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]の SharePoint 共有サービス アーキテクチャに基づくはありません。 新旧両方の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 関連テクノロジがサイド バイ サイドでコンピューターにインストールされているため、アップグレードはブロックされます。  
  
## <a name="corrective-action"></a>修正措置  
 アップグレードを続行するには、既存の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インストールのうちの 1 つをアンインストールする必要があります。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインストールのうちの 1 つを削除した後、アップグレード アドバイザーを再実行して、他にアップグレードに関する問題がないことを確認します。  
  
  