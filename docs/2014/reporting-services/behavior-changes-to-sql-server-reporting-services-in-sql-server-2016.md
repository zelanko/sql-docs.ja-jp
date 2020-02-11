---
title: SQL Server 2014 | での SQL Server Reporting Services の動作の変更Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
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
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 91fa7a66981f3e36c7e25babffbf73dc2519a0c2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66109939"
---
# <a name="behavior-changes-to-sql-server-reporting-services--in-sql-server-2014"></a>SQL Server 2014 における SQL Server Reporting Services の動作変更
  このトピックでは、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]における動作変更について説明します。 動作変更によって、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] の以前のバージョンに比べて、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の機能の動作や操作方法が変わります。  
  
 このトピックの内容:  
  
-   [SQL Server 2014 Reporting Services 動作の変更](#bkmk_sql14)  
  
-   [SQL Server 2012 Reporting Services における動作変更](#bkmk_rc0)  
  
-   [SQL Server 2008 R2 Reporting Services における動作変更](#bkmk_kj)  
  
##  <a name="bkmk_sql14"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Reporting Services 動作の変更  
 
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] では、 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]の動作に変更はありません。  
  
##  <a name="bkmk_rc0"></a>[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Reporting Services 動作の変更  
 ここでは、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint モードでの動作変更について説明します。  
  
### <a name="view-items-permission-will-not-download-shared-datasets-sharepoint-mode"></a>"アイテムの表示" 権限によって共有データセットがダウンロードされない (SharePoint モード)  
 **新しい動作:**"アイテムの表示" 権限を持つユーザーは、Reporting Services 共有データセットのコンテンツをダウンロードできなくなります。 この動作変更は、レポート、データソース、およびモデルに対する "アイテムの表示" 権限と一致するようになりました。 "アイテムの表示" 権限を持つユーザーは、レポート、データソース、およびモデルを表示および実行できますが、コンテンツをダウンロードすることはできません。  
  
 **以前の動作:** SharePoint の "アイテムの表示" 権限を持つユーザーは Reporting Services 共有データセットの内容をダウンロードできます。  
  
 SharePoint 権限レベルの詳細については、「 [ユーザー権限とアクセス許可レベル](https://technet.microsoft.com/library/cc721640.aspx)」を参照してください。  
  
### <a name="report-server-trace-logs-are-in-a-new-location-for-sharepoint-mode-sharepoint-mode"></a>SharePoint モードでは Report Server のトレース ログが新しい場所に置かれる (SharePoint モード)  
 **新しい動作:** SharePoint モードでインストールされたレポートサーバーの場合、レポートサーバーのトレースログは%Programfiles%\Common の Shared\Web Server Extensions\14\Web Services\ReportServer\LogFiles. にあります。  
  
 **以前の動作:** レポートサーバーのトレースログは、次のようなパスで見つかりました\\ :%Programfilesdir%\Microsoft SQL Server<RS_instance> \ Reporting Services\LogFiles  
  
### <a name="getserverconfiginfo-soap-api-is-no-longer-supported-sharepoint-mode"></a>GetServerConfigInfo SOAP API がサポートされなくなった (SharePoint モード)  
 **新しい動作**: PowerShell コマンドレット "SPRSServiceApplicationServers" を使用します。  
  
 **以前の動作:**[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]エンドポイントと直接通信する SOAP クライアントコードを開発し、GetReportServerConfigInfo () を呼び出すことができます。  
  
### <a name="report-server-configuration-and-management-tools"></a>レポート サーバーの構成と管理のツール  
  
#### <a name="configuration-manager-is-not-used-for-sharepoint-mode"></a>SharePoint モードで構成マネージャーが使用されない  
 **新しい動作:** Configuration Manager [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]では、SharePoint モードのレポートサーバーがサポートされなくなりました。 
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint モードの構成は、SharePoint サーバーの全体管理を使用して完了できるようになったため、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 構成マネージャーでは SharePoint モードはサポートされなくなりました。 構成マネージャーは今後、ネイティブ モードのレポート サーバーに対してのみ使用されます。  
  
#### <a name="you-cannot-change-the-server-from-one-mode-to-another"></a>サーバーを別のモードに変更できない  
 **新しい動作:** サーバーモードを変更することはできません。 レポート サーバーをネイティブ モードとしてインストールした場合、それを変更または再構成して SharePoint モードにすることはできません。 SharePoint モードでインストールした場合は、レポート サーバーをネイティブ モードに変更できます。  
  
 **以前の動作:** 顧客は、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]レポートサーバーを SharePoint モードでインストールします。 レポート サーバーをネイティブ モードに切り替えたい場合は、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 構成マネージャーを開き、新しいネイティブ モード データベースを作成するか、または既存のネイティブ モード データベースに接続することで、ネイティブ モードに切り替えることができました。 また、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 構成マネージャーを使用して、SharePoint モードからネイティブ モードに切り替えることもできました。  
  
##  <a name="bkmk_kj"></a>SQL Server 2008 R2 Reporting Services 動作の変更  
 ここでは、 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]の動作変更について説明します。  
  
> [!NOTE]  
>  SQL Server 2008 R2 は SQL Server 2008 のマイナー バージョン アップグレードなので、SQL Server 2008 のセクションのコンテンツも確認することをお勧めします。  
  
### <a name="secureconnectionlevel-property-in-the-reporting-services-wmi-provider-library"></a>Reporting Services WMI プロバイダー ライブラリの SecureConnectionLevel プロパティ  
 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]の WMI プロバイダーライブラリでは、 **secureconnectionlevel**プロパティによっ`0`て`1``2``3` `0` 、、、、、のいずれかの web サービスメソッドで ssl (Secure Socket Layer) が不要であることが`3`示されています。これは、すべての web サービス`1`メソッド`2`に ssl が必要であることを示し、ssl を必要とする web サービスメソッドのサブセットを示します。 で[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]は、これらの値は次の2つの意味を持つことができます。  
  
-   
  `0` は、いずれの Web サービス メソッドでも SSL が不要であることを示します。  
  
-   正の整数は、すべての Web サービス メソッドで SSL が必要であることを示します。  
  
 この変更によって、レポート サーバーが Web サービス呼び出しに応答する方法に影響が及びます。 <xref:ReportService2005.ReportingService2005.ListSecureMethods%2A>たとえば、 **secureconnectionlevel**が0に設定されていて、 <xref:ReportService2005.ReportingService2005> **secureconnectionlevel**が、 `1` `2`、または`3`に設定されている場合、は何も返さないようになりました。  
  
## <a name="see-also"></a>参照  
 [新機能 &#40;Reporting Services&#41;](what-s-new-reporting-services.md)   
 [SQL Server 2014 の SQL Server Reporting Services の非推奨の機能](deprecated-features-in-sql-server-reporting-services-ssrs.md)   
 [SQL Server 2014 で SQL Server Reporting Services が廃止された機能](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)   
 [SQL Server 2014 における SQL Server Reporting Services の重大な変更](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)  
  
  
