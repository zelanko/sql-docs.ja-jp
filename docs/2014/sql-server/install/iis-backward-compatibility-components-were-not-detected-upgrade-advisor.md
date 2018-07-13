---
title: IIS の下位互換コンポーネントがなかった検出 (アップグレード アドバイザー) |Microsoft Docs
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
- IIS [Reporting Services]
ms.assetid: e794185a-0a77-480a-9aea-d09f8760a6b8
caps.latest.revision: 10
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 689ca199202b594376a4d0785992123f6016e384
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37177226"
---
# <a name="iis-backward-compatibility-components-were-not-detected-upgrade-advisor"></a>IIS の下位互換コンポーネントが検出されない (アップグレード アドバイザー)
  新しい [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL を作成するためにセットアップで使用する情報を提供する IIS コンポーネントと設定が、アップグレード アドバイザーで検出されませんでした。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のネイティブ モード。|  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>説明  
 IIS にはレポート サーバー仮想ディレクトリおよびレポート マネージャー仮想ディレクトリに関する情報を提供するコンポーネントが含まれており、これらのコンポーネントがレポート サーバー コンピューターにインストールされていません。 アップグレードを続行できますが、レポート サーバーまたはレポート マネージャーの URL は、アップグレードで再作成されません。  
  
## <a name="corrective-action"></a>修正措置  
 アップグレードの完了後、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールを使用してレポート サーバーまたはレポート マネージャーの URL を設定します。 IIS マネージャーを使用して、不要になった仮想ディレクトリを削除します。  
  
 詳細については、次を参照してください。 [URL の構成&#40;SSRS 構成マネージャー&#41; ](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オンライン ブックの「します。  
  
## <a name="see-also"></a>参照  
 [Reporting Services のアップグレードに関する問題&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
