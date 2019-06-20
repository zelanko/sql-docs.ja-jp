---
title: 'レッスン 9: 階層を作成する |Microsoft Docs'
ms.date: 05/07/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 388df29badcde95c04c3db3604af63ed995666ac
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65403744"
---
# <a name="lesson-9-create-hierarchies"></a>レッスン 9: 階層を作成する
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

このレッスンでは、階層を作成します。 階層は、複数のレベルに分類された列のグループです。たとえば、Geography という階層に、Country、State、County、および City というサブレベルを含めることができます。 階層は、あるレポート クライアント アプリケーション フィールドの一覧の他の列とは分けて表示できるため、クライアントのユーザーは簡単に移動し、レポートに含めることができます。 詳細についてを参照してください。[階層](../tabular-models/hierarchies-ssas-tabular.md)します。  
  
階層を作成するには、モデル デザイナーを使用します*ダイアグラム ビュー*します。 作成して、階層の管理は、データ ビューではサポートされていません。  
  
このレッスンを完了するまでに時間を推定するには。**20 分**  
  
## <a name="prerequisites"></a>前提条件  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンでは、タスクを実行する前に、前のレッスンを完了が必要があります。[レッスン 8: パースペクティブを作成する](lesson-8-create-perspectives.md)します。  
  
## <a name="create-hierarchies"></a>階層を作成する  
  
#### <a name="to-create-a-category-hierarchy-in-the-dimproduct-table"></a>DimProduct テーブルに Category 階層を作成するには  
  
1.  モデル デザイナー (ダイアグラム ビュー) でを右クリックし、 **DimProduct**テーブル >**階層の作成**です。 テーブル ウィンドウの下部に新しい階層が表示されます。 階層の名前を変更**カテゴリ**します。  
  
2.  クリックしてドラッグし、 **ProductCategoryName**を新しい列**カテゴリ**階層。  
  
3.  **カテゴリ**階層を右クリックし、 **ProductCategoryName** > **の名前を変更**、し、入力**カテゴリ**します。  
  
    > [!NOTE]  
    > 階層内の列の名前を変更しても、テーブル内のその列の名前は変更されません。 階層内の列は、テーブル内の列の 1 つの表現形態に過ぎません。  
  
4.  クリックしてドラッグし、 **ProductSubcategoryName**列を**カテゴリ**階層。 名前を変更して**Subcategory**します。 
  
5.  右クリックし、 **ModelName**列 >**階層を追加する**、し、**カテゴリ**します。 同じ**EnglishProductName**します。 これらの列、階層内の名前を変更**モデル**と**製品**します。  

    ![as-tabular-lesson9-category](media/as-tabular-lesson9-category.png)
  
#### <a name="to-create-hierarchies-in-the-dimdate-table"></a>DimDate テーブルに階層を作成するには  
  
1.  **DimDate**という名前の新しい階層を作成するテーブルで、**カレンダー**します。  
  
3.  次の列を順番に追加します。

    *  CalendarYear
    *  CalendarSemester
    *  CalendarQuarter
    *  MonthCalendar
    *  DayNumberOfMonth
    
4.  **DimDate**テーブルで、作成、**会計**階層。 次の列が含まれます。  
  
    *  FiscalYear
    *  FiscalSemester
    *  FiscalQuarter
    *  MonthCalendar
    *  DayNumberOfMonth
  
5.  最後に、 **DimDate**テーブルで、作成、 **ProductionCalendar**階層。 次の列が含まれます。  
    *  CalendarYear
    *  WeekNumberOfYear
    *  DayNumberOfWeek
  
 ## <a name="whats-next"></a>次の操作
次のレッスンに移動します。[レッスン 10:パーティションの作成](lesson-10-create-partitions.md)です。 
  
  
