---
title: レポートサーバー web サイトのクライアント証明書 (アップグレードアドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 5ecce26b-99df-4109-8e51-d150d369dff7
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 5588930efbadf785e78aa115ad0021bce64bd7f7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "71952603"
---
# <a name="client-certificates-on-the-report-server-web-site-upgrade-advisor"></a>レポート サーバー Web サイト上のクライアント証明書 (アップグレード アドバイザー)
  アップグレード アドバイザーによって、レポート サーバー仮想ディレクトリまたはレポート マネージャー仮想ディレクトリをホストする IIS Web サイトで、1 つ以上のクライアント証明書が検出されました。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード。|  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>[説明]  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]では、ユーザーを認証するためのクライアント証明書の使用はサポートされていません。 アップグレードを続行できますが、クライアント証明書はアップグレード後のレポート サーバーで使用されません。  
  
## <a name="corrective-action"></a>修正措置  
 クライアント証明書の認証要件に対処するには、ISA Server など個別のソリューションを使用する必要があります。  
  
## <a name="see-also"></a>参照  
 [アップグレードに関する問題を Reporting Services &#40;アップグレードアドバイザー&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
