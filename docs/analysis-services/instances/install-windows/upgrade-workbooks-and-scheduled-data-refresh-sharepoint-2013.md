---
title: "ブックと定期データ更新 (SharePoint 2013) のアップグレード |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- setup-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a49c4af4-e243-4926-be97-74da1f9d54eb
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b76561da72c6a4502f451d9ee39f8e9f90c97546
ms.sourcegitcommit: c77a8ac1ab372927c09bf241d486e96881b61ac9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2018
---
# <a name="upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013"></a>ブックのアップグレードと定期データ更新 (SharePoint 2013)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]このトピックの内容が以前に作成されたブックのユーザー エクスペリエンスについて説明します[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]環境およびアップグレードする方法[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]ブックのこのリリースで導入された新機能の利用できるようにします。 新機能の詳細については、「 [PowerPivot の新機能](http://go.microsoft.com/fwlink/?LinkID=203917)」を参照してください。  
  
> [!WARNING]  
>  サーバーで自動的にアップグレードされるブックのアップグレードをロールバックすることはできません。 ブックのアップグレードが完了すると、アップグレードされた状態のままになります。 以前のバージョンを使用するには、以前のブックを SharePoint に再パブリッシュするか、以前のバージョンを復元するか、ブックを再利用します。 SharePoint でのドキュメントの復元または再利用の詳細については、「 [ごみ箱とバージョン管理を使用したコンテンツ保護を計画する](http://go.microsoft.com/fwlink/?LinkId=238669)」を参照してください。  
  
  
##  <a name="bkmk_overview"></a> ブックのアップグレードの概要  
 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ブックは、埋め込みの [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] データを含んでいる Excel ブックです。 ブックのアップグレードには、次の 2 つの利点があります。  
  
-   [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)]の新機能を使用できます。  
  
-   SharePoint モードの [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] Analysis Services サーバーで実行されるブックの定期データ更新を有効にできます。  
  
> [!IMPORTANT]  
>  アップグレードしたブックはロールバックできないため、以前のバージョンの [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)]や [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)]でそのブックを使用することがある場合は、必ずコピーを作成しておいてください。  
  
 次の表に、ブックが作成された環境に基づく [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ブックのサポートおよび動作を示します。 この表では、一般的なユーザー エクスペリエンス、特定の環境にブックをアップグレードするときにサポートされるアップグレード オプション、およびアップグレードしていないブックの定期データ更新の動作について説明しています。  
  
### <a name="workbook-behavior-and-upgrade-options"></a>ブックの動作とアップグレード オプション  
  
|作成|\<|サポートおよび動作|>|  
|----------------|--------|--------------------------|--------|  
||**2008 R2 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2010**|**2012 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2010**|**2012 SP1 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2013**|  
|**2008 R2 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for Excel 2010**|すべての機能|**エクスペリエンス:** ユーザーはブラウザーでブックを操作し、他のソリューションのデータ ソースとして使用できます。<br /><br /> **アップグレード:** SharePoint ファームの [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] サービスで自動アップグレードが有効になっている場合、ドキュメント ライブラリのブックが自動アップグレードされます。<br /><br /> **定期データ更新:** サポートされていません。 ブックをアップグレードする必要があります。|**エクスペリエンス:** ユーザーはブックを操作し、他のソリューションのデータ ソースとして使用できます。<br /><br /> **アップグレード:** 自動アップグレードは使用できません。 SQL Server 2008 R2 ブックを、2012 バージョンまたは Office 2013 バージョンに手動でアップグレードする必要があります。<br /><br /> **定期データ更新:** サポートされていません。 ブックをアップグレードする必要があります。|  
|**2012 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for Excel**|サポートされていません|すべての機能|**エクスペリエンス:** ユーザーはブラウザーでブックを操作し、他のソリューションのデータ ソースとして使用できます。 定期データ更新を使用できます。<br /><br /> **アップグレード:** 自動アップグレードはサポートされていません。 手動でブックを Office 2013 バージョンにアップグレードできます。<br /><br /> **定期データ更新:** サポートされています。|  
|**Excel 2013**|サポートされていません|サポートされていません|すべての機能|  
  
##  <a name="bkmk_to_2012sp1_from_2008r2"></a> SQL Server 2008 R2 ブックから SQL Server 2012 Service Pack 1 (SP1) ブックへのアップグレード  
 ここでは、SQL Server 2008 R2 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for Excel 2010 ブックから、SQL Server 2012 SP1 の [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for Excel 2013 ブックへアップグレードする方法について説明します。  
  
 **動作変更:** SQL Server 2008 R2 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ブックを SQL Server 2012 SP1 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2013 で使用するときに、ブックは自動的にはアップグレードされません。 そのため、SQL Server 2008 R2 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ブックの定期データ更新は機能しません。  
  
 2008 R2 ブックは、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2013 で開きますが、定期データ更新は機能しません。 更新履歴を確認すると、次のようなエラー メッセージが表示されます。  
  
 ブックに、サポートされていない [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] モデルが含まれています。 ブックの [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] モデルは、SQL Server 2008 R2 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for Excel 2010 形式です。 次の [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] モデルがサポートされています。  
  
-   SQL Server 2012 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for Excel 2010  
  
-   SQL Server 2012 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for Excel 2013  
  
 **ブックをアップグレードする方法:** 定期データ更新は、ブックを 2012 ブックにアップグレードするまで機能しません。 ブックとブックに含まれるモデルをアップグレードするには、次のいずれかの手順を実行します。  
  
-   SQL Server 2012 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for Excel アドインがインストールされた Microsoft Excel 2010 でブックをダウンロードして開きます。  
  
     [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ウィンドウを開き、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] モデルをアップグレードします。  
  
     ブックを保存して、SharePoint に再発行します。  
  
-   Microsoft Excel 2013 でブックをダウンロードして開きます。  
  
     [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ウィンドウを開き、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] モデルをアップグレードします。  
  
     ブックを保存して、SharePoint サーバーに再発行します。  
  
 Analysis Services の機能の変更点に関する詳細については、「 [SQL Server 2016 における Analysis Services 機能の動作の変更](../../../analysis-services/behavior-changes-to-analysis-services-features-in-sql-server-2016.md)」を参照してください。  
  
 更新履歴の詳細については、「 [データ更新履歴の表示 &#40;Power Pivot for SharePoint&#41;](../../../analysis-services/power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md)」を参照してください。  
  
##  <a name="bkmk_to_2012sp1_from_2012"></a> SQL Server 2012 PowerPivot for Excel アドインで作成したブックから Office 2013 ブックへのアップグレード  
 ここでは、SQL Server 2012 **for Excel 2010 ブック** から [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] SQL Server 2012 SP1 **for Excel 2013 ブック** へ [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] アップグレードする方法について説明します。  
  
 ブックをアップグレードすると、以前のバージョンのブックで定期データ更新を試みると発生する、次のエラーが解決されます。  
  
 “前のバージョンの [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] で作成されたブックに対する更新操作は使用できません。”  
  
 **ブックをアップグレードする方法**  
  
1.  各ブックを Microsoft Excel 2013 で開き、手動でアップグレードします。  
  
2.  ブックとそれに含まれるモデルをアップグレードするには、Microsoft Excel 2013 でブックをダウンロードして開きます。  
  
3.  [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ウィンドウを開き、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] モデルをアップグレードします。  
  
4.  ブックを保存して、SharePoint 2013 サーバーに再発行します。  
  
##  <a name="bkmk_to_2012_from_2008R2"></a> SQL Server 2008 R2 PowerPivot for Excel 2010 で作成したブックから SQL Server 2012 ブックへのアップグレード  
 ここでは、SQL Server 2008 R2 **for Excel 2010 ブック** から [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] SQL Server 2012 **for Excel 2010** へ [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] アップグレードする方法について説明します。  
  
 ブックをアップグレードすると、以前のバージョンのブックで定期データ更新を試みると発生する、次のエラーが解決されます。  
  
 “前のバージョンの [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] で作成されたブックに対する更新操作は使用できません。”  
  
 **ブックをアップグレードする方法**  
  
 アップグレードには 2 つの方法があります。  
  
1.  [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] バージョンの [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for Excel がインストールされているコンピューターの Excel でブックを開いて各ブックを手動でアップグレードし、サーバーにブックを再発行します。 新しいバージョンのアドインでブックを開くと、内部でいくつかの処理が行われます。具体的には、ブックのデータ接続文字列でデータ プロバイダーが MSOLAP.5 に更新され、メタデータが更新され、新しい実装に対応するためにリレーションシップが再作成されます。  
  
2.  もう 1 つの方法では、SharePoint 管理者が SharePoint ファームの [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] System サービスの自動アップグレード機能を有効にして、定期データ更新が実行されると [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)][!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ブックが自動的にアップグレードされるようにできます (定期データ更新用に構成されているブックのみがアップグレードされます)。  
  
    > [!NOTE]  
    >  自動アップグレードは、サーバー構成機能です。特定のブック、ライブラリ、またはサイト コレクションについては有効または無効にできません。  
  
 **データ更新中に自動アップグレードを構成する方法**  
  
 自動アップグレードを使用するには、[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 構成ツールで **[[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ブックを自動的にアップグレードして、サーバーからのデータ更新を有効にする]** チェック ボックスをオンにする必要があります。 ツールでこのチェック ボックスがあるのは、**[[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] System サービスのアップグレード]** ページおよび新しいインストールを構成している場合の **[[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] サービス アプリケーションの作成]** ページです。  
  
 次のコマンドレットを実行して、自動アップグレードが有効かどうかを確認できます。  
  
```  
PS C:\Windows\system32> Get-PowerPivotSystemService  
```  
  
 Get-PowerPivotSystemService からの出力は、プロパティとそれに対応する値のリストです。 プロパティ リストの **WorkbookUpgradeOnDataRefresh** を確認してください。 自動アップグレードが有効になっている場合、値は **true** に設定されます。 **false**の場合は、次の手順を続行し、ブックの自動アップグレードを有効にします。  
  
 ブックの自動アップグレードを有効にするには、次のコマンドを実行します。  
  
```  
PS C:\Windows\system32> Set-PowerPivotSystemService –WorkbookUpgradeOnDataRefresh:$true –Confirm:$false  
```  
  
 ブックをアップグレードした後は、定期データ更新および [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for Excel アドインの新機能を使用できます。  
  
##  <a name="bkmk_runold"></a> 新しいサーバーでの複数バージョンのブックの実行  
 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] の [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] インスタンスでは、古いバージョンと新しいバージョンの [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)]ブックを同時に実行できます。  
  
 サーバーをインストールした方法によっては、つのサーバー上で古いブックと新しいブックにアクセスする前に、以前のバージョンの Analysis Services OLE DB プロバイダーのインストー**ルが必要になる場合があります**。  
  
 以前の [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] SQL Server インスタンスでの新しいバージョンのブックの発行はできません。 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] のインスタンスでは、 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] の [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)]バージョンで作成したブックは読み込まれません。SQL Server 2012 のインスタンスでは、Excel で [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] の [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] バージョンを使用して作成した高度なデータ モデルが含まれる Office 2013 ブックは読み込まれません。  
  
###  <a name="bkmk_msolapxslx"></a> PowerPivot ブックで MSOLAP データ プロバイダーの情報を確認する方法  
 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ブックで使用される OLE DB プロバイダーを確認するには、次の手順に従います。 データの接続情報を確認するために [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)] アドインをインストールする必要はありません。  
  
1.  Excel で、[データ] タブの **[接続]**をクリックします。 **[プロパティ]**をクリックします。  
  
2.  **[定義]** タブの接続文字列の先頭にプロバイダーのバージョンが表示されます。  
  
     **Provider=MSOLAP.5** は、ブックが [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]であることを示しています。  
  
     **Provider=MSOLAP.4** は [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]を示しています。  
  
     **Data Source=$Embedded$** は、ブックが埋め込みデータベースを使用する [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ブックであることを示しています。  
  
###  <a name="bkmk_msolappc"></a> ローカル コンピューターに MSOLAP データ プロバイダーの最新バージョンがインストールされていることを確認する方法  
 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ブックを実行するサーバーまたはワークステーションで最新バージョンの OLE DB プロバイダーを確認するには、次の手順に従います。 最新バージョンを確認しておくと、アップグレード後のデータ接続エラーのトラブルシューティングに役立ちます。  
  
1.  レジストリ エディターで、HKEY_CLASSES_ROOT に移動します。  
  
2.  MSOLAP まで下方向へスクロールします。 システムにインストールされている OLAP プロバイダーの中に MSOLAP.5 が含まれていることを確認します。 MSOLAP | CurVer が MSOLAP.5 に設定されていることを確認してください。  
  
## <a name="see-also"></a>参照  
 [SharePoint 2013 への Power Pivot の移行](../../../analysis-services/instances/install-windows/migrate-power-pivot-to-sharepoint-2013.md)   
 [Power Pivot for SharePoint のアップグレード](../../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md)   
 [Analysis Services の新機能](../../../analysis-services/what-s-new-in-analysis-services.md)   
 [ビューのデータ更新の履歴と #40 です。Power Pivot for SharePoint &#41;](../../../analysis-services/power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
  
