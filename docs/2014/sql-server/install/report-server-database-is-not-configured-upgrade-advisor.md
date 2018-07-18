---
title: レポート サーバー データベースがない (アップグレード アドバイザー) の構成 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: b964300c-b220-4244-9fa6-c0c6a57760f6
caps.latest.revision: 14
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: ccaed3fdebca2f242b1a638315e29915ddfc08d2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249582"
---
# <a name="report-server-database-is-not-configured-upgrade-advisor"></a>レポート サーバー データベースが構成されていない (アップグレード アドバイザー)
  レポート サーバーの構成が不完全であるためアップグレードがブロックされます。 レポート サーバー データベースが構成されていません。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モード。|  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>説明  
 セットアップでアップグレードできるのは、完全に構成されているレポート サーバー インスタンスだけです。 続けるには、する必要がありますか、構成、レポート サーバー データベースまたは使用する Microsoft Windows**コントロール パネルの **からレポート サーバー機能を削除する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インストールします。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を削除すると、その他の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントをアップグレードできるようになります。  
  
## <a name="corrective-action"></a>修正措置  
 レポート サーバー データベースを構成していない場合、レポート サーバーは使用できないので、アップグレード前に削除する必要があります。  
  
 アンインストールの詳細については[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]を参照してください[Reporting Services 2012 のアンインストール](http://technet.microsoft.com/library/hh479745.aspx\(v=sql.11\))します。 このトピックでは、特定のバージョンをアンインストールする方法について説明しています。アンインストールする手順は以前のバージョンでも同様です。  
  
## <a name="see-also"></a>参照  
 [Reporting Services のアップグレードに関する問題&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
