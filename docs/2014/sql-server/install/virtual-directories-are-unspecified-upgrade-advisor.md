---
title: 仮想ディレクトリが指定されていない (アップグレード アドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- virtual directories [Reporting Services]
ms.assetid: 7d32b560-49d6-4558-b5d6-9127067f82d6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: cbadcd0f42f8d5ae81ea2a97625be96214df4ce2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48227152"
---
# <a name="virtual-directories-are-unspecified-upgrade-advisor"></a>仮想ディレクトリが指定されていない (アップグレード アドバイザー)
  アップグレード アドバイザーで、レポート サーバー Web サービスまたはレポート マネージャーの仮想ディレクトリ設定が検出されませんでした。 アップグレードの完了後、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを使用してレポート サーバーの URL 予約を構成する必要があります。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のネイティブ モード。|  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>説明  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インストールのアップグレードには、レポート サーバー Web サービスとレポート マネージャーの新しい URL の予約が含まれます。 アップグレードするインスタンスのレポート サーバーまたはレポート マネージャーの仮想ディレクトリが、アップグレード アドバイザーによって検出されませんでした。そのため、アップグレード プロセスでは、アップグレード後のレポート サーバーの URL 予約を作成するための情報が不足しています。 アップグレードを続行できますが、レポート サーバー仮想ディレクトリまたはレポート マネージャー仮想ディレクトリは、アップグレード後のインストールでは未定義になります。  
  
## <a name="corrective-action"></a>修正措置  
 アップグレードの完了後、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを使用して、レポート サーバーおよびレポート マネージャーの URL を設定します。 IIS マネージャーを使用して、不要になった仮想ディレクトリをすべて削除します。  
  
 詳細については、[URL の構成&#40;SSRS 構成マネージャー&#41; ](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オンライン ブックの「を参照してください。  
  
## <a name="see-also"></a>参照  
 [Reporting Services のアップグレードに関する問題&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
