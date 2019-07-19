---
title: Power Pivot サーバーの管理とサーバーの全体管理の構成 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 87e2903607b476b04c44ac81ba337ea38e68a58b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68208073"
---
# <a name="power-pivot-server-administration-and-configuration-in-central-administration"></a>サーバーの全体管理での Power Pivot サーバーの管理と構成
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] サーバーの管理および構成は、SharePoint サービス アプリケーションの管理者が SharePoint サーバーの全体管理を使用して実行します。  
  
 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] for SharePoint を使用するには、このコンポーネントがあらかじめ構成されている必要があります。 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] for SharePoint は、SQL Server セットアップを使用してインストールした後、次のいずれかの方法を使用して構成できます。  
  
-   [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] 構成ツールまたは [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] for SharePoint 2013 構成ツール  
  
-   SharePoint サーバーの全体管理  
  
-   PowerShell コマンドレット  
  
 3 つの方法はすべて、完全に構成されたサーバーを提供します。  
  
 ここでは、サーバーの全体管理を使用してソフトウェアを構成するタスクについて説明します。 少なくとも、以下に示す 3 つの必須の構成タスクをすべて実行する必要があります。  
  
> [!IMPORTANT]  
>  SharePoint 2010 の場合は、 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] for SharePoint、または [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] データベース サーバーを使用する SharePoint ファームを構成する前に、SharePoint 2010 Service Pack 1 (SP1) をインストールする必要があります。 サービス パックをインストールしていない場合は、サーバーの構成を始める前にここでインストールしてください。  
  
## <a name="benefits-of-configuring-power-pivot-for-sharepoint-using-central-administration"></a>サーバーの全体管理を使用して PowerPivot for SharePoint を構成する利点  
 SharePoint サーバーの全体管理は、SharePoint ファームの管理アプリケーションです。 ファームの管理者は、 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] for SharePoint インスタンスをファームに追加するときに、使い慣れたツールの使用を好む場合があります。  
  
 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] 構成ツールや PowerShell コマンドレットとは対照的に、サーバーの全体管理には、アプリケーションまたはサーバーの構成時に設定できるすべてのオプションを完全に指定するページがあります。 他の方法では、構成ワークフローがより少数の手順に圧縮されるか、PowerShell を使用して SharePoint サーバーを構成する方法に関する知識が事前に必要です。  
  
## <a name="related-content"></a>関連コンテンツ  
 [Windows PowerShell を使用した Power Pivot の構成](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell.md)  
  
 [Power Pivot の構成ツール](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools.md)  
  
## <a name="related-tasks"></a>Related Tasks  
  
|リンク|種類|タスクの説明|  
|----------|----------|----------------------|  
|[SharePoint への PowerPivot ソリューションの配置](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md)|必須|この手順では、プログラム ファイルとアプリケーション ページをファームとサイト コレクションに追加するソリューション ファイルをインストールします。|  
|[サーバーの全体管理での Power Pivot サービス アプリケーションの作成および構成](../../analysis-services/power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md)|必須|この手順では、 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] System サービスを準備します。|  
|[サイト コレクションを対象とした Power Pivot 機能の統合をサーバーの全体管理でアクティブ化する方法](../../analysis-services/power-pivot-sharepoint/activate-power-pivot-integration-for-site-collections-in-ca.md)|必須|この手順では、サイト コレクション レベルで [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] 機能を有効にします。|  
|[Excel Services で信頼できるデータ プロバイダーとして MSOLAP.5 を追加](../../analysis-services/power-pivot-sharepoint/add-msolap-5-as-a-trusted-data-provider-in-excel-services.md)|必須|この手順では、Analysis Services OLE DB プロバイダーを Excel Services の信頼できるプロバイダーとして追加します。|  
|[SharePoint 2010 での Power Pivot データ更新](http://msdn.microsoft.com/01b54e6f-66e5-485c-acaa-3f9aa53119c9)|推奨|データの更新は省略可能ですが推奨されます。 パブリッシュされた Excel ブックで [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] データに自動更新をスケジュールできます。|  
|[Power Pivot 自動データ更新アカウントの構成 (Power Pivot for SharePoint)](http://msdn.microsoft.com/81401eac-c619-4fad-ad3e-599e7a6f8493)|推奨|この手順では、サーバー上でデータの更新ジョブを実行するために使用できる特別な目的のアカウントを準備します。|  
|[使用状況データ収集の構成 (Power Pivot for SharePoint)](../../analysis-services/power-pivot-sharepoint/configure-usage-data-collection-for-power-pivot-for-sharepoint.md)|省略可|使用状況データ コレクションは既定で構成されています。 これらの手順を使用して、既定の設定を変更できます。|  
|[データ更新専用またはクエリ専用処理の構成 (PowerPivot for SharePoint)](http://msdn.microsoft.com/5e027605-1086-4941-bb01-f315df8f829b)|Optional|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] インスタンスは、データ更新ジョブまたはクエリ専用にすることができます。 さらに、並列データ更新ジョブの既定の設定を変更できます。|  
|[Power Pivot サービス アカウントの構成](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts.md)|省略可|パスワードの更新とサービス アカウントの変更方法について説明します。|  
|[サーバーの全体管理での SharePoint Web アプリケーションへの PowerPivot サービス アプリケーションの接続](../../analysis-services/power-pivot-sharepoint/connect-power-pivot-service-app-to-sharepoint-web-app-in-ca.md)|省略可|サービスの関連付けを変更する方法について説明します。|  
|[サーバーの全体管理での Power Pivot サイト用の信頼できる場所の作成](../../analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)|省略可|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] ギャラリーを信頼できる場所として追加する方法について説明します。|  
|[SharePoint ログ ファイルと診断ログの構成と表示 (Power Pivot for SharePoint)](../../analysis-services/power-pivot-sharepoint/configure-and-view-sharepoint-and-diagnostic-logging.md)|Optional|イベントのログ記録は既定で構成されています。 これらの手順を使用して、既定の設定を変更できます。|  
|[Power Pivot の正常性ルールの構成](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-health-rules.md)|Optional|サーバーの正常性ルールは既定で構成されています。 これらの手順を使用して、既定の設定の一部を変更できます。|  
|[PowerPivot ギャラリーの作成およびカスタマイズ](../../analysis-services/power-pivot-sharepoint/create-and-customize-power-pivot-gallery.md)|省略可|インストールを手動で構成している場合は、この手順で、格納している [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] ブックのサムネイル画像を示す [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] ギャラリー ライブラリの作成方法を説明します。|  
|[BI セマンティック モデル接続のコンテンツ タイプのライブラリへの追加 (Power Pivot for SharePoint)](../../analysis-services/power-pivot-sharepoint/add-bi-semantic-model-connection-content-type-to-library.md)|省略可|BI セマンティック モデル接続ファイルの作成をサポートするようにドキュメント ライブラリを拡張する方法について説明します。|  
  
## <a name="see-also"></a>関連項目  
 [Power Pivot for SharePoint 2010 のインストール](http://msdn.microsoft.com/8d47dde7-c941-4280-a934-e2fe3f9a938f)   
 [構成設定のリファレンス (Power Pivot for SharePoint)](../../analysis-services/power-pivot-sharepoint/configuration-setting-reference-power-pivot-for-sharepoint.md)   
 [PowerPivot for SharePoint の障害復旧](http://go.microsoft.com/fwlink/p/?LinkId=389570)  
  
  
