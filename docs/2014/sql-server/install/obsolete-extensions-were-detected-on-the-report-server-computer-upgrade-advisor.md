---
title: レポート サーバー コンピューター (アップグレード アドバイザー) で廃止された拡張機能が検出されました |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 40d245a2-0631-470e-81b3-1feb47e028cb
caps.latest.revision: 13
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: c29365b40d59d76ab65d8f9f40a3bec86a0b486f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37328997"
---
# <a name="obsolete-extensions-were-detected-on-the-report-server-computer-upgrade-advisor"></a>互換性のために残されている拡張機能がレポート サーバー コンピューターで検出された (アップグレード アドバイザー)
  アップグレード アドバイザーによって、現在のリリースでは使用できない表示拡張機能が 1 つ以上検出されました。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モード。|  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>説明  
 このリリースで提供が中止されている拡張機能を 1 つ以上使用するようにレポート サーバーが構成されています。 廃止された拡張機能は次のとおりです。  
  
-   HTML OWC 表示拡張機能  
  
-   HTML 3.2 表示拡張機能  
  
 アップグレードを続行できますが、サポートされていない機能はアップグレード後のレポート サーバーで使用できません。  
  
 これらの拡張機能が必要な場合は、これらの要件に対する代替ソリューションが見つかるまで、アップグレードしないでください。 同一または同様の機能を提供するカスタム表示拡張機能を取得またはビルドする必要が生じることがあります。  
  
## <a name="corrective-action"></a>修正措置  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に現在含まれている一連の機能を評価して、サポートされている機能がユーザーの要件を満たすかどうかを判断します。  
  
## <a name="see-also"></a>参照  
 [Reporting Services のアップグレードに関する問題&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
