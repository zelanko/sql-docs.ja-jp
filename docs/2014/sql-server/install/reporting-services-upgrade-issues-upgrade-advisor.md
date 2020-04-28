---
title: Reporting Services のアップグレードに関する問題 (アップグレードアドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Report Manager [Reporting Services], upgrade issues
- Reporting Services, upgrades
- upgrading Reporting Services
- report servers [Reporting Services], upgrade issues
ms.assetid: d9663f25-98d7-4508-ae3c-55a7277211bd
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 75c3bda5d15e3930fcdeba9ca73d70128fd90336
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "71952057"
---
# <a name="reporting-services-upgrade-issues-upgrade-advisor"></a>Reporting Services のアップグレードに関するその他の問題 (アップグレード アドバイザー)
  次のトピックでは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 、へ[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のアップグレードに影響する可能性がある問題について説明します。 これらのトピックでは、これらの変更が環境に与える影響を軽減するために実行できる操作について説明します。  
  
 アップグレード アドバイザーによって、現在インストールされているレポート サーバーが分析されます。 コンピューターにインストールされている [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントがレポート デザイナーのみであるなど、クライアント コンポーネントのみがインストールされている場合は、問題は報告されません。  
  
 インストールの構成によっては、アップグレード アドバイザーでは報告されない問題が発生することがあります。 これらの問題によって [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をアップグレードできなくなることはありませんが、アップグレード完了後にレポートとアプリケーションの実行に影響する可能性があります。 これらの問題の詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「Reporting Services の旧バージョンとの互換性」を参照してください。  
  
 セットアップを使用して [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をアップグレードできない場合は、新しい [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インスタンスをインストールし、既存の Reporting Services を新しいインスタンスに移行できます。 詳細については、オンライン[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ブックの「Reporting Services のアップグレードと移行」、「[アップグレードと移行](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)」を参照してください Reporting Services。  
  
 次に示すトピックでは、アップグレード アドバイザーによって報告される既知の問題、および既存インストールを修正してアップグレードを可能にする方法について説明します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインスタンスを分析するには、アップグレード アドバイザーをレポート サーバーにインストールしておく必要があります。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] はリモート分析をサポートしません。  
>   
>  詳細については、「 [Upgrade Advisor のインストール](../../../2014/sql-server/install/installing-upgrade-advisor.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [レポートサーバー web サイトのクライアント証明書 &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/client-certificates-on-the-report-server-web-site-upgrade-advisor.md)  
  
-   [レポートサーバー &#40;アップグレードアドバイザーでカスタム拡張機能が検出されました&#41;](../../../2014/sql-server/install/custom-extensions-were-detected-on-the-report-server-upgrade-advisor.md)  
  
-   [カスタムレポートアイテムがレポートサーバー &#40;アップグレードアドバイザーで検出されました&#41;](../../../2014/sql-server/install/custom-report-items-were-detected-on-the-report-server-upgrade-advisor.md)  
  
-   [アップグレードアドバイザー &#40;IIS の下位互換性コンポーネントが検出されませんでした&#41;](../../../2014/sql-server/install/iis-backward-compatibility-components-were-not-detected-upgrade-advisor.md)  
  
-   [アップグレードアドバイザーの &#40;IP アドレス制限が検出されました&#41;](../../../2014/sql-server/install/ip-address-restriction-detected-upgrade-advisor.md)  
  
-   [レポートサーバーサイト &#40;アップグレードアドバイザーで検出された ISAPI フィルター&#41;](../../../2014/sql-server/install/isapi-filters-detected-on-the-report-server-site-upgrade-advisor.md)  
  
-   [古い拡張機能がレポートサーバーコンピューター &#40;アップグレードアドバイザーで検出されました&#41;](../../../2014/sql-server/install/obsolete-extensions-were-detected-on-the-report-server-computer-upgrade-advisor.md)  
  
-   [レポートサーバーデータベースがアップグレードアドバイザー &#40;構成されていません&#41;](../../../2014/sql-server/install/report-server-database-is-not-configured-upgrade-advisor.md)  
  
-   [SQL Server 2005 レポートサーバー Web サービスグループが &#40;アップグレードアドバイザーを検出しました&#41;](../../../2014/sql-server/install/sql-server-2005-report-server-web-service-group-detected-upgrade-advisor.md)  
  
-   [仮想ディレクトリは &#40;アップグレードアドバイザーでは指定されていません&#41;](../../../2014/sql-server/install/virtual-directories-are-unspecified-upgrade-advisor.md)  
  
-   [仮想ディレクトリに、アップグレードアドバイザー &#40;サポートされていない認証方法があり&#41;](../../../2014/sql-server/install/virtual-directory-has-unsupported-authentication-method-upgrade-advisor.md)  
  
-   [SQL Server Standard と Enterprise &#40;Upgrade Advisor の CPU およびメモリの制限に対する変更&#41;](../../../2014/sql-server/install/cpu-memory-limits-changes-sql-server-standard-enterprise-upgrade-advisor.md)  
  
-   [SharePoint ファームに必要なドメインアカウント &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/domain-accounts-required-for-sharepoint-farm-upgrade-advisor.md)  
  
-   [レポートサーバー &#40;アップグレードアドバイザーの直接参照&#41;](../../../2014/sql-server/install/direct-browsing-to-report-server-upgrade-advisor.md)  
  
-   [Microsoft SharePoint 2007 は &#40;Upgrade Advisor にインストールされて&#41;](../../../2014/sql-server/install/microsoft-sharepoint-2007-is-installed-upgrade-advisor.md)  
  
-   [SharePoint 共有サービスがサイドバイサイド &#40;アップグレードアドバイザーによってインストールされている Microsoft SQL Server Reporting Services&#41;](../../../2014/sql-server/install/sql-server-reporting-services-sharepoint-shared-service-side-by-side-upgrade-advisor.md)  
  
-   [互換性のないデータベースエンジン Server 照合順序 &#40;アップグレードアドバイザー&#41;](../../../2014/sql-server/install/incompatible-database-engine-server-collation-upgrade-advisor.md)  
  
-   [Reporting Services のアップグレードに関するその他の問題](../../../2014/sql-server/install/other-reporting-services-upgrade-issues.md)  
  
  
