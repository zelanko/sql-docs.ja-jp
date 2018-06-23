---
title: レポート サーバー サイト (アップグレード アドバイザー) 上で検出された ISAPI フィルター |Microsoft ドキュメント
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
- ISAPI filters
- report servers [Reporting Services], upgrade issues
ms.assetid: dd30560d-9e16-47c7-ba68-a9743a657e4e
caps.latest.revision: 12
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 18a9aab0737cb6d5127bbb3357d307c9c8f03aef
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165725"
---
# <a name="isapi-filters-detected-on-the-report-server-site-upgrade-advisor"></a>ISAPI フィルターがレポート サーバー サイトで検出された (アップグレード アドバイザー)
  アップグレード アドバイザーによって、レポート サーバー仮想ディレクトリおよびレポート マネージャー仮想ディレクトリをホストする Web サイトで 1 つ以上の ISAPI フィルターが検出されました。 ISAPI フィルターがでサポートされていない[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]です。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブです。|  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>説明  
 アップグレードする前に、Web サイトの ISAPI フィルターが [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アプリケーションで使用されているかどうかを確認します。 ISAPI フィルターが必要でない場合、レポート サーバーをアップグレードできます。 セットアップでは、既定の URL が作成され、IIS で実行される ISAPI フィルターはサポートされません。 ISAPI フィルターが必要な場合は、ISAPI フィルターをホストする別の方法 (ISA Server の使用や、IIS での ISAPI フィルターのホストの継続など) を把握してからアップグレードしてください。 レポート サーバーでは、シナリオによっては、ISAPI フィルターの代わりとして ASP.NET HTTPModules がサポートされます。 詳細については、MSDN で ASP.NET のマニュアルを参照してください。  
  
## <a name="corrective-action"></a>修正措置  
 配置に必要な ISAPI フィルターをホストするための個別のソリューションを評価し、使用します。  
  
## <a name="see-also"></a>参照  
 [Reporting Services のアップグレード問題&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  