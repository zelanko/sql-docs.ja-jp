---
title: ブックのアップグレードと定期データ更新 (SharePoint 2013) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: a49c4af4-e243-4926-be97-74da1f9d54eb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 57fe740bdd02c96eb21994f5996c734620793616
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66079838"
---
# <a name="upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013"></a>ブックのアップグレードと定期データ更新 (SharePoint 2013)
  このトピックでは、以前の PowerPivot 環境で作成されたブックのユーザー エクスペリエンスについて、およびこのリリースで導入された新機能を利用できるよう、PowerPivot ブックをアップグレードする方法について説明します。 新機能の詳細については、「 [PowerPivot の新](https://go.microsoft.com/fwlink/?LinkID=203917)機能」を参照してください。  
  
> [!WARNING]  
>  サーバーで自動的にアップグレードされるブックのアップグレードをロールバックすることはできません。 ブックのアップグレードが完了すると、アップグレードされた状態のままになります。 以前のバージョンを使用するには、以前のブックを SharePoint に再パブリッシュするか、以前のバージョンを復元するか、ブックを再利用します。 SharePoint でのドキュメントの復元または再利用の詳細については、「 [ごみ箱とバージョン管理を使用したコンテンツ保護を計画する](https://go.microsoft.com/fwlink/?LinkId=238669)」を参照してください。  
  
 このトピックには、次のセクションが含まれます。  
  
-   [ブックのアップグレードの概要](#bkmk_overview)  
  
-   [2008 R2 ブックから SQL Server 2012 Service Pack 1 (SP1) ブックへのアップグレード](#bkmk_to_2012sp1_from_2008r2)  
  
-   [SQL Server 2012 の PowerPivot for Excel アドインで作成したブックから Office 2013 ブックへのアップグレード](#bkmk_to_2012sp1_from_2012)  
  
-   [SQL Server 2008 R2 の PowerPivot for Excel アドインで作成したブックから SQL Server 2012 ブックへのアップグレード](#bkmk_to_2012_from_2008R2)  
  
-   [新しいサーバーでの複数のブックバージョンの実行](#bkmk_runold)  
  
##  <a name="bkmk_overview"></a>ブックのアップグレードの概要  
 PowerPivot ブックは、PowerPivot データが埋め込まれた Excel ブックです。 ブックのアップグレードには、次の 2 つの利点があります。  
  
-   
  [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)]の新機能を使用できます。  
  
-   SharePoint モードの [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] Analysis Services サーバーで実行されるブックの定期データ更新を有効にできます。  
  
> [!IMPORTANT]  
>  アップグレードしたブックはロールバックできないため、以前のバージョンの [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)]や [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)]でそのブックを使用することがある場合は、必ずコピーを作成しておいてください。  
  
 次の表に、ブックが作成された環境に基づく PowerPivot ブックのサポートおよび動作を示します。 この表では、一般的なユーザー エクスペリエンス、特定の環境にブックをアップグレードするときにサポートされるアップグレード オプション、およびアップグレードしていないブックの定期データ更新の動作について説明しています。  
  
### <a name="workbook-behavior-and-upgrade-options"></a>ブックの動作とアップグレード オプション  
  
|作成|\<|サポートおよび動作|>|  
|----------------|--------|--------------------------|--------|  
||**SQL Server 2008 R2 の PowerPivot for SharePoint 2010**|**SQL Server 2012 の PowerPivot for SharePoint 2010**|**SQL Server 2012 SP1 の PowerPivot for SharePoint 2013**|  
|**2008 R2 PowerPivot for Excel 2010**|すべての機能|**エクスペリエンス:** ユーザーは、ブラウザーでブックを操作し、他のソリューションのデータソースとして使用することができます。<br /><br /> **アップグレード:** SharePoint ファームの PowerPivot system サービスで自動アップグレードが有効になっている場合、ドキュメントライブラリ内のブックは自動的にアップグレードされます。<br /><br /> **データ更新のスケジュール:** サポートされていません。 ブックをアップグレードする必要があります。|**エクスペリエンス:** ユーザーはブックを操作し、他のソリューションのデータソースとして使用することができます。<br /><br /> **アップグレード:** 自動アップグレードは使用できません。 SQL Server 2008 R2 ブックを、2012 バージョンまたは Office 2013 バージョンに手動でアップグレードする必要があります。<br /><br /> **データ更新のスケジュール:** サポートされていません。 ブックをアップグレードする必要があります。|  
|**2012 PowerPivot for Excel**|サポートされていません|すべての機能|**エクスペリエンス:** ユーザーは、ブラウザーでブックを操作し、他のソリューションのデータソースとして使用することができます。 定期データ更新を使用できます。<br /><br /> **アップグレード:** 自動アップグレードはサポートされていません。 手動でブックを Office 2013 バージョンにアップグレードできます。<br /><br /> **データ更新のスケジュール:** サポートされています。|  
|**Excel 2013**|サポートされていません|サポートされていません|すべての機能|  
  
##  <a name="bkmk_to_2012sp1_from_2008r2"></a>2008 R2 ブックから SQL Server 2012 Service Pack 1 (SP1) ブックへのアップグレード  
 ここでは、SQL Server 2008 R2 の PowerPivot for Excel 2010 ブックから、SQL Server 2012 SP1 の PowerPivot for Excel 2013 ブックへアップグレードする方法について説明します。  
  
 **動作の変更:** SQL Server 2008 R2 PowerPivot ブックは SQL Server 2012 SP1 PowerPivot for SharePoint 2013 で使用される場合、自動的にアップグレードされません。 そのため、SQL Server 2008 R2 の PowerPivot ブックの定期データ更新は機能しません。  
  
 2008 R2 ブックは、PowerPivot for SharePoint 2013 で開きますが、定期データ更新は機能しません。 更新履歴を確認すると、次のようなエラー メッセージが表示されます。  
  
 "ブックにサポートされていない PowerPivot モデルが含まれています。 ブックの PowerPivot モデルは、SQL Server 2008 R2 PowerPivot for Excel 2010 形式です。 サポートされている PowerPivot モデルは、  
  
-   SQL Server 2012 PowerPivot for Excel 2010  
  
-   または SQL Server 2012 PowerPivot for Excel 2013 です。」  
  
 **ブックをアップグレードする方法:** スケジュールされたデータ更新は、ブックを2012ブックにアップグレードするまで機能しません。 ブックとブックに含まれるモデルをアップグレードするには、次のいずれかの手順を実行します。  
  
-   SQL Server 2012 PowerPivot for Excel アドインがインストールされた Microsoft Excel 2010 でブックをダウンロードして開きます。  
  
     PowerPivot ウィンドウを開き、PowerPivot モデルをアップグレードします。  
  
     ブックを保存して、SharePoint に再発行します。  
  
-   Microsoft Excel 2013 でブックをダウンロードして開きます。  
  
     PowerPivot ウィンドウを開き、PowerPivot モデルをアップグレードします。  
  
     ブックを保存して、SharePoint サーバーに再発行します。  
  
 Analysis Services 機能の変更点の詳細については、「 [SQL Server 2014 の Analysis Services 機能に対する動作の変更](../../behavior-changes-to-analysis-services-features-in-sql-server-2014.md)」を参照してください。  
  
 更新履歴の詳細については、「[データ更新履歴の表示 &#40;PowerPivot for SharePoint&#41;](../../power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md)」を参照してください。  
  
##  <a name="bkmk_to_2012sp1_from_2012"></a>Excel 用の 2012 PowerPivot アドインを使用して作成されたバージョンから Office 2013 ブックにアップグレードする  
 このセクションで**は、** SQL Server 2012 Powerpivot for excel 2010 ブック**から**SQL Server 2012 SP1 PowerPivot In excel 2013 にアップグレードする方法について説明します。  
  
 ブックをアップグレードすると、以前のバージョンのブックで定期データ更新を試みると発生する、次のエラーが解決されます。  
  
 "以前のバージョンの PowerPivot で作成されたブックの更新操作は使用できません。"  
  
 **ブックをアップグレードする方法**  
  
1.  各ブックを Microsoft Excel 2013 で開き、手動でアップグレードします。  
  
2.  ブックとそれに含まれるモデルをアップグレードするには、Microsoft Excel 2013 でブックをダウンロードして開きます。  
  
3.  PowerPivot ウィンドウを開き、PowerPivot モデルをアップグレードします。  
  
4.  ブックを保存して、SharePoint 2013 サーバーに再発行します。  
  
##  <a name="bkmk_to_2012_from_2008R2"></a>Excel 2010 用 2008 R2 PowerPivot アドインを使用して作成されたバージョンから SQL Server 2012 ブックにアップグレードする  
 このセクションでは **、** SQL Server 2008 R2 Powerpivot for excel 2010 ブックから SQL Server 2012 Powerpivot for excel 2010 へ**の**アップグレードについて説明します。  
  
 ブックをアップグレードすると、以前のバージョンのブックで定期データ更新を試みると発生する、次のエラーが解決されます。  
  
 "以前のバージョンの PowerPivot で作成されたブックの更新操作は使用できません。"  
  
 **ブックをアップグレードする方法**  
  
 アップグレードには 2 つの方法があります。  
  
1.  
  [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] バージョンの PowerPivot for Excel がインストールされているコンピューターの Excel でブックを開いて各ブックを手動でアップグレードし、サーバーにブックを再発行します。 新しいバージョンのアドインでブックを開くと、内部でいくつかの処理が行われます。具体的には、ブックのデータ接続文字列でデータ プロバイダーが MSOLAP.5 に更新され、メタデータが更新され、新しい実装に対応するためにリレーションシップが再作成されます。  
  
2.  もう 1 つの方法では、SharePoint 管理者が SharePoint ファームの PowerPivot System サービスの自動アップグレード機能を有効にして、定期データ更新が実行されると [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] PowerPivot ブックが自動的にアップグレードされるようにできます (定期データ更新用に構成されているブックのみがアップグレードされます)。  
  
    > [!NOTE]  
    >  自動アップグレードは、サーバー構成機能です。特定のブック、ライブラリ、またはサイト コレクションについては有効または無効にできません。  
  
 **データ更新中に自動アップグレードを構成する方法**  
  
 自動アップグレードを使用するには、PowerPivot 構成ツールで **[PowerPivot ブックを自動的にアップグレードして、サーバーからのデータ更新を有効にする]** チェック ボックスをオンにする必要があります。 ツールでこのチェック ボックスがあるのは、 **[PowerPivot System サービスのアップグレード]** ページおよび新しいインストールを構成している場合の **[PowerPivot サービス アプリケーションの作成]** ページです。  
  
 次のコマンドレットを実行して、自動アップグレードが有効かどうかを確認できます。  
  
```  
PS C:\Windows\system32> Get-PowerPivotSystemService  
```  
  
 Get-PowerPivotSystemService からの出力は、プロパティとそれに対応する値のリストです。 プロパティ リストの `WorkbookUpgradeOnDataRefresh` を確認してください。 自動アップグレードが有効になっている場合、値は **true** に設定されます。 
  **false**の場合は、次の手順を続行し、ブックの自動アップグレードを有効にします。  
  
 ブックの自動アップグレードを有効にするには、次のコマンドを実行します。  
  
```  
PS C:\Windows\system32> Set-PowerPivotSystemService -WorkbookUpgradeOnDataRefresh:$true -Confirm:$false  
```  
  
 アップグレードした後のブックは、定期データ更新および PowerPivot for Excel アドインの新機能を使用できます。  
  
##  <a name="bkmk_runold"></a>新しいサーバーでの複数のブックバージョンの実行  
 
  [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] の [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)]インスタンスでは、古いバージョンと新しいバージョンの PowerPivot ブックを同時に実行できます。  
  
 サーバーをインストールした方法によっては、1 つのサーバー上で古いブックと新しいブックにアクセスする前に、以前のバージョンの Analysis Services OLE DB プロバイダーのインストールが必要になる場合があります。 ****  
  
 以前の [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] SQL Server インスタンスでの新しいバージョンのブックの発行はできません。 
  [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] のインスタンスでは、 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] の [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)]バージョンで作成したブックは読み込まれません。SQL Server 2012 のインスタンスでは、Excel で PowerPivot の [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] バージョンを使用して作成した高度なデータ モデルが含まれる Office 2013 ブックは読み込まれません。  
  
###  <a name="bkmk_msolapxslx"></a>PowerPivot ブックで MSOLAP Data Provider 情報を確認する方法  
 PowerPivot ブックで使用される OLE DB プロバイダーを確認するには、次の手順に従います。 データの接続情報を確認するために [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)] アドインをインストールする必要はありません。  
  
1.  Excel で、[データ] タブの **[接続]** をクリックします。 
  **[プロパティ]** をクリックします。  
  
2.  
  **[定義]** タブの接続文字列の先頭にプロバイダーのバージョンが表示されます。  
  
     **Provider = MSOLAP. 5**は、ブックが[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]であることを示します。  
  
     **Provider = MSOLAP. 4**は[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]を示します。  
  
     **Data Source = $Embedded $** は、ブックが埋め込みデータベースを使用する PowerPivot ブックであることを示します。  
  
###  <a name="bkmk_msolappc"></a>ローカルコンピューター上の MSOLAP Data Provider の現在のバージョンを確認する方法  
 PowerPivot ブックを実行するサーバーまたはワークステーションで最新バージョンの OLE DB プロバイダーを確認するには、次の手順に従います。 最新バージョンを確認しておくと、アップグレード後のデータ接続エラーのトラブルシューティングに役立ちます。  
  
1.  レジストリ エディターで、HKEY_CLASSES_ROOT に移動します。  
  
2.  MSOLAP まで下方向へスクロールします。 システムにインストールされている OLAP プロバイダーの中に MSOLAP.5 が含まれていることを確認します。 MSOLAP | CurVer が MSOLAP.5 に設定されていることを確認してください。  
  
## <a name="see-also"></a>参照  
 [PowerPivot から SharePoint への移行2013](migrate-power-pivot-to-sharepoint-2013.md)   
 [PowerPivot for SharePoint のアップグレード](../../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md)   
 [Analysis Services とビジネスインテリジェンスの新機能](../../what-s-new-in-analysis-services.md)   
 [データ更新履歴の表示 &#40;PowerPivot for SharePoint&#41;](../../power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
  
