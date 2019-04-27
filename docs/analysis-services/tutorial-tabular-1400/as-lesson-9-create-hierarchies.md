---
title: Analysis Services チュートリアル レッスン 9:階層を作成する |Microsoft Docs
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfiles"
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 92f83e1e2b3553f85301574e98f95ed7e22c1184
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62469786"
---
# <a name="create-hierarchies"></a>階層を作成する

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

このレッスンでは、階層を作成します。 階層は、レベルに分類された列のグループです。 たとえば、Geography 階層と、国、州、国、および市区町村の下位レベルの場合があります。 階層は、あるレポート クライアント アプリケーション フィールドの一覧の他の列とは分けて表示できるため、クライアントのユーザーは簡単に移動し、レポートに含めることができます。 詳細についてを参照してください[階層。](../tabular-models/hierarchies-ssas-tabular.md)
  
階層を作成するには、モデル デザイナーを使用して、*ダイアグラム ビュー*します。 作成して、階層の管理は、データ ビューではサポートされていません。  
  
このレッスンを完了するまでに時間を推定するには。**20 分**  
  
## <a name="prerequisites"></a>前提条件  

この記事では、順序で完了する必要があります、表形式モデルのチュートリアルの一部です。 このレッスンでは、タスクを実行する前に、前のレッスンを完了が必要があります。[レッスン 8: パースペクティブを作成する](../tutorial-tabular-1400/as-lesson-8-create-perspectives.md)します。  
  
## <a name="create-hierarchies"></a>階層を作成する  
  
#### <a name="to-create-a-category-hierarchy-in-the-dimproduct-table"></a>DimProduct テーブルに Category 階層を作成するには  
  
1.  モデル デザイナー (ダイアグラム ビュー) でを右クリックし、 **DimProduct**テーブル >**階層の作成**です。 テーブル ウィンドウの下部に新しい階層が表示されます。 階層の名前を変更**カテゴリ**します。  
  
2.  クリックしてドラッグし、 **ProductCategoryName**を新しい列**カテゴリ**階層。  
  
3.  **カテゴリ**階層を右クリックして**ProductCategoryName** > **の名前を変更**、し、入力**カテゴリ**します。  
  
    > [!NOTE]  
    > 階層内の列の名前を変更しても、テーブル内のその列の名前は変更されません。 階層内の列は、テーブル内の列の 1 つの表現形態に過ぎません。  
  
4.  クリックしてドラッグし、 **ProductSubcategoryName**列を**カテゴリ**階層。 名前を変更して**Subcategory**します。 
  
5.  右クリックし、 **ModelName**列 >**階層を追加する**、し、**カテゴリ**します。 名前を変更して**モデル**します。

6.  最後に、追加**EnglishProductName**カテゴリ階層にします。 名前を変更して**製品**します。  

    ![as-lesson9-category](../tutorial-tabular-1400/media/as-lesson9-category.png)
  
#### <a name="to-create-hierarchies-in-the-dimdate-table"></a>DimDate テーブルに階層を作成するには  
  
1.  **DimDate**という名前の階層を作成するテーブルで、**カレンダー**します。  
  
3.  次の列を順番に追加します。

    *  CalendarYear
    *  CalendarSemester
    *  CalendarQuarter
    *  MonthCalendar
    *  DayNumberOfMonth
    
4.  **DimDate**テーブルで、作成、**会計**階層。 次の列での順序のとおりです。  
  
    *  FiscalYear
    *  FiscalSemester
    *  FiscalQuarter
    *  MonthCalendar
    *  DayNumberOfMonth
  
5.  最後に、 **DimDate**テーブルで、作成、 **ProductionCalendar**階層。 次の列での順序のとおりです。  
    *  CalendarYear
    *  WeekNumberOfYear
    *  DayNumberOfWeek
  
 ## <a name="whats-next"></a>次の操作

[レッスン 10:パーティションの作成](../tutorial-tabular-1400/as-lesson-10-create-partitions.md)です。 
  
  
