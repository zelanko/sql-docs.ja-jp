---
title: カスタム レポート アイテムがレポート サーバー (アップグレード アドバイザー) で検出された |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- custom report items, upgrading
ms.assetid: aee32006-65b2-4dfe-9570-d85a249d17b2
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: c971c8e19c6881cdc172a4e5c29952a1f829912a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48170762"
---
# <a name="custom-report-items-were-detected-on-the-report-server-upgrade-advisor"></a>カスタム レポート アイテムがレポート サーバーで検出された (アップグレード アドバイザー)
  以前のリリース用に作成されたカスタム レポート アイテム[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]と互換性がない[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]します。 アップグレードを続行できますが、そのカスタム レポート アイテムを使用するレポートは想定どおりに実行されません。 アップグレード アドバイザーによって、カスタム レポート アイテムが検出されました。 アップグレードを続行できますが、アップグレードの完了後、カスタム レポート アイテム ファイルを新しいインストール フォルダーに手動で移動する必要があります。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モード。|  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>説明  
 アップグレード アドバイザーによって、構成ファイル内にカスタム [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 拡張設定が検出されました。これは、レポート用のカスタム アセンブリが 1 つ以上インストールに含まれていることを示しています。  
  
## <a name="corrective-action"></a>修正措置  
 アップグレードの完了後、カスタム レポート アイテム ファイルを新しいインストール フォルダーに手動で移動します。  
  
## <a name="see-also"></a>参照  
 [Reporting Services のアップグレードに関する問題&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
