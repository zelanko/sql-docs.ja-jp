---
title: 'レッスン 3: 日付テーブルとしてマーク |Microsoft Docs'
ms.date: 08/22/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7cb63b6cb67303dd763263b7d9dbeea30cfc4e3b
ms.sourcegitcommit: e8e013b4d4fbd3b25f85fd6318d3ca8ddf73f31e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/23/2018
ms.locfileid: "42791983"
---
# <a name="lesson-3-mark-as-date-table"></a>レッスン 3: 日付テーブルとしてマーク
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

「レッスン 2: データの追加」では、DimDate という名前のディメンション テーブルをインポートしました。 モデルでこのテーブルは DimDate と命名、中にそのことができますとも呼ばれます、*日付テーブル*日付と時刻のデータが含まれていることにします。  
  
含む日付テーブル プロパティを指定する必要があります、メジャー、少し後で作成するときに行いますの計算で DAX タイム インテリジェンス関数を使用するたびに、*日付テーブル*および一意の識別子*日付列*そのテーブルにします。
  
このレッスンでは、DimDate テーブルとしてマークします、*日付テーブル*として (、Date テーブルの Date 列、*日付列*(一意識別子)。  

日付テーブルと日付列をマークして、前に、モデルを理解しやすいようにを少しハウスキーピングを実行する必要があります。 という名前の列 DimDate テーブルに表示されます**FullDateAlternateKey**します。 毎日、テーブルに含まれる各カレンダー年の 1 つの行が含まれています。 使用するこのコラムの多くとレポート メジャーの数式にします。 しかし、本当にこの列の適切な識別子が FullDateAlternateKey ではありません。 名前を変更します**日付**、簡単に識別し、式に含めることができます。 可能であればは Power BI や Excel などのアプリケーションをレポート作成クライアントで識別しやすいようにするテーブルと列のようなオブジェクトの名前を変更することをお勧めします。 
  
このレッスンの推定所要時間: **3 分**  
  
## <a name="prerequisites"></a>Prerequisites  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 2: データを追加する](../analysis-services/lesson-2-add-data.md)します。 

### <a name="to-rename-the-fulldatealternatekey-column"></a>FullDateAlternateKey 列の名前を変更するには

1.  モデル デザイナーで、クリックして、 **DimDate**テーブル。

2.  ヘッダーをダブルクリック、 **FullDateAlternateKey**列、しに名前を変更**日付**します。

  
### <a name="to-set-mark-as-date-table"></a>日付テーブルとして設定する  
  
1.  **[日付]** 列を選択し、 **[プロパティ]** ウィンドウの **[データ型]** で  **[日付]** が必ず選択されているようにします。  
  
2.  **[テーブル]** メニュー、**[日付]****[日付テーブルとしてマーク]** の順にクリックします。  
  
3.  **[日付テーブルとしてマーク]** ダイアログ ボックスの **[日付]** ボックスの一覧で、一意の識別子として **[Date]** 列を選択します。 既定では、通常、選択されます。 **[OK]** をクリックします。 

    ![-テーブル-lesson3-日付-テーブルとして](../analysis-services/media/as-tabular-lesson3-date-table.png)
  

## <a name="whats-next"></a>次の操作
次のレッスンに移動:[レッスン 4: リレーションシップの作成](../analysis-services/lesson-4-create-relationships.md)です。
  
