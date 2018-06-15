---
title: 'Analysis Services tutorial 補足のレッスン: 不規則階層 |Microsoft ドキュメント'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bc5a2164576e2e6142d8835dad6f6c114b7a9c5b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34043926"
---
# <a name="supplemental-lesson---ragged-hierarchies"></a>補足のレッスンの不規則階層

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

この補足のレッスンと解決する一般的な問題をさまざまなレベルでの空白の値 (メンバー) を含む階層にピボットしています。 たとえば、高度なマネージャーが各部門のマネージャーと直属の部下として管理者以外の両方を持つ組織。 または、地理的な階層は、国-地域-市、いくつかの都市が親の州や都道府県などワシントン d. c.、バチカン市がないので構成されます。 階層には、空のメンバーが持つ、異なる、または幅合わせしない、レベルに多くの場合は至ります。

![as-lesson-detail-ragged-hierarchies-table](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-table.png)

1400 互換性レベルの表形式モデルがある追加の**メンバーを非表示**階層のプロパティです。 **既定**設定では、任意のレベルで空のメンバーがないと仮定します。 **空のメンバーを非表示に**設定は、ピボット テーブル レポートやレポートに追加されたときに、階層から空のメンバーを除外します。  
  
このレッスンの推定所要時間: **20 分**  
  
## <a name="prerequisites"></a>前提条件  
この補足のレッスン記事は、テーブル モデリング チュートリアルの一部です。 この補足のレッスンでは、タスクを実行する前に作成した前のレッスンをすべて完了した Adventure Works Internet Sales サンプル モデル プロジェクトがあるか。 

このチュートリアルの一部として AW Internet Sales プロジェクトを作成した場合、モデルはまだ含まれていませんデータか、不規則階層。 この補足のレッスンを完了するには、は、まず、いくつか追加のテーブルを追加することで、問題、リレーションシップ、計算列、メジャー、および新しい組織階層を作成する必要があります。 その一部は、15 分ぐらいかかります。 その後、ほんの数分で解決するためが表示されます。  

## <a name="add-tables-and-objects"></a>テーブルおよびオブジェクトを追加します。
  
### <a name="to-add-new-tables-to-your-model"></a>モデルに新しいテーブルを追加するには
  
1.  表形式モデル エクスプ ローラーで、展開**データ ソース**、し、接続を右クリックして >**新しいテーブルのインポート**です。
  
2.  ナビゲーターで、次のように選択します。 **DimEmployee**と**FactResellerSales**、順にクリック**OK**です。

3.  クエリ エディターで、クリックして**インポート**

4.  次の作成[リレーションシップ](../tutorial-tabular-1400/as-lesson-4-create-relationships.md):

    | 表 1           | 列       | フィルターの方向   | 表 2     | 列      | Active |
    |-------------------|--------------|--------------------|-------------|-------------|--------|
    | FactResellerSales | OrderDateKey | 既定値            | DimDate     | 日付        | はい    |
    | FactResellerSales | DueDate      | 既定値            | DimDate     | 日付        | いいえ     |
    | FactResellerSales | ShipDateKey  | 既定値            | DimDate     | 日付        | いいえ     |
    | FactResellerSales | ProductKey   | 既定値            | DimProduct  | ProductKey  | はい    |
    | FactResellerSales | EmployeeKey  | 両方のテーブルに | DimEmployee | EmployeeKey | はい    |

5. **DimEmployee**テーブルで、次の作成、[集計列](../tutorial-tabular-1400/as-lesson-5-create-calculated-columns.md): 

    **[パス]** 
    ```
    =PATH([EmployeeKey],[ParentEmployeeKey])
    ```

    **FullName** 
    ```
    =[FirstName] & " " & [MiddleName] & " " & [LastName]
    ```

    **Level1** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],1,1)) 
    ```

    **レベル 2** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],2,1)) 
    ```

    **Level3** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],3,1)) 
    ```

    **Level4** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],4,1)) 
    ```

    **Level5** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],5,1)) 
    ```

6.  **DimEmployee**テーブルで、作成、[階層](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md)という**組織**です。 次の列での順序を追加: **Level1**、 **Level2**、 **Level3**、 **Level4**、 **Level5**です。

7.  **FactResellerSales**テーブルで、次の作成、[メジャー](../tutorial-tabular-1400/as-lesson-6-create-measures.md):

    ```
    ResellerTotalSales:=SUM([SalesAmount])
    ```

8.  使用して[Excel で分析](../tutorial-tabular-1400/as-lesson-12-analyze-in-excel.md)Excel を開いて、ピボット テーブルを自動的に作成します。

9.  **ピボット テーブル フィールド**、追加、**組織**から階層、 **DimEmployee**テーブル**行**、および**ResellerTotalSales**メジャーを**FactResellerSales**テーブル**値**です。

    ![as-lesson-detail-ragged-hierarchies-pivottable](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-pivottable.png)

    わかるように、ピボット テーブルで、階層は不規則である行を表示します。 行が多数ある空のメンバーが表示されます。

## <a name="to-fix-the-ragged-hierarchy-by-setting-the-hide-members-property"></a>非表示にするメンバーのプロパティを設定して、不規則階層を修正するには

1.  **表形式モデル エクスプ ローラー**、展開**テーブル** > **DimEmployee** > **階層** > **組織**です。

2.  **プロパティ** > **メンバーを非表示****空のメンバーを非表示に**です。 

    ![as-lesson-detail-ragged-hierarchies-hidemembers](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-hidemembers.png)

3.  Excel でピボット テーブルを更新します。 

    ![as-lesson-detail-ragged-hierarchies-pivottable-refresh](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-pivottable-refresh.png)

    深めるを検索するようになりました。

## <a name="see-also"></a>参照   
[レッスン 9: 階層の作成](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md)  
[補足のレッスンの動的なセキュリティ](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)  
[補足のレッスンでは、詳細行](../tutorial-tabular-1400/as-supplemental-lesson-detail-rows.md)  
