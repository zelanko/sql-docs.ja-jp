---
title: キャッシュの事前読み込み (レポート マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-server
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cache [Reporting Services]
- preloading cache
ms.assetid: 152a1051-8aa5-4c01-bc85-f8be8971b0cd
caps.latest.revision: 35
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: e1bd75c7973c603cdcd9093f07190b1f3fa70c8b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="preload-the-cache-report-manager"></a>キャッシュの事前読み込み (レポート マネージャー)
  共有データセットのキャッシュ更新計画を作成することによって、共有データセットのキャッシュを事前に読み込むことができます。  
  
 レポートのキャッシュを事前に読み込むには 2 つの方法があります。  
  
1.  レポートのキャッシュ更新計画を作成します。 これは推奨される方法です。  
  
2.  データ ドリブン サブスクリプションを使用して、パラメーター化されたレポートのインスタンスをキャッシュに事前に読み込みます。 これは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] より前のバージョンの [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]でキャッシュを事前に読み込む唯一の方法でした。 詳細については、「 [レポートのキャッシュ (SSRS)](../../reporting-services/report-server/caching-reports-ssrs.md)でキャッシュを事前に読み込む唯一の方法でした。  
  
 レポートまたは共有データセットをキャッシュするには、次の条件を満たしている必要があります。  
  
-   共有データセットまたはレポートでキャッシュが有効になっている。  
  
-   共有データセットまたはレポートの共有データ ソースで、保存済みの資格情報を使用するか、または資格情報を使用しないように構成されている。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスが実行されている。  
  
### <a name="to-preload-the-cache-by-creating-a-cache-refresh-plan"></a>キャッシュ更新計画を作成してキャッシュを事前に読み込むには  
  
1.  [レポート マネージャー &#40;SSRS ネイティブ モード&#41;](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896) を開始します。  
  
2.  レポート マネージャーで、 **[コンテンツ]** ページに移動して、キャッシュするアイテムに移動します。  
  
3.  アイテムの上にマウス ポインターを移動し、ドロップダウン リストをクリックして、 **[管理]** をクリックします。  
  
4.  **[キャッシュ更新オプション]** タブをクリックします。  
  
5.  ツール バーの **[新しいキャッシュ更新計画]** をクリックします。  
  
    > [!NOTE]  
    >  アイテムでキャッシュが有効化されていない場合は、キャッシュを有効化するように求めるメッセージが表示されます。 キャッシュを有効化するには、 **[OK]** をクリックします。  
  
     [キャッシュ更新計画] ページが開きます。  
  
6.  必要に応じて、更新計画の説明を入力します。  
  
7.  共有スケジュールを使用する場合は、 **[共有スケジュール]** をクリックして、使用するスケジュールの名前を選択します。  
  
     カスタム スケジュールを使用する場合は、 **[アイテム固有のスケジュール]**、 **[構成]** の順にクリックします。  
  
8.  スケジュールを構成します。  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-preload-the-cache-with-a-user-specific-report-by-using-a-data-driven-subscription"></a>ユーザー固有のレポートでデータ ドリブン サブスクリプションを使用してキャッシュを事前に読み込むには  
  
1.  [レポート マネージャー &#40;SSRS ネイティブ モード&#41;](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896) を開始します。  
  
2.  レポート マネージャーで **[コンテンツ]** ページに移動し、サブスクリプションを作成するレポートに移動します。  
  
3.  レポートをクリックし、 **[サブスクリプション]** タブをクリックして、 **[新しいデータ ドリブン サブスクリプション]** をクリックします。  
  
4.  必要に応じて、サブスクリプションの説明を入力します。  
  
5.  **[受信者への通知方法を指定します。]** の一覧から、 **[NULL 配信プロバイダー]** を選択します。  
  
6.  データ ソースの種類を指定し、 **[次へ]** をクリックしてデータ ソースを構成します。  
  
7.  サブスクライバー データが格納されているデータ ソースへのアクセスに使用する接続の種類、接続文字列、および資格情報を指定します。 次に、Subscribers という [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースへの接続に使用する接続文字列の例を示します。  
  
    ```  
    data source=<servername>; initial catalog=Subscribers  
    ```  
  
8.  **[次へ]** をクリックします。  
  
9. サブスクライバー データを取得するクエリまたはコマンドを指定します。 必要に応じて、処理に時間のかかるクエリのタイムアウト値を増やします。 例 :  
  
    ```  
    Select * from UserInfo  
    ```  
  
10. **[検証]** をクリックします。 クエリを検証してから続行する必要があります。 **"クエリは正常に検証されました。"** というメッセージが表示されたら、 **[次へ]** をクリックします。  
  
11. NULL 配信プロバイダーの配信拡張機能設定を構成することはできないので、 **[次へ]** をクリックします。  
  
12. サブスクリプションに対するレポートのパラメーター値を指定し、 **[次へ]** をクリックします。  
  
13. サブスクリプションをいつ処理するかを指定します。 **[レポート サーバーでのレポート データの更新時]** は選択しないでください。 この設定はスナップショットにのみ使用します。 既存のスケジュールを使用する場合は、 **[共有スケジュールで実行する]** を選択してください。  
  
     カスタム スケジュールを作成する場合は、 **[このサブスクリプション用に作成されたスケジュールで実行します]** をクリックし、 **[次へ]** をクリックします。 スケジュールを構成し、 **[完了]** をクリックします。  
  
    > [!NOTE]  
    >  サブスクライバーが最新のレポートを受け取るには、構成するスケジュールが、サブスクライバーに対して定義したレポート配信スケジュールと一致する必要があります。 詳細については、「[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)」を参照してください。  
  
14. 以下のように、レポートの実行オプションを構成します。 レポート ページで、 **[プロパティ]** タブをクリックします。  
  
15. 左フレームの **[実行]** タブをクリックします。  
  
16. このページで、 **[最新データを使用して、このレポートを表示する]** を選択します。  
  
17. 次の 2 つのキャッシュ オプションのいずれかを選択し、以下のように有効期限を構成します。  
  
    -   キャッシュされたコピーが、特定の期間が過ぎた後で有効期限が切れるようにするには、**レポートの一時コピーをキャッシュします。レポートのコピーの有効期限は数分後に切れます** をクリックします。 レポートの有効期限を分単位で入力します。  
  
    -   キャッシュされたコピーが、スケジュールに基づいて有効期限が切れるようにするには、**[レポートの一時コピーをキャッシュします。次のスケジュールでレポートのコピーの有効期限は切れます。]** をクリックします。 **[構成]** をクリックするか、共有スケジュールを選択して、レポートの有効期限をスケジュールします。  
  
18. **[適用]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [データ ドリブン サブスクリプション](../../reporting-services/subscriptions/data-driven-subscriptions.md)   
 [データ ドリブン サブスクリプションの作成 &#40;SSRS チュートリアル&#41;](../../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md)   
 [パフォーマンス、スナップショット、キャッシュ &#40;Reporting Services&#41;](../../reporting-services/report-server/performance-snapshots-caching-reporting-services.md)   
 [レポート処理プロパティの設定](../../reporting-services/report-server/set-report-processing-properties.md)   
 [レポートのキャッシュ &#40;SSRS&#41;](../../reporting-services/report-server/caching-reports-ssrs.md)  
  
  
