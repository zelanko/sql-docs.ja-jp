---
title: Analysis Services チュートリアル補足のレッスン:不規則階層 |Microsoft Docs
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 39f8bcc63b7e5344f70a6d4a3b6c44ae3e69e108
ms.sourcegitcommit: 0a7beb2f51e48889b4a85f7c896fb650b208eb36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57685399"
---
# <a name="supplemental-lesson---ragged-hierarchies"></a>補足のレッスン: 不規則階層

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

この補足のレッスンでは、さまざまなレベルで空白の値 (メンバー) を含む階層でピボットするときに、一般的な問題を解決します。 たとえば、上級管理者が各部門のマネージャーと直属の部下として管理者以外の両方を持つ組織。 または、地理的階層は、国-リージョン-市、都市もありますが、親の州または県などワシントン d.c.、バチカン市がないので構成されています。 階層では、空のメンバーには、さまざまな、または幅合わせしない、レベルに多くの場合、至ります。

![as-lesson-detail-ragged-hierarchies-table](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-table.png)

互換性レベル 1400 の表形式モデルがある追加**メンバーを隠す**階層のプロパティ。 **既定**設定では、任意のレベルで空白のメンバーが存在しない前提としています。 **空のメンバーを非表示に**設定は、ピボット テーブル レポートやレポートに追加されたときに、階層から空のメンバーを除外します。  
  
このレッスンを完了するまでに時間を推定するには。**20 分**  
  
## <a name="prerequisites"></a>前提条件  
この補足のレッスンの記事では、表形式モデルのチュートリアルの一部です。 この補足のレッスンの実習を行う前に作成した前のレッスンをすべて完了した Adventure Works Internet Sales サンプル モデル プロジェクトがあるか。 

を、チュートリアルの一環として AW Internet Sales プロジェクトを作成した場合、モデルにはまだが含まれていないデータや不規則な階層。 この補足のレッスンを完了するには、まず、いくつかのテーブルを追加することで、問題の作成、リレーションシップ、計算列、メジャー、および新しい組織階層を作成する必要があります。 その一部は、約 15 分かかります。 それから、ほんの数分でそれを解決します。  

## <a name="add-tables-and-objects"></a>テーブルとオブジェクトを追加します。
  
### <a name="to-add-new-tables-to-your-model"></a>新しいテーブルをモデルに追加するには
  
1.  表形式モデル エクスプ ローラーで**データソース**、し、接続を右クリックして >**新しいテーブルのインポート**します。
  
2.  ナビゲーターで、次のように選択します。 **DimEmployee**と**FactResellerSales**、順にクリックします**OK**します。

3.  クエリ エディターで、クリックして**インポート**

4.  次の作成[リレーションシップ](../tutorial-tabular-1400/as-lesson-4-create-relationships.md):

    | 表 1           | [列]       | フィルターの方向   | 表 2     | [列]      | Active |
    |-------------------|--------------|--------------------|-------------|-------------|--------|
    | FactResellerSales | OrderDateKey | 既定            | DimDate     | date        | はい    |
    | FactResellerSales | DueDate      | 既定            | DimDate     | date        | いいえ     |
    | FactResellerSales | ShipDateKey  | 既定            | DimDate     | date        | いいえ     |
    | FactResellerSales | ProductKey   | 既定            | DimProduct  | ProductKey  | はい    |
    | FactResellerSales | EmployeeKey  | 両方のテーブルに | DimEmployee | EmployeeKey | はい    |

5. **DimEmployee**テーブルで、次の作成、[計算列](../tutorial-tabular-1400/as-lesson-5-create-calculated-columns.md): 

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

    **レベル 3** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],3,1)) 
    ```

    **Level4 です。** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],4,1)) 
    ```

    **Level5** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],5,1)) 
    ```

6.  **DimEmployee**テーブルで、作成、[階層](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md)という**組織**します。 次の列を順番に追加します。**Level1**、 **Level2**、 **Level3**、 **Level4**、 **Level5**します。

7.  **FactResellerSales**テーブルで、次の作成、[メジャー](../tutorial-tabular-1400/as-lesson-6-create-measures.md):

    ```
    ResellerTotalSales:=SUM([SalesAmount])
    ```

8.  使用[Excel で分析](../tutorial-tabular-1400/as-lesson-12-analyze-in-excel.md)Excel を開いて、ピボット テーブルを自動的に作成します。

9.  **ピボット テーブル フィールド**、追加、**組織**階層から、 **DimEmployee**テーブル**行**、および**ResellerTotalSales**メジャーを**FactResellerSales**テーブル**値**します。

    ![as-lesson-detail-ragged-hierarchies-pivottable](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-pivottable.png)

    ピボット テーブルでは、ご覧のとおり、階層は不規則な行が表示されます。 行が多数ある空のメンバーが表示されます。

## <a name="to-fix-the-ragged-hierarchy-by-setting-the-hide-members-property"></a>メンバーを隠す プロパティを設定して不規則階層を修正するには

1.  **Tabular Model Explorer**、展開**テーブル** > **DimEmployee** > **階層** > **組織**します。

2.  **プロパティ** > **メンバーを隠す**を選択します**空のメンバーを非表示に**します。 

    ![as-lesson-detail-ragged-hierarchies-hidemembers](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-hidemembers.png)

3.  Excel に戻って、ピボット テーブルを更新します。 

    ![as-lesson-detail-ragged-hierarchies-pivottable-refresh](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-pivottable-refresh.png)

    大幅に改善を検索するようになりました。

## <a name="see-also"></a>参照   
[レッスン 9:階層を作成します。](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md)  
[補足のレッスン - 動的なセキュリティ](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)  
[補足のレッスン - 詳細行](../tutorial-tabular-1400/as-supplemental-lesson-detail-rows.md)  
