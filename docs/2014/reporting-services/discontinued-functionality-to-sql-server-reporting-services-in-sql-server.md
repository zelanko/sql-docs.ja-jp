---
title: 廃止された SQL Server 2014 における SQL Server Reporting Services の機能 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- discontinued functionality [Reporting Services]
- Reporting Services, backward compatibility
- Rsactivate.exe
- unsupported features [Reporting Services]
ms.assetid: d529cc96-3483-480b-9bfc-bd28b1d0ef52
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: ec97f47c87abed0a3fd650632458bf4ba956e985
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48100222"
---
# <a name="discontinued-functionality-to-sql-server-reporting-services-in-sql-server-2014"></a>SQL Server 2014 で廃止された SQL Server Reporting Services の機能
  このトピックでは、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] で使用できなくなった [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]の機能について説明します。 特定のバージョンのオペレーティング システムまたは [!INCLUDE[msCoName](../includes/msconame-md.md)] インターネット インフォメーション サービス (IIS) で廃止されたサポートに関する告知事項は含まれていません。 システムの前提条件の詳細については、次を参照してください。 [Hardware and Software Requirements for Installing SQL Server 2014](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)します。  
  
 このトピックの内容  
  
-   [SQL Server 2014 Reporting Services で廃止された機能](#bkmk_sql14)  
  
-   [SQL Server 2012 Reporting Services で廃止された機能](#bkmk_rc0)  
  
-   [SQL Server 2008 R2 Reporting Services で廃止された機能](#bkmk_kj)  
  
##  <a name="bkmk_sql14"></a> [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Reporting Services で廃止された機能  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] で廃止された [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 機能はありません。  
  
##  <a name="bkmk_rc0"></a> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Reporting Services で廃止された機能  
 ここでは、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] で廃止された [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 機能について説明します。  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] で廃止された [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 機能はありません。  
  
##  <a name="bkmk_kj"></a> SQL Server 2008 R2 Reporting Services で廃止された機能  
 このセクションの説明では、廃止[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]します。  
  
> [!NOTE]  
>  SQL Server 2008 R2 は SQL Server 2008 のマイナー バージョン アップグレードなので、SQL Server 2008 のセクションのコンテンツも確認することをお勧めします。  
  
### <a name="64-bit-platform-support"></a>64 ビット プラットフォームのサポート  
 以降では[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]コンポーネントは、Windows Server 2003 または Windows Server 2003 R2 を実行している Itanium ベースのサーバーをサポートしていません。 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Windows Server 2008 を itanium ベース システムと Windows Server 2008 R2 for Itanium-Based Systems など、他の 64 ビット オペレーティング システムをサポートし続けます。 Windows Server 2003 または Windows Server 2003 R2 の Itanium ベース システム エディションにインストールされた [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] を [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] にアップグレードするには、まずオペレーティング システムをアップグレードする必要があります。  
  
### <a name="data-source-credentials-in-url-access"></a>URL アクセスでのデータ ソース資格情報  
 URL アクセス パラメーター文字列*dsu:datasourcename 値 =* と*dsp:datasourcename 値 =* は、廃止されました。 以前のバージョンでは、これらのパラメーター文字列は、セキュリティで保護されていないブラウザー キャッシュにプレーンテキストで保存されます。  
  
## <a name="see-also"></a>参照  
 [新機能については&#40;Reporting Services&#41;](what-s-new-reporting-services.md)   
 [SQL Server 2014 における SQL Server Reporting Services の動作変更します。](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)   
 [SQL Server 2014 における SQL Server Reporting Services の非推奨の機能](deprecated-features-in-sql-server-reporting-services-ssrs.md)  
  
  
