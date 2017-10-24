---
title: "レッスン 4: 日付テーブルとしてマークして |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/27/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: c32cc336-b7d8-4122-9d62-4936344d2315
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5bef08da2c79aa1b17241300d1b9b31e7b977781
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-3-mark-as-date-table"></a>レッスン 3: が日付テーブルとしてマークします。
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

「レッスン 2: データの追加」では、DimDate という名前のディメンション テーブルをインポートしました。 モデルのこのテーブルが DimDate という名前は、中に、できるとも呼ばれます、*日付テーブル*日付と時刻のデータが含まれていることにします。  
  
メジャー、少し後で作成するときの操作すると、計算で DAX タイム インテリジェンス関数を使用するたびに含める日付テーブルのプロパティを指定する必要があります、*日付テーブル*および一意の識別子*日付列*そのテーブルにします。
  
このレッスンと DimDate テーブルをマークするが、*日付テーブル*として (、Date テーブル内) Date 列、*日付列*(一意の識別子)。  

日付テーブルと日付の列をマークしてには、モデルを理解しやすくには少しハウスキーピング操作を行いますが必要です。 わかります DimDate テーブルのという名前の列**FullDateAlternateKey**です。 テーブルに含まれる各カレンダー年の日の 1 つの行が含まれています。 使用するこの列の多くとレポート メジャーの数式にします。 しかし、本当にこの列の適切な識別子が FullDateAlternateKey ではありません。 名前を変更**日付**、容易に識別および数式が含まれます。 可能な限りは、テーブルおよび列を Power BI と Excel のようなアプリケーションをレポート作成クライアントで識別しやすいようになどのオブジェクトの名前を変更することをお勧めします。 
  
このレッスンの推定所要時間: **3 分**  
  
## <a name="prerequisites"></a>前提条件  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 2: データを追加](../analysis-services/lesson-2-add-data.md)です。 

### <a name="to-rename-the-fulldatealternatekey-column"></a>FullDateAlternateKey 列の名前を変更するには

1.  モデル デザイナーで、をクリックして、 **DimDate**テーブル。

2.  ヘッダーをダブルクリック、 **FullDateAlternateKey**  列の名前を変更する**日付**です。

  
### <a name="to-set-mark-as-date-table"></a>日付テーブルとして設定する  
  
1.  **[日付]** 列を選択し、 **[プロパティ]** ウィンドウの **[データ型]**で  **[日付]** が必ず選択されているようにします。  
  
2.  **[テーブル]** メニュー、**[日付]****[日付テーブルとしてマーク]** の順にクリックします。  
  
3.  **[日付テーブルとしてマーク]** ダイアログ ボックスの **[日付]** ボックスの一覧で、一意の識別子として **[Date]** 列を選択します。 既定では通常選択されます。 **[OK]**をクリックします。 

    ![-テーブル-lesson3-日付のテーブルとして](../analysis-services/media/as-tabular-lesson3-date-table.png)
  

## <a name="whats-next"></a>次の操作
次のレッスンに移動:[レッスン 4: リレーションシップの作成](../analysis-services/lesson-4-create-relationships.md)です。
  

