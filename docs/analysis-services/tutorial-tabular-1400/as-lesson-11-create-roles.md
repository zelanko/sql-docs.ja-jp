---
title: 'Analysis Services のチュートリアル レッスン 11: ロールを作成 |Microsoft ドキュメント'
description: Analysis Services tutorial プロジェクトにロールを作成する方法について説明します。
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
ms.workload: na
ms.date: 02/20/2018
ms.author: owend
monikerRange: '>= sql-analysis-services-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 15994491230e1952d699b028c96df5a972698e39
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="create-roles"></a>ロールの作成

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

このレッスンでは、ロールを作成します。 ロールは、ロールのメンバーであるユーザーのみへのアクセスを制限することによって、モデル データベースのオブジェクトとデータのセキュリティを提供します。 各ロールは、1 つの権限 (なし、読み取り、読み取りと実行、実行、または管理者) を使用して定義されます。 ロール マネージャーを使用してモデルを作成中にロールを定義できます。 モデルが配置された後は、SQL Server Management Studio (SSMS) を使用してロールを管理できます。 詳細については、次を参照してください。[ロール](../tabular-models/roles-ssas-tabular.md)です。
  
> [!NOTE]  
> ロールの作成は、このチュートリアルを完了するために必ずしも必要ではありません。 既定では、現在ログインで使用するアカウントは、モデルに対する管理者特権を持ちます。 ただし、他の組織内ユーザーを参照できるレポート作成クライアントを使用してには、読み取りアクセス許可を使って、少なくとも 1 つのロールを作成し、それらのユーザーをメンバーとして追加する必要があります。  
  
3 つのロールを作成します。  
  
-   **販売責任者**– この役割は、すべてのモデル オブジェクトとデータに対する読み取り権限が対象となる、組織内ユーザーを含めることができます。  
  
-   **Sales Analyst US** – この役割は、米国の州の売上に関連するデータを参照できるのみにする、組織内ユーザーを含めることができます。 このロールの定義に DAX 数式を使用する、*行フィルター*、United States に対してのみデータを参照するメンバーを制限します。  
  
-   **管理者**– この役割は、無制限のアクセスと、モデル データベースに対して管理タスクを実行するアクセス許可が管理者権限を付与するユーザーを含めることができます。  
  
組織内の Windows ユーザーおよびグループ アカウントは一意であるため、特定の組織からのアカウントをメンバーに追加できます。 しかし、このチュートリアルでは、メンバーを空白のままにすることもできます。 レッスン 12 で後で各ロールの効果をテストする: Excel で分析します。  
  
このレッスンの推定所要時間: **15 分**  
  
## <a name="prerequisites"></a>前提条件  

この記事は、順番に従って実行する必要がありますが、テーブル モデリング チュートリアルの一部です。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 10: パーティションの作成](../tutorial-tabular-1400/as-lesson-10-create-partitions.md)です。  
  
## <a name="create-roles"></a>ロールの作成  
  
#### <a name="to-create-a-sales-manager-user-role"></a>Sales Manager ユーザー ロールを作成するには  
  
1.  表形式モデル エクスプ ローラーを右クリックして**ロール** > **ロール**です。  
  
2.  ロール マネージャーで、をクリックして**新規**です。  
  
3.  [新しいロール] をクリックし、**名前**列、するロールの名前を変更**営業マネージャー**です。  
  
4.  **[権限]** 列で、ドロップダウン リストをクリックし、 **[読み取り]** 権限を選択します。 

    ![as-lesson11-new-role](../tutorial-tabular-1400/media/as-lesson11-new-role.png) 
  
5.  省略可能: をクリックして、**メンバー**  タブをクリックして**追加**です。 **[ユーザーまたはグループの選択]** ダイアログ ボックスで、ロールに含める組織の Windows ユーザーまたはグループを入力します。  
  
#### <a name="to-create-a-sales-analyst-us-user-role"></a>Sales Analyst US ユーザー ロールを作成するには  
  
1.  ロール マネージャーで、をクリックして**新規**です。    
  
2.  ロールの名前を変更**Sales Analyst US**です。  
  
3.  このロールを付与**読み取り**権限です。  
  
4.  行フィルター タブをクリックし、 **DimGeography**テーブルだけ、DAX フィルター 列で、次の数式を入力します。  
  
    ```Administrator
    =DimGeography[CountryRegionCode] = "US" 
    ```
    
    行フィルター式は、ブール値 (TRUE/FALSE) に解決される必要があります。 この数式では、"US"の Country Region Code の値を持つ行のみをユーザーに表示することを指定します。  
    ![as-lesson11-role-filter](../tutorial-tabular-1400/media/as-lesson11-role-filter.png) 
  
6.  省略可能: をクリックして、**メンバー**  タブをクリックして**追加**です。 **[ユーザーまたはグループの選択]** ダイアログ ボックスで、ロールに含める組織の Windows ユーザーまたはグループを入力します。  
  
#### <a name="to-create-an-administrator-user-role"></a>管理者ユーザー ロールを作成するには  
  
1.  **[新規作成]**をクリックします。  
  
2.  ロールの名前を変更**管理者**です。  
  
3.  このロールを付与**管理者**権限です。  
  
4.  省略可能: をクリックして、**メンバー**  タブをクリックして**追加**です。 **[ユーザーまたはグループの選択]** ダイアログ ボックスで、ロールに含める組織の Windows ユーザーまたはグループを入力します。 
  
  
## <a name="whats-next"></a>次の操作

[レッスン 12: Excel で分析](../tutorial-tabular-1400/as-lesson-12-analyze-in-excel.md)です。

  
  
