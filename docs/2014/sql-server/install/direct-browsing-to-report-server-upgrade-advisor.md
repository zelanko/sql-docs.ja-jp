---
title: 直接参照するレポート サーバー (アップグレード アドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 3d2814a4-318a-45ed-b093-1e852fab561f
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: af75f05708c6975a845b6077edef8109db6e5b10
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48128482"
---
# <a name="direct-browsing-to-report-server-upgrade-advisor"></a>レポート サーバーの直接参照 (アップグレード アドバイザー)
  アップグレード アドバイザーには、現在インストールが検出された[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]がレポート サーバーの仮想ディレクトリを直接参照します。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モード。|  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>説明  
 アップグレード アドバイザーには、現在インストールが検出された[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]などのレポート サーバーの仮想ディレクトリを直接参照は**http://\<サーバー名 >/ReportServer**します。 このような直接参照は現在のバージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ではサポートされていません。  
  
> [!NOTE]  
>  この規則は警告であり、アップグレードはブロックされません。  
  
## <a name="corrective-action"></a>修正措置  
 ドキュメント ライブラリの SharePoint ユーザー インターフェイスを使用して参照または使用**http://\<サーバー名 >/sharepoint サイト >/_vti_bin/reportserver reportserver**します。  
  
  
