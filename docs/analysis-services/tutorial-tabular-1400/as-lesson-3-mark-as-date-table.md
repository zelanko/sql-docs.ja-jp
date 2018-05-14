---
title: 'Analysis Services のチュートリアル レッスン 3: 日付テーブルとしてマーク |Microsoft ドキュメント'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 82b4093aa1a46cf1a7bb14b4c689ba6ba09e4d2b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="mark-as-date-table"></a>日付テーブルとしてマーク

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

レッスン 2: データの取得、インポートしたという名前のディメンション テーブル**DimDate**です。 モデルのこのテーブルが DimDate という名前は、中に、できるとも呼ばれます、*日付テーブル*日付と時刻のデータが含まれていることにします。  
  
含むプロパティを指定する必要があります、後でメジャーを作成する場合と同様に、DAX タイム インテリジェンス関数を使用するたびに、*日付テーブル*および一意の識別子*日付列*そのテーブルにします。
  
このレッスンではマークする、 **DimDate**としてテーブル、*日付テーブル*と**日付**(テーブルの列、日) として、*日付列*(一意の識別子) です。  

日付テーブルと日付の列をマークする前に行うことで、モデルをわかりやすくする少しハウスキーピング絶好のタイミングを勧めします。 という名前の列を DimDate テーブルで注目**FullDateAlternateKey**です。 この列には、テーブルに含まれる各カレンダー年の日の 1 つの行が含まれています。 メジャーの数式とレポートに、この列を多く使用します。 しかし、FullDateAlternateKey は実際にはこの列の適切な識別子。 名前を変更する**日付**、容易に識別および数式が含まれます。 可能な限りは、SSDT でのクライアント レポート アプリケーションを識別しやすいようにするテーブルおよび列のようなオブジェクトの名前を変更することをお勧めします。 
  
このレッスンを完了する時間を推定: **3 分間**  
  
## <a name="prerequisites"></a>前提条件  

この記事は、順番に従って実行する必要がありますが、テーブル モデリング チュートリアルの一部です。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 2: データの取得](../tutorial-tabular-1400/as-lesson-2-get-data.md)です。 

### <a name="to-rename-the-fulldatealternatekey-column"></a>FullDateAlternateKey 列の名前を変更するには

1.  モデル デザイナーで、をクリックして、 **DimDate**テーブル。

2.  ヘッダーをダブルクリックして、 **FullDateAlternateKey**  列の名前を変更する**日付**です。

  
### <a name="to-set-mark-as-date-table"></a>日付テーブルとして設定する  
  
1.  **[日付]** 列を選択し、 **[プロパティ]** ウィンドウの **[データ型]** で  **[日付]** が必ず選択されているようにします。  
  
2.  **[テーブル]** メニュー、**[日付]****[日付テーブルとしてマーク]** の順にクリックします。  
  
3.  **[日付テーブルとしてマーク]** ダイアログ ボックスの **[日付]** ボックスの一覧で、一意の識別子として **[Date]** 列を選択します。 これは通常、既定で選択します。 **[OK]** をクリックします。 

    ![as-lesson3-date-table](../tutorial-tabular-1400/media/as-lesson3-date-table.png)
  

## <a name="whats-next"></a>次の操作

[レッスン 4: リレーションシップの作成](../tutorial-tabular-1400/as-lesson-4-create-relationships.md)です。
  
