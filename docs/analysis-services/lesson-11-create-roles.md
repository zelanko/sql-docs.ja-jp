---
title: "レッスン 12: ロールの作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/27/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tutorial
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 984face4-00fc-46d3-8ae1-9755bf737bdf
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 659b8bb8af4d759367d81bb3e8828360fd2b1f28
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-11-create-roles"></a>レッスン 11: ロールを作成します。
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

このレッスンでは、ロールを作成します。 ロールを使用すると、ロール メンバーである Windows ユーザーのみにアクセスを制限することで、モデル データベース オブジェクトとデータにセキュリティを提供できます。 各ロールは、1 つの権限 (なし、読み取り、読み取りと実行、実行、または管理者) を使用して定義されます。 ロール マネージャーを使用してモデルを作成中にロールを定義できます。 モデルを配置した後は、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]を使用してロールを管理できます。 詳細については、「 [[ロール]](../analysis-services/tabular-models/roles-ssas-tabular.md)の [ロール マネージャー] ダイアログ ボックスを使用して定義できます。  
  
> [!NOTE]  
> ロールの作成は、このチュートリアルを完了するために必ずしも必要ではありません。 既定では、現在ログインに使用しているアカウントには、モデルに対する管理者特権が付与されています。 ただし、レポート作成クライアントを使用して、モデルの参照に組織内の他のユーザーを許可するには、読み取りアクセス許可を使って、少なくとも 1 つのロールを作成およびメンバーとしてこれらのユーザーを追加する必要があります。  
  
ここでは、次の 3 つのロールを作成します。  
  
-   **販売責任者**– この役割は、すべてのモデル オブジェクトとデータに対する読み取り権限が対象となる、組織内ユーザーを含めることができます。  
  
-   **Sales Analyst US** – この役割は、米国の州の売上に関連するデータを参照できるのみにする、組織内ユーザーを含めることができます。 このロールに対しては、DAX 式を使用して *行フィルター*を定義することにより、メンバーが米国のデータのみを参照できるように制限します。  
  
-   **管理者**– この役割は、無制限のアクセスと、モデル データベースに対して管理タスクを実行するアクセス許可が管理者権限を付与するユーザーを含めることができます。  
  
組織内の Windows ユーザーおよびグループ アカウントは一意であるため、特定の組織からのアカウントをメンバーに追加できます。 しかし、このチュートリアルでは、メンバーを空白のままにすることもできます。 各ロールの影響は、後の「レッスン 12: Excel での分析」でもテストできます。  
  
このレッスンの推定所要時間: **15 分**  
  
## <a name="prerequisites"></a>前提条件  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 10: パーティションの作成](../analysis-services/lesson-10-create-partitions.md)です。  
  
## <a name="create-roles"></a>ロールの作成  
  
#### <a name="to-create-a-sales-manager-user-role"></a>Sales Manager ユーザー ロールを作成するには  
  
1.  表形式モデル エクスプ ローラーを右クリックして**ロール** > **ロール**です。  
  
2.  ロール マネージャーで、をクリックして**新規**です。  
  
3.  [でをクリックし、新しいロールを**名前**] 列にロールの名前**営業マネージャー**です。  
  
4.  **[権限]** 列で、ドロップダウン リストをクリックし、 **[読み取り]** 権限を選択します。 

    ![として表形式の lesson11-新しい-役割](../analysis-services/media/as-tabular-lesson11-new-role.png) 
  
5.  省略可能: をクリックして、**メンバー**  タブをクリックして**追加**です。 **[ユーザーまたはグループの選択]** ダイアログ ボックスで、ロールに含める組織の Windows ユーザーまたはグループを入力します。  
  
#### <a name="to-create-a-sales-analyst-us-user-role"></a>Sales Analyst US ユーザー ロールを作成するには  
  
1.  ロール マネージャーで、をクリックして**新規**です。    
  
2.  ロールの名前を変更**Sales Analyst US**です。  
  
3.  このロールを付与**読み取り**権限です。  
  
4.  クリックし、行フィルター タブでの**DimGeography**テーブルのみに、DAX フィルター 列で、次の数式を入力します。  
  
    ```
    =DimGeography[CountryRegionCode] = "US" 
    ```
    
    行フィルター式は、ブール値 (TRUE/FALSE) に解決される必要があります。 この式では、Country Region Code の値が "US" である行のみがユーザーに表示されるように指定しています。  
    ![として、表形式の lesson11-ロールのフィルター](../analysis-services/media/as-tabular-lesson11-role-filter.png) 
  
6.  (省略可能) **[メンバー]** タブをクリックし、 **[追加]**をクリックします。 **[ユーザーまたはグループの選択]** ダイアログ ボックスで、ロールに含める組織の Windows ユーザーまたはグループを入力します。  
  
#### <a name="to-create-an-administrator-user-role"></a>管理者ユーザー ロールを作成するには  
  
1.  **[新規作成]**をクリックします。  
  
2.  ロールの名前を変更**管理者**です。  
  
3.  このロールを付与**管理者**権限です。  
  
4.  (省略可能) **[メンバー]** タブをクリックし、 **[追加]**をクリックします。 **[ユーザーまたはグループの選択]** ダイアログ ボックスで、ロールに含める組織の Windows ユーザーまたはグループを入力します。 
  
  
## <a name="whats-next"></a>次の操作
次のレッスンに移動:[レッスン 12: Excel で分析](../analysis-services/lesson-12-analyze-in-excel.md)です。

  
  

