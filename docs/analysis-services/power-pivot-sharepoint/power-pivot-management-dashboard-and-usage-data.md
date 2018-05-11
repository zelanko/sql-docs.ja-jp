---
title: Power Pivot 管理ダッシュ ボードと使用状況データ |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 394aa487fec0d67e5effc90faea5ed8bf7c415b8
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="power-pivot-management-dashboard-and-usage-data"></a>Power Pivot 管理ダッシュボードと使用状況データ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] 管理ダッシュボードとは、SQL Server [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] for SharePoint の配置の管理に役立つ SharePoint サーバーの全体管理の定義済みのレポートおよび Web パーツのコレクションです。 管理ダッシュボードでは、サーバーの状態、ブックの利用状況、およびデータ更新に関連する情報が示されます。 ダッシュボードは、SharePoint 使用状況データ コレクションのデータを使用します。  
  
  
##  <a name="prereq"></a> 前提条件  
 管理する [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] サービス アプリケーションの [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] 管理ダッシュボードを開くには、サービス管理者である必要があります。  
  
##  <a name="items"></a> ダッシュボードのセクションの概要  
 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] 管理ダッシュボードには、特定の情報カテゴリにドリル ダウンする Web パーツおよび埋め込みレポートが用意されています。 ダッシュボードの各部分の説明を次に示します。  
  
|ダッシュボード|Description|  
|---------------|-----------------|  
|インフラストラクチャ - サーバーの状態|CPU 使用率、メモリ消費量、およびクエリ応答時間の時間の経過に伴う変化の傾向を表示し、システム リソースが最大容量に近づいていないかどうか、または使用率が低くなっていないかどうかを評価できるようにします。|  
|アクション|現在のサービス アプリケーション、サービス アプリケーションの一覧、および使用状況ログを含む、サーバーの全体管理内の他のページへのリンクを示します。|  
|ブックの利用状況 - グラフ|データ アクセスの頻度をレポートします。 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] データ ソースへの接続が発生する頻度を日単位または週単位で確認できます。|  
|ブックの利用状況 - リスト|データ アクセスの頻度をレポートします。 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] データ ソースへの接続が発生する頻度を日単位または週単位で確認できます。|  
|データ更新 - 最近の利用状況|データ更新ジョブの状態をレポートします (実行に失敗したジョブを含む)。 このレポートは、データ更新操作をアプリケーション レベルで総合的に理解するのに役立ちます。 管理者は、 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] サービス アプリケーション全体に対して定義されているデータ更新ジョブの数が一目でわかります。|  
|データ更新 - 最近のエラー|データ更新が正常に完了しなかった [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] ブックを一覧表示します。|  
|レポート|Excel で開くことができるレポートへのリンクを示します。|  
  
##  <a name="open"></a> Power Pivot 管理ダッシュボードを開く  
 ダッシュボードには、一度に 1 つの [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] サービス アプリケーションの情報が表示されます。 管理ダッシュボードは、異なる 2 つの場所から開くことができます。  
  
### <a name="open-the-dashboard-from-general-application-settings"></a>[アプリケーションの全般設定] からダッシュボードを開く  
  
1.  サーバーの全体管理の **[アプリケーションの全般設定]** グループで **[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] 管理ダッシュボード**をクリックします。  
  
2.  メイン ページで、業務データを表示する Power Pivot サービス アプリケーションを選択します。  
  
### <a name="open-the-dashboard-from-a-power-pivot-service-application"></a>Power Pivot サービス アプリケーションからダッシュボードを開く  
  
1.  サーバーの全体管理で、 **[アプリケーション構成の管理]** の **[サービス アプリケーションの管理]** をクリックします。  
  
2.  [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] サービス アプリケーションの名前をクリックします。 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] 管理ダッシュボードに、現在のサービス アプリケーションの業務データが表示されます。  
  
### <a name="change-the-current-service-application"></a>現在のサービス アプリケーションを変更する  
 管理ダッシュボードで現在の [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] サービス アプリケーションを変更するには、次の手順を実行します。  
  
1.  [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] 管理ダッシュボードの上部で、現在のサービス アプリケーションの名前 ("**既定の [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] サービス アプリケーション**" など) を確認します。  
  
2.  **[アクション]** ダッシュボードで、 **[サービス アプリケーションの一覧を表示する]** をクリックします。  
  
3.  管理ダッシュボードのレポートを表示する [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] サービス アプリケーションの名前をクリックします。  
  
##  <a name="sourcedata"></a> ダッシュボードのソース データ  
 ダッシュボード、レポート、および Web パーツでは、システムおよび [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] アプリケーション データベースからデータを取り出す内部データ モデルのデータが表示されます。 内部データ モデルは、サーバーの全体管理サイトでホストされている [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] ブックに埋め込まれています。 データ モデルの構造は固定されています。 PowertPivot ブックをデータ ソースとして使用して新しいレポートを作成できますが、構造は変更しないでください。変更すると、その構造を使用する定義済みのレポートが壊れます。  
  
 データの収集方法の詳細については、以下を参照してください。  
  
-   [Power Pivot 使用状況データ収集](../../analysis-services/power-pivot-sharepoint/power-pivot-usage-data-collection.md)  
  
-   [使用状況データ収集の構成 (Power Pivot for SharePoint)](../../analysis-services/power-pivot-sharepoint/configure-usage-data-collection-for-power-pivot-for-sharepoint.md)  
  
 Power Pivot サーバー システムに関するデータをキャプチャするために、イベント メッセージング、データ更新の履歴、およびその他の使用状況履歴が各 Power Pivot サービス アプリケーションに対して有効になっていることを確認してください。 通常のサーバー操作中に収集されるサーバーおよび使用状況のデータは、最終的に、内部データ モデルに格納されるソース データになります。 **注:** イベントまたは使用状況履歴を無効にすると、複合レポートは不完全またはエラーになります。  
  
##  <a name="edit"></a> Power Pivot 管理ダッシュボードの編集  
 ダッシュボードの開発またはカスタマイズに関する専門知識がある場合は、ダッシュボードを編集して新しい Web パーツを含めることができます。 また、ダッシュボードに含まれる Web パーツのプロパティも編集できます。  
  
##  <a name="reports"></a> Power Pivot 管理ダッシュボード用カスタム レポートの作成  
 レポートを作成するため、 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] の使用状況データと履歴は、ダッシュボードと共に作成および構成される内部の [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] ブックに保持されます。 必要な情報が既定のレポートに含まれていない場合は、ブックに基づいて Excel でカスタム レポートを作成できます。 後で [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] ソリューション ファイルをアップグレードまたはアンインストールした場合、ブックと作成したカスタム レポートは両方とも保持されます。 ブックとレポートは、サーバーの全体管理サイト内の [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] 管理ライブラリに格納されます。 このライブラリは既定では表示されませんが、[サイトの操作] にある [すべてのサイト コンテンツの表示] 操作を使用すると表示できます。  
  
 カスタム レポートでの作業を簡単に開始できるように、 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] 管理ダッシュボードには、ソースのブックに接続するための Office データ接続 (.odc) ファイルが用意されています。 たとえば、.odc ファイルを Excel で使用して、追加のレポートを作成できます。  
  
> [!NOTE]  
>  Excel で .odc ファイルを使用しようとしたときに "データ ソースの初期化に失敗しました" というエラーが表示されないように、ファイルを編集してください。 自動生成される .odc ファイルには、MSOLAP OLE DB プロバイダーでサポートされていないパラメーターが 1 つ含まれています。 次の手順では、これらのパラメーターを削除する回避策について説明します。  
  
 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] ブックに基づいて全体管理でレポートを作成するには、ファーム管理者またはサービス管理者である必要があります。  
  
1.  [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] 管理ダッシュボードを開きます。  
  
2.  ページの下部にある **[レポート]** セクションまでスクロールします。  
  
3.  **[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] 管理データ**をクリックします。  
  
4.  .odc ファイルをローカル フォルダーに保存します。  
  
5.  テキスト エディターで .odc ファイルを開きます。  
  
6.  **\<Odc:ConnectionString >** 要素、削除の行の最後までスクロール**データが埋め込まれた = False**、し、削除**編集モードの 0 を =** です。 文字列の最後の文字がセミコロンである場合は、ここで削除します。  
  
7.  このファイルを保存します。 残りの手順は、使用している [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] と Excel のバージョンによって異なります。  
  
8.  1.  Excel 2013 を起動します。  
  
    2.  **[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]** リボンで、 **[管理]** をクリックします。  
  
    3.  **[外部データの取り込み]** をクリックし、 **[既存の接続]** をクリックします。  
  
    4.  .ODC ファイルが表示されている場合はそのファイルをクリックします。 .ODC ファイルが表示されない場合は、 **[参照]** をクリックし、ファイル パスで .odc ファイルを指定します。  
  
    5.  **[開く]** をクリックします。  
  
    6.  **[接続のテスト]** をクリックして、接続に成功したことを確認します。  
  
    7.  接続の名前を指定して、 **[次へ]** をクリックします。  
  
    8.  [MDX クエリの指定] で、 **[デザイン]** をクリックして MDX クエリ デザイナーを開き、操作するデータを収集します。 **Edit Mode プロパティ名の形式が正しくありません。** というエラー メッセージが表示される場合は、.ODC ファイルを編集していることを確認してください。  
  
    9. **[OK]** をクリックし、 **[完了]** をクリックします。  
  
    10. ピボットテーブル レポートまたはピボットグラフ レポートを作成して、データを Excel で表示します。  
  
9. 1.  Excel 2010 を起動します。  
  
    2.  [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] リボンで、**[[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] ウィンドウの起動]** をクリックします。  
  
    3.  [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] ウィンドウのデザイン リボンで、 **[既存の接続]** をクリックします。  
  
    4.  **[参照]** をクリックします。  
  
    5.  ファイル パスで、.odc ファイルを指定します。  
  
    6.  **[開く]** をクリックします。 使用状況データを含む [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] ブックへの接続文字列を使用して、テーブルのインポート ウィザードが開始されます。  
  
    7.  **[接続テスト]** をクリックして、アクセス権があることを確認します。  
  
    8.  接続の表示名を入力し、 **[次へ]** をクリックします。  
  
    9. [MDX クエリの指定] で、 **[デザイン]** をクリックして MDX クエリ デザイナーを開き、操作するデータを収集してから、ピボットテーブル レポートまたはピボットグラフ レポートを作成して、データを Excel で表示します。  
  
## <a name="see-also"></a>参照  
 [SharePoint 2010 での PowerPivot データの更新](http://msdn.microsoft.com/en-us/01b54e6f-66e5-485c-acaa-3f9aa53119c9)   
 [使用状況データ収集の構成 (Power Pivot for SharePoint)](../../analysis-services/power-pivot-sharepoint/configure-usage-data-collection-for-power-pivot-for-sharepoint.md)  
  
  
