---
title: レポート サーバーの状態 (SSRS ネイティブ モード) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SQL12.rsconfigtool.serverstatus.F1
ms.assetid: 2f63ad1c-1bc2-449d-b451-fb39a0060838
caps.latest.revision: 14
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 914b5ffb0d7cbdfa2368966e110fe4d7ecf278ff
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075662"
---
# <a name="report-server-status-ssrs-native-mode"></a>レポート サーバーの状態 (SSRS ネイティブ モード)
  このページを使用すると、現在接続しているレポート サーバー インスタンスに関する情報を表示できます。 このページはレポート サーバー構成の開始ページです。 他のページでは、URL、サービス アカウント、レポート サーバーのデータベース、レポート サーバーの電子メール配信、スケールアウト配置、および暗号化キーを構成できます。  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード。  
  
 このページを開くには、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを起動して、レポート サーバー インスタンスに接続します。 詳細については、次を参照してください。 [Reporting Services 構成マネージャー &#40;del&#41;](/sql/2014/sql-server/install/reporting-services-configuration-manager-native-mode)です。  
  
> [!TIP]  
>  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]構成マネージャー (RSConfigTool.exe) は、"highestAvailable"の特権レベルと共にインストールします。 この動作は仕様による結果です。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI API と通信する必要があります。 一部の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]WMI 通信には、高いレベルまたは管理者の特権が必要です。  
  
 レポート サーバーに接続したときに、すべてのページ リンクがグレー表示されている場合は、レポート サーバー サービスが開始されていることを確認します。 **レポート サービスの状態** は "開始" にする必要があります。 また、サービスの状態を確認するには、管理ツールの [サービス] コンソール アプリケーションを使用します。  
  
## <a name="options"></a>および  
 **SQL Server インスタンス**  
 現在接続しているレポート サーバー インスタンスに関する情報が表示されます。 レポート サーバー インスタンスの名前がに基づいて[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]名前付きインスタンス。 既定のインスタンスは MSSQLSERVER です。 名前付きインスタンスは、セットアップ中に指定した値になります。 インスタンスの詳細については、次を参照してください。[複数のバージョンと SQL Server のインスタンスを操作](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md)で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オンライン ブック。  
  
> [!NOTE]  
>  SQL Server Express with Advanced Services の既定のインスタンスは SQLExpress です。  
  
 **インスタンス ID**  
 接続先の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのプログラム ファイルを格納する、ファイル システム上のフォルダーに対応します。 **インスタンス ID**形式で値がセットアップによって割り当てられている*コンポーネント*.*インスタンス*ここで、*コンポーネント*を示す値を、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンポーネントと*インスタンス*インスタンスの名前を指定します。 既定のインスタンス名は MSSQLSERVER です。 既定のインスタンスをインストールする場合など、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、および[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]コンポーネント、対応するフォルダー名が次に示します。  
  
-   MSSQL12.MSSQLSERVER  
  
-   MSAS12.MSSQLSERVER  
  
-   MSRS12.MSSQLSERVER  
  
 インストール済みであるなど、コンポーネントの 2 番目のインスタンスをインストールする場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、し、そのインスタンスに Contoso の名前、**インスタンス ID** MSSQL12 がします。Contoso です。  
  
 **のエディション**  
 エディション情報が表示されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の各エディションでサポートされる機能の一覧については、「 [SQL Server の各エディションがサポートする機能](http://go.microsoft.com/fwlink/?linkid=232473)」を参照してください。  
  
 **製品バージョン**  
 バージョンを表示[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]インストールされています。  
  
 **レポート サーバー データベース**  
 現在のレポート サーバー インスタンスのアプリケーション データを格納しているレポート サーバー データベースの名前が表示されます。  
  
 **レポート サーバー モード**  
 常に値 **Native**が表示されます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration manager では、ネイティブ モードのレポート サーバーのみがサポートされます。 **[SharePoint 統合モード]** という値が表示されている場合は、ネイティブ モードの配置が正しく構成されていないことを示しています。そのため、ネイティブ モードのレポート カタログに接続する必要があります。 構成マネージャーの **[データベース]** ページを使用してデータベースを変更し、データベースを新規作成するか、ネイティブ モードのレポート サーバーの既存のレポート カタログに接続します。  
  
 **サーバーの状態**  
 レポート サーバー サービスが実行中かどうかを示します。  
  
 **コントロール パネルの  ◆セグ : 文が分断されているため、訳の位置が入れ替わっています◇**  
 レポート サーバー サービスを開始します。 たとえば、コンピューター名が変更された後でレポート サーバーを再度構成するときなど、構成を変更した後は、このサービスを再起動する必要があります。 URL 予約を再構成すると、サービスは自動的に再起動されます。 変更を取得するには、サービスを再起動する必要があります。  
  
 **[停止]**  
 レポート サーバー サービスを停止します。 サービスを停止すると、レポート サーバーの動作が停止します。 詳細については、次を参照してください。[を起動し、レポート サーバー サービスを停止](../../reporting-services/report-server/start-and-stop-the-report-server-service.md)で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オンライン ブック。  
  
## <a name="see-also"></a>参照  
 [Reporting Services 構成マネージャーの F1 ヘルプ トピック&#40;SSRS ネイティブ モード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Reporting Services 構成マネージャー &#40;del&#41;](/sql/2014/sql-server/install/reporting-services-configuration-manager-native-mode)   
 [レポート サーバーの初期化 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)  
  
  
