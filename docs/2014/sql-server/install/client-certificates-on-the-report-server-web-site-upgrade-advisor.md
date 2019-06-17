---
title: レポート サーバー web サイト (アップグレード アドバイザー) 上のクライアント証明書 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 5ecce26b-99df-4109-8e51-d150d369dff7
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: a0a8fb06eabb6fa07e503c00d3651020d52cff26
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66096476"
---
# <a name="client-certificates-on-the-report-server-web-site-upgrade-advisor"></a>レポート サーバー Web サイト上のクライアント証明書 (アップグレード アドバイザー)
  アップグレード アドバイザーによって、レポート サーバー仮想ディレクトリまたはレポート マネージャー仮想ディレクトリをホストする IIS Web サイトで、1 つ以上のクライアント証明書が検出されました。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のネイティブ モード。|  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>説明  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、ユーザーの認証にクライアント証明書を使用することはできません。 アップグレードを続行できますが、クライアント証明書はアップグレード後のレポート サーバーで使用されません。  
  
## <a name="corrective-action"></a>修正措置  
 クライアント証明書の認証要件に対処するには、ISA Server など個別のソリューションを使用する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [Reporting Services のアップグレードに関する問題&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
