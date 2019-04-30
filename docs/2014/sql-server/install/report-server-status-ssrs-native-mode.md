---
title: レポート サーバーの状態 (SSRS ネイティブ モード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.serverstatus.F1
ms.assetid: 2f63ad1c-1bc2-449d-b451-fb39a0060838
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 217fc6d3d5a94fb443ea262563255c10bcfc2dda
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63057955"
---
# <a name="report-server-status-ssrs-native-mode"></a>レポート サーバーの状態 (SSRS ネイティブ モード)
  このページを使用すると、現在接続しているレポート サーバー インスタンスに関する情報を表示できます。 このページはレポート サーバー構成の開始ページです。 他のページでは、URL、サービス アカウント、レポート サーバーのデータベース、レポート サーバーの電子メール配信、スケールアウト配置、および暗号化キーを構成できます。  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード。  
  
 このページを開くには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを起動して、レポート サーバー インスタンスに接続します。 詳細については、次を参照してください。 [Reporting Services 構成マネージャー &#40;del&#41;](reporting-services-configuration-manager-native-mode.md)します。  
  
> [!TIP]  
>  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] "HighestAvailable"の特権レベルで構成マネージャー (RSConfigTool.exe) がインストールされています。 この動作は仕様による結果です。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI API と通信する必要があります。 一部の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI 通信には、高いレベルまたは管理者の特権が必要です。  
  
 レポート サーバーに接続したときに、すべてのページ リンクがグレー表示されている場合は、レポート サーバー サービスが開始されていることを確認します。 **レポート サービスの状態。**「開始」にします。 また、サービスの状態を確認するには、管理ツールの [サービス] コンソール アプリケーションを使用します。  
  
## <a name="options"></a>および  
 **SQL Server インスタンス**  
 現在接続しているレポート サーバー インスタンスに関する情報が表示されます。 レポート サーバー インスタンスの名前は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の名前付きインスタンスに基づいています。 既定のインスタンスは MSSQLSERVER です。 名前付きインスタンスは、セットアップ中に指定した値になります。 インスタンスの詳細については、次を参照してください。[複数のバージョンと SQL Server のインスタンスを操作](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md)で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オンライン ブックの「します。  
  
> [!NOTE]  
>  SQL Server Express with Advanced Services の既定のインスタンスは SQLExpress です。  
  
 **インスタンス ID**  
 接続先の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのプログラム ファイルを格納する、ファイル システム上のフォルダーに対応します。 **[インスタンス ID]** の値は、セットアップによって *component*.*instance*の形式で割り当てられます。この形式で、 *component* は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントを示す値、 *instance* はインスタンス名です。 既定のインスタンス名は MSSQLSERVER です。 たとえば、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のコンポーネントの既定のインスタンスをインストールした場合、それぞれに対応するフォルダー名は次のようになります。  
  
-   MSSQL12.MSSQLSERVER  
  
-   MSAS12.MSSQLSERVER  
  
-   MSRS12.MSSQLSERVER  
  
 コンポーネントを既にインストールされているなどの 2 番目のインスタンスをインストールする場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、し、そのインスタンスに Contoso の名前、**インスタンス ID** MSSQL12 です。Contoso です。  
  
 **のエディション**  
 エディション情報が表示されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の各エディションでサポートされる機能の一覧については、「 [SQL Server の各エディションがサポートする機能](https://go.microsoft.com/fwlink/?linkid=232473)」を参照してください。  
  
 **製品バージョン**  
 インストールした [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のバージョンが表示されます。  
  
 **レポート サーバー データベース**  
 現在のレポート サーバー インスタンスのアプリケーション データを格納しているレポート サーバー データベースの名前が表示されます。  
  
 **レポート サーバー モード**  
 常に値 **Native**が表示されます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーでサポートされているのはネイティブ モード レポート サーバーだけです。 **[SharePoint 統合モード]** という値が表示されている場合は、ネイティブ モードの配置が正しく構成されていないことを示しています。そのため、ネイティブ モードのレポート カタログに接続する必要があります。 構成マネージャーの **[データベース]** ページを使用してデータベースを変更し、データベースを新規作成するか、ネイティブ モードのレポート サーバーの既存のレポート カタログに接続します。  
  
 **サーバーの状態**  
 レポート サーバー サービスが実行中かどうかを示します。  
  
 **コントロール パネルの  ◆セグ : 文が分断されているため、訳の位置が入れ替わっています◇**  
 レポート サーバー サービスを開始します。 たとえば、コンピューター名が変更された後でレポート サーバーを再度構成するときなど、構成を変更した後は、このサービスを再起動する必要があります。 URL 予約を再構成すると、サービスは自動的に再起動されます。 変更を取得するには、サービスを再起動する必要があります。  
  
 **[停止]**  
 レポート サーバー サービスを停止します。 サービスを停止すると、レポート サーバーの動作が停止します。 詳細については、次を参照してください。[を起動し、レポート サーバー サービスを停止](../../reporting-services/report-server/start-and-stop-the-report-server-service.md)で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オンライン ブックの「します。  
  
## <a name="see-also"></a>参照  
 [Reporting Services 構成マネージャーの F1 ヘルプ トピック&#40;SSRS ネイティブ モード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Reporting Services 構成マネージャー &#40;del&#41;](/sql/2014/sql-server/install/reporting-services-configuration-manager-native-mode)   
 [レポート サーバーの初期化 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)  
  
  
