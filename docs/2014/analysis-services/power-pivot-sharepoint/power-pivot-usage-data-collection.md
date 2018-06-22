---
title: PowerPivot 使用状況データ収集 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9057cb89-fb17-466e-a1ce-192c8ca20692
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 2d16c55953bc3988a7de6c9d06929904d6dc0b67
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074739"
---
# <a name="powerpivot-usage-data-collection"></a>PowerPivot 使用状況データ収集
  使用状況データ収集は、ファーム レベルの SharePoint 機能です。 PowerPivot for SharePoint では、このシステムを使用および拡張して、PowerPivot のデータやサービスがどのように使用されているかを示すレポートが PowerPivot 管理ダッシュボードに用意されています。 SharePoint のインストール方法によっては、使用状況データ収集がファームに対して無効になっていることがあります。 ファーム管理者は、使用状況のログ記録を有効にして、PowerPivot 管理ダッシュボードに表示される使用状況データを作成する必要があります。 イベントを有効にして、PowerPivot の使用状況データ収集を構成する方法の詳細については「[の使用状況データ収集を構成する&#40;PowerPivot for SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)です。  
  
 PowerPivot 管理ダッシュ ボードの使用状況データについては、次を参照してください。 [PowerPivot Management Dashboard and Usage Data](power-pivot-management-dashboard-and-usage-data.md)です。  
  
 **このトピックの内容:**  
  
 [使用状況データ収集とレポート アーキテクチャ](#usagearch)  
  
 [使用状況データのソース](#sources)  
  
 [サービスおよびタイマー ジョブ](#servicesjobs)  
  
 [使用状況データをレポートします。](#reporting)  
  
##  <a name="usagearch"></a> 使用状況データ収集とレポート アーキテクチャ  
 PowerPivot の使用状況データは、SharePoint インフラストラクチャおよび PowerPivot サーバー コンポーネントの機能の組み合わせを使用して収集、格納、および管理されます。 SharePoint インフラストラクチャには、集中管理された使用状況サービスと組み込みのタイマー ジョブが用意されています。 PowerPivot for SharePoint により、SharePoint サーバーの全体管理で表示される PowerPivot 使用状況データとレポートのための長期的な保存機能も追加されます。  
  
 使用状況データ収集システムでは、イベント情報が、アプリケーション サーバーまたは Web フロント エンド上の使用状況コレクション システムに入力されます。 使用状況データは、タイマー ジョブに応じてシステム内を移動します。タイマー ジョブにより、データは物理サーバー上の一時データ ファイルからデータベース サーバー上の永続的なストレージに移動します。 次の図に、使用状況データをデータ コレクションおよびレポート システム内で移動させるコンポーネントとプロセスを示します。  
  
 **注:** 使用状況データ収集が有効になっていることを確認してください。 確認するには、SharePoint サーバーの全体管理の **[監視]** に移動します。 詳細については、次を参照してください。[の使用状況データ収集を構成する&#40;PowerPivot for SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)です。  
  
 ![コンポーネントと使用状況データ収集のプロセス。](../media/gmni-usagedata.gif "コンポーネントと使用状況データ収集のプロセスです。")  
  
|フェーズ|説明|  
|-----------|-----------------|  
|1|使用状況データ収集は、SharePoint 配置の PowerPivot コンポーネントと [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ プロバイダーで生成されるイベントによってトリガーされます。 有効または無効にできる構成可能なイベントには、接続要求、読み込み要求とアンロード要求、およびアプリケーション サーバー上の PowerPivot サービスによって監視されるクエリ応答タイミング イベントがあります。 その他のイベントは、サーバーのみによって管理され、無効にすることはできません。 このようなイベントには、データ更新イベントとサーバー状態イベントがあります。<br /><br /> 最初に、使用状況データは SharePoint システムのデータ収集機能を使用して収集され、ローカル ログ ファイルに格納されます。 ファイルとファイルの場所は、SharePoint の標準の使用状況データ収集システムの一部になります。 ファイルの場所は、ファーム内のすべてのサーバーで同じです。 ログ ディレクトリの場所を表示または変更するには、SharePoint サーバーの全体管理の **[監視]** に移動し、 **[Usage and Health data collection の構成]** をクリックします。|  
|2|スケジュール設定された間隔 (既定では毎時) で、Microsoft SharePoint Foundation 利用状況データのインポート タイマー ジョブは、ローカル ファイルから PowerPivot サービス アプリケーション データベースに使用状況データを移動します。 ファーム内に複数の PowerPivot サービス アプリケーションが存在する場合、それぞれが独自のデータベースを持ちます。 イベントには、イベントを生成した PowerPivot サービス アプリケーションを識別する内部情報が含まれます。 このアプリケーション識別子により、使用状況データがその作成元のアプリケーションにバインドされるようになります。|  
|3|データは、サーバーの全体管理の PowerPivot 管理ダッシュボードで使用できる内部レポート データベースにコピーされます。|  
|4|データ ソースは、Excel でカスタム レポートを作成するためにアクセスできる PowerPivot ブックです。 ソースとなるブックのインスタンスは 1 つだけです。 ローカライズされたレポートはすべて、同じソースのブックに基づいています。|  
|5|使用状況データは、サーバーのパフォーマンスと可用性を管理する管理者に対して、PowerPivot サービス アプリケーションのレポートで表示されます。 SharePoint でサポートされている言語向けに、ブックのローカライズされたインスタンスが作成されます。<br /><br /> 詳細については、このトピックの「 [使用状況データのレポート](#reporting) 」を参照してください。|  
  
##  <a name="sources"></a> 使用状況データのソース  
 使用状況データ収集が有効の場合、次のサーバー イベントに対してデータが生成されます。  
  
|イベント|説明|構成可能|  
|-----------|-----------------|------------------|  
|接続|Excel ブックの PowerPivot データに対してクエリを実行しているユーザーに代わって実行されるサーバー接続。 接続イベントは、PowerPivot ブックへの接続を開いたユーザーを特定します。 レポートでは、この情報を使用して、最も頻繁に使用するユーザー、同じユーザーによってアクセスされる PowerPivot データ ソース、および長期的な接続の傾向が提示されます。|有効または無効にする[の使用状況データ収集を構成する&#40;PowerPivot for SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)です。|  
|クエリ応答時間|完了に要する時間に基づいてクエリを分類するクエリ応答統計。 クエリ応答統計は、サーバーがクエリ要求への応答に要する時間のパターンを示します。|有効または無効にする[の使用状況データ収集を構成する&#40;PowerPivot for SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)です。|  
|データ読み込み|[!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]によるデータ読み込み操作。 データ読み込みイベントは、最も頻繁に使用されるデータ ソースを特定します。|有効または無効にする[の使用状況データ収集を構成する&#40;PowerPivot for SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)です。|  
|データ アンロード|PowerPivot サービス アプリケーションによるデータ アンロード操作。 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] は、PowerPivot データ ソースが使用されていない場合、またはサーバーのメモリが不足しているかデータ更新ジョブを実行するために追加のメモリが必要な場合に、非アクティブな PowerPivot データ ソースをアンロードします。|有効または無効にする[の使用状況データ収集を構成する&#40;PowerPivot for SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)です。|  
|サーバー状態|CPU およびメモリの使用率で測定されたサーバー状態を示すサーバー操作。 このデータは、履歴的なデータです。 サーバーの現在の処理負荷に関するリアルタイム情報は提供されません。|No. このイベントに対して使用状況データは常に収集されます。|  
|データ更新|スケジュール設定されたデータ更新に応じて PowerPivot サービスにより開始されるデータ更新操作。 データ更新の使用状況履歴は、運用レポート用にアプリケーション レベルで収集され、個々のブックの [データ更新の管理] ページに反映されます。<br /><br /> **注:** [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] および SharePoint 2013 の配置では、Analysis Services サーバーではなく Excel Services によってデータ更新が管理されます。|No. PowerPivot サービス アプリケーション用のデータ更新を有効にした場合、データ更新の使用状況データは常に収集されます。|  
  
##  <a name="servicesjobs"></a> サービスおよびタイマー ジョブ  
 次の表に、使用状況データ収集システムのサービスとデータ コレクション ストアを示します。 PowerPivot 管理ダッシュ ボードのレポート内のサーバー状態と使用状況データのデータ更新を強制するため、タイマー ジョブ スケジュールをオーバーライドする方法については、次を参照してください。 [SharePoint 2010 で PowerPivot データ更新](../powerpivot-data-refresh-with-sharepoint-2010.md)です。 タイマー ジョブは、SharePoint サーバーの全体管理で確認できます。 **[監視]** に移動し、 **[ジョブ状態の確認]** をクリックして、 **[ジョブ定義の確認]** をクリックします。  
  
|コンポーネント|既定のスケジュール|説明|  
|---------------|----------------------|-----------------|  
|SharePoint Timer Service (SPTimerV4)||この Windows サービスは、ファーム内のすべてのメンバー コンピューターでローカルに実行され、ファーム レベルで定義されるすべてのタイマー ジョブを処理します。|  
|Microsoft SharePoint Foundation 利用状況データのインポート (Microsoft SharePoint Foundation Usage Data Import)|30 分ごと (SharePoint 2010 の場合)。 5 分ごと (SharePoint 2013 の場合)。|このタイマー ジョブは、ファーム レベルでグローバルに構成されます。 このタイマー ジョブは、使用状況データをローカルの使用状況ログ ファイルから中央の使用状況データ収集データベースに移動します。 このタイマー ジョブを手動で実行して、データ インポート操作を強制的に実行できます。|  
|Microsoft SharePoint Foundation 使用状況データ処理タイマー ジョブ|毎日午前 3 時|**(\*)** SQL Server 2012 PowerPivot for SharePoint 以降、このタイマー ジョブがサポートされるアップグレード シナリオまたは移行シナリオ、SharePoint 利用状況データベースにまだ古い使用状況データを必要があります。 SQL Server 2012 PowerPivot for SharePoint 以降、PowerPivot の使用状況データ収集および管理ダッシュボード ワークフローには、SharePoint 利用状況データベースが使用されません。 このタイマー ジョブを手動で実行して、SharePoint 利用状況データベースに残っている PowerPivot の関連データを PowerPivot サービス アプリケーション データベースに移動することができます。<br /><br /> このタイマー ジョブは、ファーム レベルでグローバルに構成されます。 このタイマージョブは、中央の使用状況データ収集データベース内にある期限切れになった使用状況データ (つまり、30 日を超えているすべてのレコード) を調べます。 ファーム内の PowerPivot サーバーに対して、このタイマー ジョブは PowerPivot 使用状況データの追加確認を実行します。 PowerPivot 使用状況データを検出した場合、このタイマー ジョブは、アプリケーション識別子を使用して適切なサービス アプリケーション データベースを検索し、データをそのデータベースに移動します。<br /><br /> このタイマー ジョブを手動で実行して、期限切れになったデータを強制的に確認したり、PowerPivot サービス アプリケーション データベースへ PowerPivot 使用状況データを強制的にインポートしたりできます。|  
|PowerPivot 管理ダッシュボード処理タイマー ジョブ|毎日午前 3 時|このタイマー ジョブは、管理データを PowerPivot 管理ダッシュボードに提供する内部 PowerPivot ブックを更新します。 これは、ダッシュボード レポートまたは Web パーツに表示されるサーバー名、ユーザー名、アプリケーション名、およびファイル名など、SharePoint により管理される更新情報を取得します。|  
  
##  <a name="reporting"></a> 使用状況データのレポート  
 PowerPivot データの使用状況データを表示するには、PowerPivot 管理ダッシュボードで組み込みレポートを表示します。 組み込みレポートは、サービス アプリケーション データベースのレポート データ構造から取得された使用状況データを統合します。 基になるレポート データが毎日更新されるため、組み込みの使用状況レポートで更新済みの情報が表示されるのは、Microsoft SharePoint Foundation の使用状況データ処理タイマー ジョブによりデータが PowerPivot サービス アプリケーション データベースにコピーされた後に限られます。 既定では、この処理は 1 日 1 回行われます。  
  
 レポートを表示する方法の詳細についてを参照してください[PowerPivot Management Dashboard and Usage Data](power-pivot-management-dashboard-and-usage-data.md)です。  
  
## <a name="see-also"></a>参照  
 [PowerPivot 管理ダッシュ ボードと使用状況データ](power-pivot-management-dashboard-and-usage-data.md)   
 [構成設定のリファレンス&#40;PowerPivot for SharePoint&#41;](configuration-setting-reference-power-pivot-for-sharepoint.md)   
 [使用状況データ収集の構成&#40;PowerPivot for SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)  
  
  