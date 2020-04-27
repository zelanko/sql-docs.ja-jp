---
title: 'レッスン 4: 日付テーブルとしてマークする |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c32cc336-b7d8-4122-9d62-4936344d2315
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 26877c4892b050cbf9c8dcc6553530dff513f8fc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66078786"
---
# <a name="lesson-4-mark-as-date-table"></a>レッスン 4:日付テーブルとしてマーク
  「レッスン 2: データの追加」では、DimDate という名前のディメンション テーブルをインポートしました。 次に、「レッスン 3: 列名の変更」では DimDate テーブルの名前を単純な Date に変更しました。 このモデルでは、このテーブルは Date という名前になりましたが、実際は日付と時刻のデータが含まれた*日付テーブル*になります。  
  
 計算でタイム インテリジェンス関数を使用する場合は必ず、少し後でメジャーを作成することになるので、 *Date table* と、そのテーブル内で一意の識別子である *Date column* を含む日付テーブル プロパティを指定する必要があります。 他のテーブルと日付テーブルの間で有効なリレーションシップを作成できます。これは、DAX のタイム インテリジェンス機能を使用して計算するために必要です。  
  
 このレッスンでは、インポートされ名前を変更された Date テーブルを *日付テーブル* 、Date テーブルの Date 列を *日付列* (一意識別子) として設定します。 名前の日付を使用すると、混乱を招く可能性がありますが、すぐに考えてみましょう。  
  
 このレッスンの推定所要時間: **3 分**  
  
## <a name="prerequisites"></a>前提条件  
 このトピックは、表形式モデルのチュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンの実習を行う前に、前のレッスン [「レッスン 3: 列名の変更」](rename-columns.md)を完了している必要があります。  
  
### <a name="to-set-mark-as-date-table"></a>Mark as Date Table を設定する  
  
1.  モデル デザイナーで、 **Date** テーブル (タブ) をクリックします。  
  
2.  [**テーブル**] メニューをクリックし、[**日付**] をクリックして、[**日付テーブルとしてマーク**] をクリックします。  
  
3.  **[日付テーブルとしてマーク]** ダイアログ ボックスの **[日付]** ボックスの一覧で、一意の識別子として **[Date]** 列を選択します。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルを続行するには、次のレッスン「 [レッスン 5: リレーションシップの作成](lesson-4-create-relationships.md)」に進んでください。  
  
  
