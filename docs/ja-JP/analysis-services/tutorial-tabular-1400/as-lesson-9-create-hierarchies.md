---
title: 'Analysis Services のチュートリアル レッスン 9: 階層を作成 |Microsoft ドキュメント'
description: ''
ms.prod_service: analysis-services, azure-analysis-services
services: analysis-services
ms.suite: pro-bi
documentationcenter: ''
author: Minewiskan
manager: kfile
editor: ''
tags: ''
ms.assetid: ''
ms.service: analysis-services
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.date: 02/20/2018
ms.author: owend
monikerRange: '>= sql-analysis-services-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 95953da3ff2fc71ac39db75daeea6dacdc0854f5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="create-hierarchies"></a>階層を作成する

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

このレッスンでは、階層を作成します。 階層は、レベルで並べられた列のグループです。 たとえば、Geography 階層と、国、州、国、および市の下位レベルの場合があります。 階層は、あるレポート クライアント アプリケーション フィールドの一覧の他の列とは分けて表示できるため、クライアントのユーザーは簡単に移動し、レポートに含めることができます。 詳細については、次を参照してください[階層。](../tabular-models/hierarchies-ssas-tabular.md)
  
階層を作成するには、モデル デザイナーを使用して*ダイアグラム ビュー*です。 作成して、階層の管理は、データ ビューではサポートされていません。  
  
このレッスンの推定所要時間: **20 分**  
  
## <a name="prerequisites"></a>前提条件  

この記事は、順番に従って実行する必要がありますが、テーブル モデリング チュートリアルの一部です。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 8: パースペクティブの作成](../tutorial-tabular-1400/as-lesson-8-create-perspectives.md)です。  
  
## <a name="create-hierarchies"></a>階層を作成する  
  
#### <a name="to-create-a-category-hierarchy-in-the-dimproduct-table"></a>DimProduct テーブルに Category 階層を作成するには  
  
1.  モデル デザイナー (ダイアグラム ビュー) を右クリックし、 **DimProduct**テーブル >**階層の作成**です。 テーブル ウィンドウの下部に新しい階層が表示されます。 階層の名前を変更**カテゴリ**です。  
  
2.  をクリックし、ドラッグ、 **ProductCategoryName**を新しい列**カテゴリ**階層。  
  
3.  **カテゴリ**階層を右クリックして**ProductCategoryName** > **の名前を変更**、し、入力**カテゴリ**です。  
  
    > [!NOTE]  
    > 階層内の列の名前を変更しても、テーブル内のその列の名前は変更されません。 階層内の列は、テーブル内の列の 1 つの表現形態に過ぎません。  
  
4.  をクリックし、ドラッグ、 **ProductSubcategoryName**列を**カテゴリ**階層。 名前を変更して**Subcategory**です。 
  
5.  右クリックし、 **ModelName**列 >**階層を追加する**、し、**カテゴリ**です。 名前を変更して**モデル**です。

6.  最後に、追加**EnglishProductName**カテゴリ階層にします。 名前を変更して**製品**です。  

    ![as-lesson9-category](../tutorial-tabular-1400/media/as-lesson9-category.png)
  
#### <a name="to-create-hierarchies-in-the-dimdate-table"></a>DimDate テーブルの階層を作成するには  
  
1.  **DimDate**という名前の階層を作成するテーブルで、**カレンダー**です。  
  
3.  次の列での順序を追加します。

    *  CalendarYear
    *  CalendarSemester
    *  CalendarQuarter
    *  月表示カレンダー
    *  DayNumberOfMonth
    
4.  **DimDate**テーブルで、作成、**会計**階層。 次の列での順序のとおりです。  
  
    *  FiscalYear
    *  FiscalSemester
    *  FiscalQuarter
    *  月表示カレンダー
    *  DayNumberOfMonth
  
5.  最後に、 **DimDate**テーブルで、作成、 **ProductionCalendar**階層。 次の列での順序のとおりです。  
    *  CalendarYear
    *  WeekNumberOfYear
    *  DayNumberOfWeek
  
 ## <a name="whats-next"></a>次の操作

[レッスン 10: パーティションの作成](../tutorial-tabular-1400/as-lesson-10-create-partitions.md)です。 
  
  
