---
title: "共有データセット (web ポータル) の操作 |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2641ea84-9343-4e6f-aec1-25339031b163
caps.latest.revision: 7
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: 40f29d8cd68a60f88e2077a16f745f8e37bf35f2
ms.contentlocale: ja-jp
ms.lasthandoff: 07/03/2017

---
# 共有データセットの web ポータルを作業します。
<a id="work-with-shared-datasets---web-portal" class="xliff"></a>

[!INCLUDE[ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../includes/ssrs-appliesto-pbirs.md)]

共有データセットを使用すると、データセットを使用するレポートおよび他のカタログ アイテムとは別にデータセットの設定を管理できます。 共有データセットは、ページ割り当てされたレポートおよびモバイル レポートで KPI と共に使用できます。

Web ポータル内の共有データセットのプロパティを表示および管理できます。 Web ポータルからレポート ビルダーを起動して共有データセットを作成または編集できます。

## 共有データセットを作成する
<a id="create-a-shared-dataset" class="xliff"></a>
  
新しい共有データセットを作成するには、次のようにします。  
  
1.  メニュー バーから [新規] を選択します。  
  
2.  **[データセット]**を選択します。  
  
    ![ssRSDataset-NewDataset](../reporting-services/media/ssrsdataset-newdataset.png)  
  
3.  レポート ビルダーが起動されるか、またはレポート ビルダーをダウンロードするように求められます。  
  
4.  **[新しいレポートまたはデータセット]** ダイアログで、このデータセットに使用するデータ ソース接続を選択します。 共有データ ソースの場所を参照することが必要な場合があります。  
  
5.  **[作成]**を選択します。  
  
6.  データセットを作成し、画面左上の **[保存]** アイコンを選択してデータセットをレポート サーバーに保存します。  
  
## 既存の共有データセットを管理する
<a id="manage-an-existing-shared-dataset" class="xliff"></a>
  
既存の共有データセットを管理するには、次のようにします。  
  
> [!NOTE]
> フォルダーに共有データセットが表示されない場合は、データセットを表示していることを確認します。 Web ポータルの右上にあるメニュー バーで **[表示]** を選択します。 **[データセット]** がオンになっていることを確認します。  
  
1.  選択、**省略記号 (...)**を管理するデータセットのです。  
  
    ![ssRSDataset-Ellipse](../reporting-services/media/ssrsdataset-ellipse.png)  
  
2.  **[管理]** を選択すると、編集画面に移動します。  
  
    ![ssRSDataset-Manage](../reporting-services/media/ssrsdataset-manage.png)  
  
## プロパティ
<a id="properties" class="xliff"></a>
  
プロパティ画面では、データセットの **[名前]** と **[説明]** を変更できます。 また、 **[削除]**、 **[移動]**、 **[レポート ビルダーでの編集]**、 **[ダウンロード]** 、 **[置換]**を選択することもできます。  
  
![ssRSdataset-Properties](../reporting-services/media/ssrsdataset-properties.png)  
  
## キャッシュ
<a id="caching" class="xliff"></a>
  
データセットのデータのキャッシュに関するオプションがあります。 簡単な選択で始めことができます。  
  
1.  **[常に最新データを使用して、このレポートを実行する]** は、要求されたらデータ ソースにクエリを発行します。  
  
2.  **[このレポートのコピーをキャッシュし、使用できるときはそれを使用する]** は、データの一時的なコピーをキャッシュに格納し、このデータセットを使用するアイテムで使用します。 再度データセット クエリを実行することなくデータがキャッシュから返されるので、通常はキャッシュによってパフォーマンスが向上します。  
  
![ssRSDataset-Caching1](../reporting-services/media/ssrsdataset-caching1.png)  
  
**[このレポートのコピーをキャッシュし、使用できるときはそれを使用する]** を選択すると、さらにいくつかのオプションが表示されます。  
  
![ssRSDataset-Caching2](../reporting-services/media/ssrsdataset-caching2.png)  
  
### キャッシュの有効期限
<a id="cache-expiration" class="xliff"></a>  
  
一定の時間が経過したら共有データセットのキャッシュを期限切れにするか、またはスケジュールに従って行うかを制御できます。 共有スケジュールを使用できます。  
  
![ssRSDataset-Caching3](../reporting-services/media/ssrsdataset-caching3.png)  
  
> [!NOTE]
> 有効期限を設定しても、キャッシュは更新されません。 キャッシュ更新計画がない場合、データはデータセットの次の実行時に更新されます。  
  
### キャッシュ更新計画
<a id="cache-refresh-plans" class="xliff"></a>  
  
[キャッシュ更新計画] を使用すると、共有データセットのデータの一時コピーを事前にキャッシュに読み込むスケジュールを作成できます。 更新計画には、スケジュールと、パラメーターの値を指定または上書きするためのオプションが含まれます。 読み取り専用にマークされているパラメーターの値を上書きすることはできません。 複数の更新計画を作成して使用できます。   
  
キャッシュ更新計画の共有データセットの追加、削除、変更が可能な既定のロールの割り当ては、コンテンツ マネージャー、個人用レポート、およびパブリッシャーです。  
  
以上のキャッシュ オプションを適用した後は、キャッシュ更新計画を定義できます。 そのためには、キャッシュの設定を適用した後で表示される **[更新計画の管理]** リンクを選択します。 キャッシュ更新計画のページが表示されます。   
  
新しいキャッシュ更新計画を作成するには、 **[新しいキャッシュ更新計画]**を選択します。 計画の名前を入力し、スケジュールを指定します。 データセットでパラメーターが定義されている場合、その一覧が表示され、読み取り専用以外のパラメーターには値を指定できます。  
  
完了したら、 **[キャッシュ更新計画の作成]**を選択します。  
  
![ssRSDataset-Caching4](../reporting-services/media/ssrsdataset-caching4.png)  
  
> [!NOTE]
> キャッシュ更新計画を作成するには、SQL Server エージェントが動作している必要があります。  
  
一覧に表示されている計画は、 **[編集]** または **[削除]** できます。 **[既存のものから新規作成]** オプションは、キャッシュ更新計画が 1 つだけ選択されている場合に有効になります。 このオプションでは、新しい更新計画が元の計画からコピーされて作成されます。 キャッシュ更新計画ページは、選択された計画の詳細があらかじめ設定された状態で開きます。 その後、更新計画オプションを変更して、新しい説明で計画を保存できます。  

他に質問しますか。 [Reporting Services のフォーラムで質問してみてください。](http://go.microsoft.com/fwlink/?LinkId=620231)
