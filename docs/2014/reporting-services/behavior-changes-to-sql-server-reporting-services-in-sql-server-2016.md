---
title: SQL Server 2014 における SQL Server Reporting Services の動作変更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- rows [Reporting Services], heights
- leading blanks
- installing Reporting Services, behavior changes with release
- cryptography [Reporting Services]
- Setup [Reporting Services], behavior changes with release
- DefaultValueQueryBased property
- encryption [Reporting Services]
- decryption [Reporting Services]
- blank characters [SQL Server]
- initializing installations [Reporting Services]
- behavior changes [Reporting Services]
ms.assetid: 2a767f0f-84f2-4099-8784-1e37790f858e
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: a8533552a48acd695ca7216ba6881b33369d5b1c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48116378"
---
# <a name="behavior-changes-to-sql-server-reporting-services--in-sql-server-2014"></a>SQL Server 2014 における SQL Server Reporting Services の動作変更
  このトピックでは、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]における動作変更について説明します。 動作変更によって、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] の以前のバージョンに比べて、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の機能の動作や操作方法が変わります。  
  
 このトピックの内容  
  
-   [SQL Server 2014 Reporting Services における動作変更](#bkmk_sql14)  
  
-   [SQL Server 2012 Reporting Services における動作変更](#bkmk_rc0)  
  
-   [SQL Server 2008 R2 Reporting Services における動作変更](#bkmk_kj)  
  
##  <a name="bkmk_sql14"></a> [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Reporting Services の動作の変更  
 あるない[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]の動作に変更[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]します。  
  
##  <a name="bkmk_rc0"></a> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Reporting Services の動作の変更  
 ここでは、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint モードでの動作変更について説明します。  
  
### <a name="view-items-permission-will-not-download-shared-datasets-sharepoint-mode"></a>"アイテムの表示" 権限によって共有データセットがダウンロードされない (SharePoint モード)  
 **新しい動作:** "アイテムの表示" SharePoint 権限を持つユーザーは、Reporting Services 共有データセットのコンテンツをダウンロードできなくなりました。 この動作変更は、レポート、データ ソース、およびモデルに対する各 "アイテムの表示" 権限間で一貫しています。 "アイテムの表示" 権限を持つユーザーは、レポート、データ ソース、およびモデルを表示することはできますが、それらのコンテンツをダウンロードすることはできません。  
  
 **以前の動作:** "アイテムの表示" SharePoint 権限を持つユーザーは、Reporting Services 共有データセットのコンテンツをダウンロードすることができました。  
  
 SharePoint 権限レベルの詳細については、「 [ユーザー権限とアクセス許可レベル](http://technet.microsoft.com/library/cc721640.aspx)」を参照してください。  
  
### <a name="report-server-trace-logs-are-in-a-new-location-for-sharepoint-mode-sharepoint-mode"></a>SharePoint モードでは Report Server のトレース ログが新しい場所に置かれる (SharePoint モード)  
 **新しい動作:** SharePoint モードでインストールされているレポート サーバーは、レポート サーバーのトレース ログが %Programfiles%\Common files \microsoft shared \web Server \14\web Services\ReportServer\LogFiles 下になります。  
  
 **以前の動作:** レポート サーバーのトレース ログは、次のようなパスで見つかった: %Programfilesdir%\Microsoft SQL Server\\< RS_instance > \reporting  
  
### <a name="getserverconfiginfo-soap-api-is-no-longer-supported-sharepoint-mode"></a>GetServerConfigInfo SOAP API がサポートされなくなった (SharePoint モード)  
 **新しい動作**: PowerShell を使用してコマンドレット"Get-sprsserviceapplicationservers"  
  
 **以前の動作:** 顧客と直接通信するために SOAP クライアント コードを開発、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]終点、および GetReportServerConfigInfo() を呼び出す。  
  
### <a name="report-server-configuration-and-management-tools"></a>レポート サーバーの構成と管理のツール  
  
#### <a name="configuration-manager-is-not-used-for-sharepoint-mode"></a>SharePoint モードで構成マネージャーが使用されない  
 **新しい動作:** 、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Configuration Manager が SharePoint モードのレポート サーバーをサポートしていません。 構成の[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]SharePoint モードで SharePoint サーバーの全体管理を使用して完了できるため[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]Configuration Manager が SharePoint モードをサポートしていません。 構成マネージャーは今後、ネイティブ モードのレポート サーバーに対してのみ使用されます。  
  
#### <a name="you-cannot-change-the-server-from-one-mode-to-another"></a>サーバーを別のモードに変更できない  
 **新しい動作:** サーバー モードを変更することはできません。 レポート サーバーをネイティブ モードとしてインストールした場合、それを変更または再構成して SharePoint モードにすることはできません。 SharePoint モードでインストールした場合は、レポート サーバーをネイティブ モードに変更できます。  
  
 **以前の動作:** インストール、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint モードでレポート サーバー。 レポート サーバーをネイティブ モードに切り替えたい場合は、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 構成マネージャーを開き、新しいネイティブ モード データベースを作成するか、または既存のネイティブ モード データベースに接続することで、ネイティブ モードに切り替えることができました。 顧客も使用できます[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]Configuration Manager を SharePoint モードからネイティブ モードに切り替えます。  
  
##  <a name="bkmk_kj"></a> SQL Server 2008 R2 Reporting Services における動作変更  
 このセクションの動作の変更を説明します[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]します。  
  
> [!NOTE]  
>  SQL Server 2008 R2 は SQL Server 2008 のマイナー バージョン アップグレードなので、SQL Server 2008 のセクションのコンテンツも確認することをお勧めします。  
  
### <a name="secureconnectionlevel-property-in-the-reporting-services-wmi-provider-library"></a>Reporting Services WMI プロバイダー ライブラリの SecureConnectionLevel プロパティ  
 WMI プロバイダー ライブラリで[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]、 **SecureConnectionLevel**プロパティの値を許可する`0`、`1`、`2`、`3`で`0`Secure Socket Layer (SSL) が、Web サービス メソッドのいずれかの必要ないことを示す`3`SSL が必要なすべての Web サービス メソッドであることを示すと`1`と`2`Web サービス メソッドのサブセットを示しますSSL を必要とします。 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]、これらの値が 2 つだけの可能性のある意味になります。  
  
-   `0` は、いずれの Web サービス メソッドでも SSL が不要であることを示します。  
  
-   正の整数は、すべての Web サービス メソッドで SSL が必要であることを示します。  
  
 この変更によって、レポート サーバーが Web サービス呼び出しに応答する方法に影響が及びます。 たとえば、<xref:ReportService2005.ReportingService2005.ListSecureMethods%2A>何も返すようになりました場合**SecureConnectionLevel** 0 とのすべてのメソッドに設定されている<xref:ReportService2005.ReportingService2005>場合**SecureConnectionLevel**に設定されている`1`、 `2`、または`3`します。  
  
## <a name="see-also"></a>参照  
 [新機能については&#40;Reporting Services&#41;](what-s-new-reporting-services.md)   
 [SQL Server 2014 における SQL Server Reporting Services の非推奨の機能](deprecated-features-in-sql-server-reporting-services-ssrs.md)   
 [SQL Server Reporting Services SQL Server 2014 で廃止された機能](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)   
 [SQL Server 2014 における SQL Server Reporting Services における重大な変更](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)  
  
  
