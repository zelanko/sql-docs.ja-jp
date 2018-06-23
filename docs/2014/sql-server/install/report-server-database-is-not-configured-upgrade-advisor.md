---
title: レポート サーバー データベースが構成された (アップグレード アドバイザー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: b964300c-b220-4244-9fa6-c0c6a57760f6
caps.latest.revision: 14
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: f86e9963750d2bacbdc55e235e4975a05c2f625e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085579"
---
# <a name="report-server-database-is-not-configured-upgrade-advisor"></a>レポート サーバー データベースが構成されていない (アップグレード アドバイザー)
  レポート サーバーの構成が不完全であるためアップグレードがブロックされます。 レポート サーバー データベースが構成されていません。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モード。|  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>説明  
 セットアップでアップグレードできるのは、完全に構成されているレポート サーバー インスタンスだけです。 続行するには必要がありますか、レポート サーバー データベースを構成するかを使用して Microsoft Windows**コントロール パネルの **からレポート サーバー機能を削除する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インストールします。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を削除すると、その他の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントをアップグレードできるようになります。  
  
## <a name="corrective-action"></a>修正措置  
 レポート サーバー データベースを構成していない場合、レポート サーバーは使用できないので、アップグレード前に削除する必要があります。  
  
 アンインストールの詳細については[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]を参照してください[Reporting Services 2012 のアンインストール](http://technet.microsoft.com/library/hh479745.aspx\(v=sql.11\))です。 このトピックでは、特定のバージョンをアンインストールする方法について説明しています。アンインストールする手順は以前のバージョンでも同様です。  
  
## <a name="see-also"></a>参照  
 [Reporting Services のアップグレード問題&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  