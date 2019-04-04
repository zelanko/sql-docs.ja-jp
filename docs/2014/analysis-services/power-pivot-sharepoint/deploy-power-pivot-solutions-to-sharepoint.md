---
title: SharePoint に PowerPivot ソリューションの配置 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: f202a2b7-34e0-43aa-90d5-c9a085a37c32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: af3b98aab31aeaa3a01b1026eca8b3098ce97bef
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52515971"
---
# <a name="deploy-powerpivot-solutions-to-sharepoint"></a>SharePoint への PowerPivot ソリューションの配置
  SharePoint Server 2010 環境に PowerPivot 機能を追加する 2 つのソリューション パッケージを手動で配置するには、次の手順に従います。 ソリューションの配置は、SharePoint 2010 サーバー上で PowerPivot for SharePoint を構成するために必要な手順です。 必要な手順の完全な一覧を表示するには、[サーバーの全体管理で PowerPivot サーバーの管理と構成](power-pivot-server-administration-and-configuration-in-central-administration.md)を参照してください。  
  
 ソリューションの配置には、PowerPivot 構成ツールを使用することもできます。 シングル サーバー インストールでは構成ツールを使用するのが簡単で効率的ですが、使い慣れたツールを使用したい場合や、複数の機能を同時に構成する場合は、サーバーの全体管理と PowerShell を使用することもできます。 詳細については、構成ツールを使用して、[PowerPivot 構成ツール](power-pivot-configuration-tools.md)を参照してください。  
  
 ソリューションを配置する前に、まず、SQL Server 2012 インストール メディアを使用して、PowerPivot for SharePoint をインストールする必要があります。 SQL Server セットアップでは、配置しようとしているソリューション パッケージがインストールされます。  
  
 このトピックには、次のセクションが含まれます。  
  
 [前提条件:Web アプリケーションがクラシック モード認証を使用することを確認します。](#bkmk_classic)  
  
 [ステップ 1: ファーム ソリューションを配置します。](#bkmk_farm)  
  
 [手順 2:サーバーの全体管理の PowerPivot Web アプリケーション ソリューションを配置します。](#deployCA)  
  
 [手順 3:他の Web アプリケーションに PowerPivot Web アプリケーション ソリューションを配置します。](#deployUI)  
  
 [ソリューションの再配置または取り消し](#retract)  
  
 [PowerPivot ソリューションの概要](#intro)  
  
##  <a name="bkmk_classic"></a> 前提条件:Web アプリケーションでクラシック モード認証が使用されていることを確認する  
 PowerPivot for SharePoint は、Windows クラシック モード認証を使用する Web アプリケーションでのみサポートされます。 アプリケーションがクラシック モードを使用しているかどうかを確認するから次の PowerShell コマンドレットを実行、 **SharePoint 2010 管理シェル**、 `http://<top-level site name>` SharePoint サイトの名前に置き換えます。  
  
```  
Get-spwebapplication http://<top-level site name> | format-list UseClaimsAuthentication  
```  
  
 戻り値が **false**になる必要があります。 場合は**true**、この web アプリケーションでの PowerPivot データにアクセスすることはできません。  
  
##  <a name="bkmk_farm"></a> 手順 1:ファーム ソリューションを配置します。  
 このセクションでは、PowerShell を使用したソリューションの配置方法を紹介しますが、同じタスクを PowerPivot 構成ツールを使用して実行することもできます。 詳細については、[構成または修復の PowerPivot for SharePoint 2010 &#40;PowerPivot 構成ツール&#41;](../configure-repair-powerpivot-sharepoint-2010.md)を参照してください。  
  
 このタスクは、PowerPivot for SharePoint をインストールした後で、一度だけ実行する必要があります。  
  
1.  SharePoint の PowerPivot のインストールをされているサーバーで SharePoint 2010 管理シェルを使用して、開き、**管理者として実行**オプション。  
  
2.  次のコマンドレットを実行してファーム ソリューションを追加します。  
  
    ```  
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotFarm.wsp"  
    ```  
  
     コマンドレットにより、ソリューション名、ソリューション ID、および Deployed=False が返されます。 次の手順では、ソリューションを配置します。  
  
3.  次のコマンドレットを実行してファーム ソリューションを配置します。  
  
    ```  
    Install-SPSolution -Identity PowerPivotFarm.wsp -GACDeployment -Force  
    ```  
  
##  <a name="deployCA"></a> 手順 2:サーバーの全体管理の PowerPivot Web アプリケーション ソリューションを配置します。  
 ファーム ソリューションを配置した後で、サーバーの全体管理に Web アプリケーション ソリューションを配置する必要があります。 この手順によって、サーバーの全体管理に PowerPivot 管理ダッシュボードが追加されます。  
  
1.  **[管理者として実行]** オプションを使用して SharePoint 2010 管理シェルを開きます。  
  
2.  次のコマンドレットを実行して、サーバーの全体管理への参照を作成します。  
  
    ```  
    $centralAdmin = $(Get-SPWebApplication -IncludeCentralAdministration | Where { $_.IsAdministrationWebApplication -eq $TRUE})  
    ```  
  
3.  次のコマンドレットを実行してファーム ソリューションを追加します。  
  
    ```  
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotWebApp.wsp"  
    ```  
  
     コマンドレットにより、ソリューション名、ソリューション ID、および Deployed=False が返されます。 次の手順では、ソリューションを配置します。  
  
4.  次のコマンドレットを実行して、サーバーの全体管理に Web アプリケーション ソリューションをインストールします。  
  
    ```  
    Install-SPSolution -Identity PowerPivotWebApp.wsp -GACDeployment -Force -WebApplication $centralAdmin  
    ```  
  
 これで Web アプリケーション ソリューションがサーバーの全体管理に配置されたので、残りのすべての構成手順は、サーバーの全体管理を使用して実行できます。  
  
##  <a name="deployUI"></a> 手順 3:他の Web アプリケーションに PowerPivot Web アプリケーション ソリューションを配置します。  
 前のタスクでは、Powerpivotwebapp.wsp をサーバーの全体管理に配置しました。 ここでは、PowerPivot データ アクセスをサポートする既存の各 Web アプリケーションに powerpivotwebapp.wsp を配置します。 後でさらに Web アプリケーションを追加する場合は、それらの追加の Web アプリケーションに対して、この手順を繰り返してください。  
  
1.  サーバーの全体管理で、[システム設定] の **[ファーム ソリューションの管理]** をクリックします。  
  
2.  **[powerpivotwebapp.wsp]** をクリックします。  
  
3.  **[ソリューションの配置]** をクリックします。  
  
4.  **をデプロイしますか?**、PowerPivot 機能のサポートを追加する SharePoint web アプリケーションを選択します。  
  
5.  **[OK]** をクリックします。  
  
6.  PowerPivot データ アクセスをサポートする他の SharePoint Web アプリケーションに対して、この手順を繰り返します。  
  
##  <a name="retract"></a> ソリューションの再配置または取り消し  
 SharePoint サーバーの全体管理でソリューションの取り消しを実行できますが、インストールや修正プログラムの配置に関する問題のトラブルシューティングを体系的に行う場合を除いて、powerpivotwebapp.wsp ファイルを取り消す必要はありません。  
  
1.  SharePoint 2010 サーバーの全体管理で、[システム設定] の **[ファーム ソリューションの管理]** をクリックします。  
  
2.  **[powerpivotwebapp.wsp]** をクリックします。  
  
3.  **[ソリューションの取り消し]** をクリックします。  
  
 ファーム ソリューションに起因するサーバー配置の問題が発生した場合はこれを再配置を実行して、**修復**PowerPivot 構成ツールのオプション。 手動の手順が少なくて済むため、修復操作を行うときはこのツールを使用することをお勧めします。 詳細については、[構成または修復の PowerPivot for SharePoint 2010 &#40;PowerPivot 構成ツール&#41;](../configure-repair-powerpivot-sharepoint-2010.md)を参照してください。  
  
 すべてのソリューションを再配置する場合は、次の順序で実行してください。  
  
1.  PowerPivot Web アプリケーション ソリューションを使用しているすべての SharePoint Web アプリケーションでそのソリューションを取り消します。  
  
2.  PowerPivot ファーム ソリューションを取り消します。  
  
3.  PowerPivot ファーム ソリューションを再配置します。  
  
4.  PowerPivot Web アプリケーション ソリューションをすべての SharePoint Web アプリケーションに再配置します。  
  
##  <a name="intro"></a> PowerPivot ソリューションの概要  
 PowerPivot for SharePoint では、2 つのソリューション パッケージを使用して、アプリケーション ページとプログラム ファイルをファームおよび個々の Web アプリケーションに配置します。  
  
-   ファーム ソリューションはグローバルです。 このソリューションは一度配置するだけで、後でファームに追加する新しい PowerPivot for SharePoint サーバーで自動的に使用できるようになります。  
  
-   Web アプリケーション ソリューションはアプリケーション固有であり、サーバーの全体管理 Web アプリケーションを含め、ファーム内の各 Web アプリケーションに配置する必要があります。  
  
 各ソリューションは別々に配置します。  ファーム ソリューションは、最初の PowerPivot for SharePoint インスタンスのインストール後に一度だけ配置します。 ファーム ソリューションを配置するには、PowerPivot 構成ツールか PowerShell コマンドレットを使用します。  
  
 最初に Web アプリケーション ソリューションをサーバーの全体管理に配置し、その後で、PowerPivot データに対する要求をサポートする追加の Web アプリケーションに後のソリューションを配置します。 サーバーの全体管理 web アプリケーション ソリューションをデプロイするには、PowerPivot 構成ツールまたは PowerShell コマンドレットを使用する必要があります。 その他すべての Web アプリケーションには、サーバーの全体管理または PowerShell を使用して、Web アプリケーション ソリューションを手動で配置できます。  
  
|解決方法|説明|  
|--------------|-----------------|  
|powerpivotfarm.wsp|Microsoft.AnalysisServices.SharePoint.Integration.dll をグローバル アセンブリに追加する。<br /><br /> Microsoft.AnalysisServices.ChannelTransport.dll をグローバル アセンブリに追加する。<br /><br /> 機能とリソース ファイルをインストールし、コンテンツ タイプを登録する。<br /><br /> PowerPivot ギャラリー ライブラリやデータ フィード ライブラリのライブラリ テンプレートを追加する。<br /><br /> サービス アプリケーションの構成、PowerPivot 管理ダッシュボード、データ更新、および PowerPivot ギャラリー用のアプリケーション ページを追加する。|  
|[powerpivotwebapp.wsp]|Web フロントエンドの Web サーバー拡張機能フォルダーに Microsoft.AnalysisServices.SharePoint.Integration.dll リソース ファイルを追加する。<br /><br /> Web フロントエンドに PowerPivot Web サービスを追加する。<br /><br /> PowerPivot ギャラリーのサムネイル画像生成を追加する。|  
  
## <a name="see-also"></a>参照  
 [PowerPivot for SharePoint をアップグレードします。](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md)   
 [サーバーの全体管理で PowerPivot サーバーの管理と構成](power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [Windows PowerShell を使用した PowerPivot の構成](power-pivot-configuration-using-windows-powershell.md)  
  
  
