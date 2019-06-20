---
title: 直接参照するレポート サーバー (アップグレード アドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3d2814a4-318a-45ed-b093-1e852fab561f
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 870937f4dffe356ca2216335c74566efc73d2a52
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66095536"
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
  
  
