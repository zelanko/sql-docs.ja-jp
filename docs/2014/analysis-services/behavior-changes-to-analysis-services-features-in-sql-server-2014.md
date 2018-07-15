---
title: 動作の変更の分析サービスの SQL Server 2014 の機能 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 92ebd5cb-afb6-4b62-968f-39f5574a452b
caps.latest.revision: 17
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 87ec5b84d5d74bae3be3c05dfcafd3a609780f82
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37289878"
---
# <a name="behavior-changes-to-analysis-services-features-in-sql-server-2014"></a>SQL Server 2014 における Analysis Services 機能の動作の変更
  このトピックでは、動作の変更を説明します[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]多次元、テーブル、データ マイニングと[!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)]展開します。 動作の変更の影響は、現在のバージョンの SQL Server の機能や操作方法が、以前のバージョンの SQL Server とは異なることに表れます。  
  
> [!NOTE]  
>  これに対し、重大な変更は、いずれかのデータ モデルを防止またはアプリケーションと統合されて[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]を実行します。 詳細についてを参照してください。 [SQL Server 2014 Analysis Services 機能の重大な変更](breaking-changes-to-analysis-services-features-in-sql-server-2014.md)します。  
  
 このトピックの内容  
  
-   [SQL Server 2014 の動作の変更](#bkmk_sql2014)  
  
-   [SQL Server 2012 SP1 の動作の変更](#bkmk_sql2012sp1)  
  
-   [SQL Server 2012 の動作の変更](#bkmk_sql2012)  
  
##  <a name="bkmk_sql2014"></a> 動作の変更 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 テーブル、多次元、データ マイニングで発表された新しい動作の変更がないまたは[!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)]このリリースで機能します。  ただし、ため[!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)]はこれと似ています、[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]と[!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]両方の以前のリリースからの動作の変更が提供されているバージョンからアップグレードする場合の便利なように、ここ[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]します。  
  
##  <a name="bkmk_sql2012sp1"></a> 動作の変更 [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]  
 このセクションの報告の動作変更について説明[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]機能[!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]します。 これらの変更にも適用[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]します。  
  
|問題点|説明|  
|-----------|-----------------|  
|SQL Server 2008 R2 PowerPivot ブックを SQL Server 2012 SP1 PowerPivot for SharePoint 2013 で使用しているとき、モデルのアップグレードおよび更新が自動的に行われません。 そのため、SQL Server 2008 R2 PowerPivot ブックの定期データ更新が機能しません。|2008 R2 ブックはで開きます[!INCLUDE[ssGeminiShortvnext](../includes/ssgeminishortvnext-md.md)]、スケジュールされた更新は機能しません。 更新履歴を確認すると、次のようなエラー メッセージが表示されます。<br /> 「ブックに、サポートされていない PowerPivot モデルが含まれています。 ブックの PowerPivot モデルは、SQL Server 2008 R2 PowerPivot for Excel 2010 形式です。 サポートされている PowerPivot モデルは、 <br />SQL Server 2012 PowerPivot for Excel 2010 <br />SQL Server 2012 PowerPivot for Excel 2013 です。」<br /><br /> **ブックをアップグレードする方法:** ブックを 2012 ブックにアップグレードするまで定期更新は機能しません。 ブックとブックに含まれるモデルをアップグレードするには、次のいずれかの手順を実行します。<br /><br /> SQL Server 2012 PowerPivot for Excel アドインがインストールされた Microsoft Excel 2010 でブックをダウンロードして開きます。 ブックを保存して、SharePoint サーバーに再発行します。<br /><br /> Microsoft Excel 2013 でブックをダウンロードして開きます。 ブックを保存して、SharePoint サーバーに再発行します。<br /><br /> <br /><br /> ブックのアップグレードの詳細については、次を参照してください。[ブックのアップグレードと定期データ更新&#40;SharePoint 2013&#41;](instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)します。|  
|DAX での動作の変更[すべて関数](https://msdn.microsoft.com/library/ee634802(v=sql.120).aspx)します。|前のバージョン[!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]かどうか [Date] 列でマーク テーブルとして指定した日付、タイム インテリジェンスで使用するためと、すべての関数に、[Date] 列が引数として渡されること、さらに、CALCULATE 関数に、フィルター、テーブル内のすべての列のすべてのフィルターとして渡されます日付列でのスライサーに関係なくは無視されます。<br /><br /> 例を次に示します。<br /><br /> `= CALCULATE (<expression>, ALL (DateTable[Date]))`<br /><br /> 前のバージョン[!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]すべてに、[Date] 列に関係なく、引数として渡さ、DateTable のすべての列のすべてのフィルターは無視されます。<br /><br /> [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]され、Excel 2013 で powerpivot での動作を ALL の引数として渡された指定された列に対してのみ、フィルターを無視します。<br /><br /> この新しい動作に対処するには、つまりテーブル全体のフィルターとしてすべての列を無視するには、次のように引数から [Date] を除外します。<br /><br /> `=CALCULATE (<expression>, ALL(DateTable))`<br /><br /> これにより、[!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] より前のバージョンと同じ動作になります。|  
  
##  <a name="bkmk_sql2012"></a> 動作の変更 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
 このセクションの動作変更について説明[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]機能[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]します。 これらの変更にも適用[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]します。  
  
### <a name="analysis-services-multidimensional-mode"></a>Analysis Services、多次元モード  
  
#### <a name="nullprocessing-option-set-to-preserve-is-no-longer-supported-for-distinct-count-measures"></a>個別のカウント メジャーでは、NullProcessing オプションを Preserve に設定することはサポートされません。  
 前のバージョン[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]を設定することでした[NullProcessing 要素&#40;ASSL&#41; ](scripting/properties/nullprocessing-element-assl.md)に`Preserve`個別のカウント メジャー。  しかし、この方法では、多くの場合に正しくない結果が生成され、処理ジョブがクラッシュすることもありました。 その結果、この構成が無効になってで[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]します。 使用しようとすると、次の検証エラーが発生します。"メタデータ マネージャーでエラーが発生しました。 Preserve は有効な NullProcessing 値ではありません、 \<measurename > 個別のカウント メジャーです"。  
  
#### <a name="cube-browser-in-management-studio-and-cube-designer-has-been-removed"></a>Management Studio とキューブ デザイナーのキューブ ブラウザーは削除されました。  
 Management Studio またはキューブ デザイナーでキューブ ブラウザー コントロールを使用すると、PivotTable 構造体にフィールドをドラッグ アンド ドロップできましたが、このコントロールは製品から削除されました。 このコントロールは、Office Web コントロール (OWC) コンポーネントでした。 Office では OWC が非推奨とされ、使用できなくなりました。  
  
### <a name="powerpivot-for-sharepoint"></a>PowerPivot for SharePoint  
  
#### <a name="higher-permission-requirements-for-using-a-powerpivot-workbook-as-an-external-data-source"></a>PowerPivot ブックを外部データ ソースとして使用するには上位の権限が必要  
 Excel ブックでは、同じブックに埋め込まれた PowerPivot データも、外部のブックにある PowerPivot データも表示できます。 以前のリリースでは、PowerPivot データが埋め込まれている場合も、外部にある場合も、権限の要件が同じでした。 PowerPivot ブックに対する **"表示のみ"** の権限があれば、埋め込みおよび外部接続の両方について、ブック内のすべての PowerPivot データに対する完全なアクセス権を取得することができました。  
  
 このリリースでは、外部ファイルの PowerPivot データを表示する Excel ブックについて、権限の要件が変更されています。 このリリースでは、クライアント アプリケーションから外部の PowerPivot ブックに接続するには、 **"読み取り"** 権限 (具体的には、 **"アイテムを開く"** 権限) が必要になりました。 追加された権限により、ブックに埋め込まれたソース データを表示するためのダウンロード権をユーザーが持っていることが示されます。 また、この権限は、モデル データにリンクするクライアント アプリケーションやブックで、モデル データを完全に使用できることも表しています。つまり、権限の要件と実際のデータ接続動作の対応が、従来よりも適切になりました。  
  
 これまでどおり PowerPivot ブックを外部データ ソースとして使用するには、外部 PowerPivot データに接続するユーザーの SharePoint 権限を引き上げる必要があります。 権限を変更しない場合、ユーザーがデータ ソース接続で PowerPivot ブックにアクセスしようとすると、"PowerPivot Web サービスからエラー (アクセスが拒否されました。 要求したドキュメントが存在しないか、ファイルを開く権限がありません。) が返されました" というエラーが表示されます。  
  
> [!WARNING]  
>  権限の継承をライブラリ レベルで無効にして、このライブラリ内の特定のドキュメントに対するユーザー権限を **"表示のみ"** から **"読み取り"** に引き上げるには、次の手順に従います。 ただし、事前に既存の権限とドキュメントを慎重に確認し、これらの手順がサイトに対して適切であるかどうかを見極めてください。  
>   
>  または、ライブラリ内にフォルダーを作成し、影響を受けるすべてのドキュメントをそのフォルダーに移して、フォルダーに対して固有の権限を設定してもかまいません。  
  
> [!NOTE]  
>  ブックが PowerPivot ギャラリーに格納されている場合は、ブックに対する権限の継承を無効にすると、データ更新が構成されている場合にそのブックのサムネイル画像が正常に生成されなくなります。 ギャラリー内のブックとプレビュー イメージへのアクセスを同時に許可するには、ライブラリ内のすべてのドキュメントに対する **"読み取り"** 権限を特定のユーザーにライブラリ レベルで付与することを検討してください。  
  
 権限を変更するには、サイト所有者である必要があります。  
  
 **個々 のブックのアクセス許可レベルの読み取りアクセス許可を強化する方法**  
  
1.  下矢印をクリックして個々のドキュメントのメニューを開きます。  
  
2.  **[権限の管理]** をクリックします。  
  
3.  既定では、ライブラリは権限を継承します。 このライブラリ内の個々のブックの権限を変更するには、 **[権限の継承を中止]** をクリックします。  
  
4.  PowerPivot ブックに対する追加の権限が必要なユーザーまたはグループ名のチェック ボックスをオンにします。 権限を追加することで、これらのユーザーは埋め込み PowerPivot データにリンクし、他のドキュメント内でそのデータを外部データ ソースとして使用できるようになります。  
  
5.  **[ユーザー権限の編集]** をクリックします。  
  
6.  **[読み取り]** 権限を選択し、 **[OK]** をクリックします。  
  
#### <a name="powerpivot-gallery-new-rules-for-snapshot-generation-for-some-powerpivot-workbooks"></a>PowerPivot ギャラリー: 一部の PowerPivot ブックのスナップショット生成に適用される新しい規則  
 今回のリリースでは、PowerPivot ギャラリーでスナップショット画像を生成する際の要件が追加されており、情報が公開される可能性が排除されています (つまり、表示権限がないデータ ソースに含まれるデータのスナップショットを表示できなくなりました)。 こうした要件は、外部データ ソースに接続する PowerPivot ブックを表示する際にのみ適用されます。 埋め込まれた PowerPivot データだけを視覚化するブックを使用する場合は、PowerPivot ギャラリーでのスナップショットの生成方法に違いはありません。  
  
 開かれるたびにデータが更新されるブックの場合、スナップショットの生成の際に、次のような新しい規則が適用されます。  
  
-   他のブックまたはレポートにより外部データ ソースとして使用される PowerPivot ブックは、データを使用するブックと同じライブラリ内にあることが必要です。 たとえば、sales-data.xlsx が sales-report.xlsx にデータを提供する場合、両方のブックが同じギャラリー内にないと、スナップショット画像が表示されません。  
  
-   一緒に使用されるブックは、共通の親 (つまり PowerPivot ギャラリー) から権限を継承する必要があります。 先ほどの例では、sales-data.xlsx と sales-report.xlsx の両方が PowerPivot ギャラリーから権限を継承する必要があります。  
  
 ブックでいずれかの条件が満たされていない場合、予期したサムネイル画像の代わりに次のロック アイコンが表示されます。  
  
 ![GMNI_PowerPivotGalleryIcon_Locked](media/gmni-powerpivotgalleryicon-locked.gif "GMNI_PowerPivotGalleryIcon_Locked")  
  
#### <a name="new-default-setting-for-load-balancing-requests-changed-from-round-robin-to-health-based"></a>ラウンド ロビン方式からヘルス ベース方式に変更された、要求の負荷分散の既定の設定  
 PowerPivot サービス アプリケーションには、PowerPivot データに対する要求をファーム内の複数の PowerPivot for SharePoint サーバー間でどのように分散するかを決める既定の設定があります。 以前のリリースでの既定の設定は **ラウンド ロビン**方式で、要求は使用可能なサーバー間で順番に分散されていました。 今回のリリースでは、既定の設定は **ヘルス ベース**方式になりました。 PowerPivot サービス アプリケーションは、使用可能なメモリや CPU などのサーバーの状態の統計を基に、次の要求を受け取るサーバー インスタンスを決定します。  
  
 サーバーを以前のリリースからアップグレードした場合、PowerPivot サービス アプリケーションには前の既定の設定 (**ラウンド ロビン**) が保持されています。 **ヘルス ベース** の割り当て方式の設定を使用するには、構成設定を変更する必要があります。 詳細については、次を参照してください。[を作成し、サーバーの全体管理で PowerPivot サービス アプリケーションを構成する](power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md)します。  
  
## <a name="see-also"></a>参照  
 [旧バージョンとの互換性](../../2014/getting-started/backward-compatibility.md)   
 [重大な変更を Analysis Services の SQL Server 2014 の機能](breaking-changes-to-analysis-services-features-in-sql-server-2014.md)  
  
  
