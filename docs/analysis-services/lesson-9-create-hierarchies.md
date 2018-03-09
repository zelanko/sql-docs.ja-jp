---
title: "レッスン 10: 階層の作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/10/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: 1e2561d3-4890-4495-a9cd-84eb88508938
caps.latest.revision: "23"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 7a09f05b8e508205f3e2a8863627c12afdec9c64
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="lesson-9-create-hierarchies"></a>レッスン 9: 階層を作成します。
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

このレッスンでは、階層を作成します。 階層は、複数のレベルに分類された列のグループです。たとえば、Geography という階層に、Country、State、County、および City というサブレベルを含めることができます。 階層は、あるレポート クライアント アプリケーション フィールドの一覧の他の列とは分けて表示できるため、クライアントのユーザーは簡単に移動し、レポートに含めることができます。 詳細については、次を参照してください。[階層](../analysis-services/tabular-models/hierarchies-ssas-tabular.md)です。  
  
階層を作成するには、モデル デザイナーを使用するあります*ダイアグラム ビュー*です。 作成して、階層の管理は、データ ビューではサポートされていません。  
  
このレッスンの推定所要時間: **20 分**  
  
## <a name="prerequisites"></a>Prerequisites  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 8: パースペクティブの作成](../analysis-services/lesson-8-create-perspectives.md)です。  
  
## <a name="create-hierarchies"></a>階層を作成する  
  
#### <a name="to-create-a-category-hierarchy-in-the-dimproduct-table"></a>DimProduct テーブルに Category 階層を作成するには  
  
1.  モデル デザイナー (ダイアグラム ビュー) を右クリックし、 **DimProduct**テーブル >**階層の作成**です。 テーブル ウィンドウの下部に新しい階層が表示されます。 階層の名前を変更**カテゴリ**です。  
  
2.  をクリックし、ドラッグ、 **ProductCategoryName**を新しい列**カテゴリ**階層。  
  
3.  **カテゴリ**階層を右クリックし、 **ProductCategoryName** > **の名前を変更**、し、入力**カテゴリ**です。  
  
    > [!NOTE]  
    > 階層内の列の名前を変更しても、テーブル内のその列の名前は変更されません。 階層内の列は、テーブル内の列の 1 つの表現形態に過ぎません。  
  
4.  をクリックし、ドラッグ、 **ProductSubcategoryName**列を**カテゴリ**階層。 名前を変更して**Subcategory**です。 
  
5.  右クリックし、 **ModelName**列 >**階層を追加する**、し、**カテゴリ**です。 同じ操作を行います**EnglishProductName**です。 階層内のこれらの列の名前を変更**モデル**と**製品**です。  

    ![として表形式の lesson9-分類](../analysis-services/media/as-tabular-lesson9-category.png)
  
#### <a name="to-create-hierarchies-in-the-dimdate-table"></a>DimDate テーブルの階層を作成するには  
  
1.  **DimDate**という名前の新しい階層を作成するテーブルで、**カレンダー**です。  
  
3.  次の列での順序を追加します。

    *  CalendarYear
    *  CalendarSemester
    *  CalendarQuarter
    *  月表示カレンダー
    *  DayNumberOfMonth
    
4.  **DimDate**テーブルで、作成、**会計**階層。 次の列を含めます。  
  
    *  FiscalYear
    *  FiscalSemester
    *  FiscalQuarter
    *  月表示カレンダー
    *  DayNumberOfMonth
  
5.  最後に、 **DimDate**テーブルで、作成、 **ProductionCalendar**階層。 次の列を含めます。  
    *  CalendarYear
    *  WeekNumberOfYear
    *  DayNumberOfWeek
  
 ## <a name="whats-next"></a>次の操作
次のレッスンに移動:[レッスン 10: パーティションの作成](../analysis-services/lesson-10-create-partitions.md)です。 
  
  
