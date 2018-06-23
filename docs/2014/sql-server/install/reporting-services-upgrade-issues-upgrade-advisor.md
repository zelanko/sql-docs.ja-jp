---
title: Reporting Services のアップグレードに関する問題 (アップグレード アドバイザー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Report Manager [Reporting Services], upgrade issues
- Reporting Services, upgrades
- upgrading Reporting Services
- report servers [Reporting Services], upgrade issues
ms.assetid: d9663f25-98d7-4508-ae3c-55a7277211bd
caps.latest.revision: 42
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 68e688e416c0d4a001492f9372e8363f558f8a26
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36175279"
---
# <a name="reporting-services-upgrade-issues-upgrade-advisor"></a>Reporting Services のアップグレードに関するその他の問題 (アップグレード アドバイザー)
  次のトピックについて説明、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]へのアップグレードに影響する可能性のある問題[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。 各トピックでは、環境内でこれらの変更の影響を軽減するために実行できる操作について説明します。  
  
 アップグレード アドバイザーによって、現在インストールされているレポート サーバーが分析されます。 コンピューターにインストールされている [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントがレポート デザイナーのみであるなど、クライアント コンポーネントのみがインストールされている場合は、問題は報告されません。  
  
 インストールの構成によっては、アップグレード アドバイザーでは報告されない問題が発生することがあります。 これらの問題によって [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をアップグレードできなくなることはありませんが、アップグレード完了後にレポートとアプリケーションの実行に影響する可能性があります。 これらの問題の詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「Reporting Services の旧バージョンとの互換性」を参照してください。  
  
 セットアップを使用して [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をアップグレードできない場合は、新しい [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インスタンスをインストールし、既存の Reporting Services を新しいインスタンスに移行できます。 詳細についてを参照してください"アップグレードと移行 Reporting Services"[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オンライン ブック、 [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)です。  
  
 次に示すトピックでは、アップグレード アドバイザーによって報告される既知の問題、および既存インストールを修正してアップグレードを可能にする方法について説明します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインスタンスを分析するには、アップグレード アドバイザーをレポート サーバーにインストールしておく必要があります。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] はリモート分析をサポートしません。  
>   
>  詳細については、次を参照してください。[アップグレード アドバイザーをインストールする](../../../2014/sql-server/install/installing-upgrade-advisor.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [レポート サーバー web サイトでクライアント証明書&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/client-certificates-on-the-report-server-web-site-upgrade-advisor.md)  
  
-   [カスタム拡張機能がレポート サーバーで検出された&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/custom-extensions-were-detected-on-the-report-server-upgrade-advisor.md)  
  
-   [カスタム レポート アイテムがレポート サーバーで検出された&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/custom-report-items-were-detected-on-the-report-server-upgrade-advisor.md)  
  
-   [IIS の旧バージョンとの互換性コンポーネントが検出されない&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/iis-backward-compatibility-components-were-not-detected-upgrade-advisor.md)  
  
-   [IP アドレス制限が検出された&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/ip-address-restriction-detected-upgrade-advisor.md)  
  
-   [ISAPI フィルター、レポート サーバー サイトで検出された&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/isapi-filters-detected-on-the-report-server-site-upgrade-advisor.md)  
  
-   [廃止された拡張機能がレポート サーバー コンピューターで検出された&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/obsolete-extensions-were-detected-on-the-report-server-computer-upgrade-advisor.md)  
  
-   [レポート サーバー データベースが構成されていない&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/report-server-database-is-not-configured-upgrade-advisor.md)  
  
-   [SQL Server 2005 レポート サーバー Web サービス グループが検出された&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/sql-server-2005-report-server-web-service-group-detected-upgrade-advisor.md)  
  
-   [仮想ディレクトリが指定されていない&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/virtual-directories-are-unspecified-upgrade-advisor.md)  
  
-   [仮想ディレクトリの認証方法はサポートされていない&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/virtual-directory-has-unsupported-authentication-method-upgrade-advisor.md)  
  
-   [SQL Server Standard および Enterprise の CPU およびメモリの制限に変更&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/cpu-memory-limits-changes-sql-server-standard-enterprise-upgrade-advisor.md)  
  
-   [SharePoint ファームに必要なドメイン アカウント&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/domain-accounts-required-for-sharepoint-farm-upgrade-advisor.md)  
  
-   [レポート サーバーへの参照を直接&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/direct-browsing-to-report-server-upgrade-advisor.md)  
  
-   [Microsoft SharePoint 2007 がインストールされている&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/microsoft-sharepoint-2007-is-installed-upgrade-advisor.md)  
  
-   [Microsoft SQL Server Reporting Services SharePoint 共有サービスがサイド バイ サイドでインストールされている&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/sql-server-reporting-services-sharepoint-shared-service-side-by-side-upgrade-advisor.md)  
  
-   [互換性のないデータベース エンジンのサーバー照合順序&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/incompatible-database-engine-server-collation-upgrade-advisor.md)  
  
-   [その他の Reporting Services のアップグレードに関する問題](../../../2014/sql-server/install/other-reporting-services-upgrade-issues.md)  
  
  