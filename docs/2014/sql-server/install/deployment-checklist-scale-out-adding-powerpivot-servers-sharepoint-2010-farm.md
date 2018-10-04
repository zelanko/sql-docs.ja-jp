---
title: 'SharePoint 2010 ファームに PowerPivot サーバーの追加による配置のチェックリスト: スケール アウト |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 2dbddcc7-427a-4537-a8e2-56d99b9d967d
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 9a9e726aea4428ac061ca57a4c1bc28199492492
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218138"
---
# <a name="deployment-checklist-scale-out-by-adding-powerpivot-servers-to-a-sharepoint-2010-farm"></a>SharePoint 2010 ファームに PowerPivot サーバーの追加による配置のチェックリスト: スケール アウト
  SharePoint ファーム内で PowerPivot クエリ処理の要求が大量になることが予想される場合は、PowerPivot for SharePoint のインスタンスを追加して、新規クエリやデータ処理に対するサポート性能をシームレスに追加することができます。  
  
 新しいインスタンスをインストールすると、PowerPivot データのクエリや PowerPivot データの更新ジョブに対する処理容量が増加します。 必要に応じて、各サーバーで特定の種類の要求 (クエリまたはデータ更新) だけを処理することもできます。  
  
## <a name="prerequisites"></a>前提条件  
 SharePoint Server 2010 がインストールおよび構成されている。  
  
 SharePoint Server 2010 SP1 が適用され、ファームがアップグレードされている。  
  
 ファーム内の既存の PowerPivot for SharePoint インスタンスが [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (新規インストールか、または SQL Server 2008 R2 からのアップグレード) である。  
  
 新しい [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] PowerPivot for SharePoint サーバーのインストール先となるコンピューターが、ファームに参加している。 ファーム内のコンピューターとその他のサーバーは、同じドメインに属する必要があります。  
  
 次の追加トピックを確認し、システムとバージョンの要件を理解してください。  
  
-   [SharePoint 2010 ファームで SQL Server BI 機能を使用するためのガイド](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
> [!NOTE]  
>  マルチサーバー ファームでは、すべての PowerPivot for SharePoint インスタンスのバージョンが同じである必要があります。 ファーム内にある他の既存の PowerPivot サーバーにサービス パックや更新プログラムが適用されている場合は、追加する新しいインスタンスも、ファーム内の既存のインスタンスと同じバージョンに更新する必要があります。 新しいインスタンスは、アップグレードが適用されるまで利用できません。  
  
## <a name="steps"></a>手順  
 このチェック リストを使用して、SharePoint ファームに PowerPivot サーバーを追加します。 この手順では、ファーム内に既に PowerPivot for SharePoint サーバーが 1 つ存在し、2 番目のサーバーを追加して処理負荷の増加に対処することを想定しています。 インストール要件、インストール後の構成、および確認の内容が異なる点を除いて、スケールアウト ソリューションの配置手順は、既存のファームに 1 つの PowerPivot サーバーを追加する場合と同じです。  
  
|手順|リンク|  
|----------|----------|  
|ファーム内に既に存在している Analysis Services インスタンスのサービス アカウントを確認する|インストールする各追加インスタンスは、1 つ目のインスタンスと同じアカウントで実行される必要があります。 次のどちらかの方法でサービス アカウントを確認します。<br /><br /> セキュリティ セクションのサーバーの全体管理 をクリックして**サービス アカウントの構成**します。 選択**Windows サービス – SQL Server Analysis Services**します。 サービスを選択すると、サービス アカウント名がページに表示されます。<br /><br /> 既に PowerPivot サービスをインストールするサーバーで開く、**サービス**コンソール管理ツールでのアプリケーション。 ダブルクリック**SQL Server Analysis Services**します。 をクリックして、**ログオン**タブには、サービス アカウントを表示します。<br />**\*\* 重要な\* \*** のみサービス アカウントを変更するサーバーの全体管理を使用します。 別のツールまたは方法を使用する場合のアクセス許可は更新されません正しく、ファーム内。|  
|セットアップを実行して、PowerPivot for SharePoint の 2 つ目のインスタンスをインストールする|[PowerPivot for SharePoint 2010 をインストールする](../../../2014/sql-server/install/install-powerpivot-for-sharepoint-2010.md)<br /><br /> ファームに参加していてサーバー上に既存の PowerPivot インスタンスがないアプリケーション サーバーを選択します。<br /><br /> セットアップ中、サービス アカウントを指定するよう求められた場合は、前の手順のアカウントを入力します。 Analysis Services サービスのすべてのインスタンスは、同じドメイン アカウントで実行される必要があります。 この要件を満たすことにより、SharePoint の管理アカウント機能を使用できるようになります。これによって、1 つの場所のパスワードを同じ種類のすべてのサービス インスタンスに対して更新できるようになります。|  
|2 つ目のインスタンスを構成する|どちらの方法を使用するには、インスタンスを構成する: [PowerPivot 構成ツール](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools.md)または[Windows PowerShell を使用した PowerPivot の構成](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell.md)<br /><br /> 2 つ目のインスタンスを構成するときに必要なのは、ローカル サービスのプロビジョニングだけです。 その他すべての構成タスク (サービス アプリケーションの作成やデータ更新の構成など) は最初の構成時に実行され、後続のインスタンスのインストール時にはそれらが使用されます。|  
|インストール後のタスク|以降の手順は具体的には必要ありません。 サービス アプリケーションの作成、機能のアクティブ化、ソリューションの配置、サービス アプリケーション ID の変更を行う必要はありません。 既存の Web アプリケーションやサービス アプリケーションで、新しいサーバー ソフトウェアが自動的に検出されて使用されます。<br /><br /> 一方のサーバーをクエリ専用にし、もう一方のサーバーをデータ更新専用にする目的で 2 番目のサーバーをインストールした場合は、ここでサーバー インスタンスのプロパティを構成し、各サーバーで処理する要求の種類を指定できます。 詳細については、次を参照してください。[専用のデータ更新の構成または Query-Only 処理&#40;PowerPivot for SharePoint&#41;](../../analysis-services/configure-dedicated-data-refresh-query-only-processing-powerpivot-sharepoint.md)します。|  
|2 つ目のインスタンスがインストールされたことを確認する|インストールしたサーバー上で PowerPivot クエリが正常に処理されることを確認するには、次の手順を実行します。<br /><br /> 1) サーバーの全体管理で、サービスの管理サーバーとそのサービスが表示されることを確認するサーバーのページを開きます。<br />サーバーで下矢印をクリックして、[サーバーの変更] をクリックし、新しい PowerPivot for SharePoint のインストールされているサーバーを選択します。<br />-SQL Server Analysis Services と SQL Server PowerPivot System サービスが開始されたことを確認します。<br /><br /> 2) サーバーの全体管理では、インストールしたサーバーが、1 つだけ使用できるように他の PowerPivot for SharePoint サーバーを停止します。 詳細については、次を参照してください。[開始または PowerPivot を SharePoint サーバーの停止](../../analysis-services/power-pivot-sharepoint/start-or-stop-a-power-pivot-for-sharepoint-server.md)します。<br /><br /> 3) ライブラリから開く PowerPivot ブックをクリックします。<br /><br /> 4)、スライサーをクリックするか、クエリを開始するデータをピボットします。 サーバーにバックグラウンドで PowerPivot データが読み込まれます。 次の手順で、サーバーに接続して、データの読み込みとキャッシュが行われたことを確認します。<br /><br /> 5)、[スタート] メニューで、Microsoft SQL Server プログラム グループから SQL Server Management Studio を起動します。 サーバーでこのツールがインストールされていない場合は、手順を省略できます最後をキャッシュ ファイルの存在を確認します。<br /><br /> 6) でサーバーの種類を選択します。 **Analysis Services**します。<br /><br /> 7) でサーバー名では、次のように入力します。 **\<サーバー名 > \powerpivot**ここで、 **\<サーバー名 >** 、新しい powerpivot for SharePoint のインストールするコンピューターの名前を指定します。<br /><br /> 8) クリック**接続**します。<br /><br /> 9) でオブジェクト エクスプ ローラーで、次のようにクリックします。**データベース**読み込まれる PowerPivot データ ファイルの一覧を表示します。<br /><br /> 10) でコンピューターのファイル システム、ファイルをキャッシュするかどうかを判断する次のフォルダーをチェック ディスクにします。 キャッシュされたファイルが存在していれば、配置が機能していることの確認になります。 ファイル キャッシュを表示するには、\Program Files\Microsoft SQL Server\MSAS11.POWERPIVOT\OLAP\Backup フォルダーに移動します。<br /><br /> 11) 前に停止したサービスを再起動します。|  
  
## <a name="see-also"></a>参照  
 [構成の初期&#40;PowerPivot for SharePoint&#41;](../../../2014/sql-server/install/initial-configuration-powerpivot-for-sharepoint.md)   
 [PowerPivot for SharePoint 2010 のインストール](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)   
 [サーバーの全体管理での PowerPivot サーバーの管理と構成](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
  
