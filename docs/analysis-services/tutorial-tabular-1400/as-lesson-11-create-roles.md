---
title: 'Analysis Services チュートリアル-レッスン 11: ロールの作成 |Microsoft Docs'
ms.date: 08/27/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfiles"
ms.openlocfilehash: 90742e38b3948a0fc64df4908d6a0daadf0793e9
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43076973"
---
# <a name="create-roles"></a>ロールの作成

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

このレッスンでは、ロールを作成します。 ロールは、ロールのメンバーであるユーザーのみにアクセスを制限することで、モデル データベース オブジェクトとデータ セキュリティを提供します。 各ロールは、1 つの権限 (なし、読み取り、読み取りと実行、実行、または管理者) を使用して定義されます。 ロール マネージャーを使用してモデルの作成時にロールを定義できます。 モデルを配置すると後、は、SQL Server Management Studio (SSMS) を使用してロールを管理することができます。 詳細についてを参照してください。[ロール](../tabular-models/roles-ssas-tabular.md)します。
  
> [!NOTE]  
> ロールの作成は、このチュートリアルを完了するために必ずしも必要ではありません。 既定では、現在ログインしてアカウントは、モデルに対する管理者特権を持ちます。 ただし、他のユーザー、組織内を参照できるレポート作成クライアントを使用してには、読み取りアクセス許可を使って、少なくとも 1 つのロールを作成し、それらのユーザーをメンバーとして追加する必要があります。  
  
3 つのロールを作成します。  
  
-   **営業マネージャー** – この役割は、すべてのモデル オブジェクトとデータに対する読み取り権限が対象となる組織のユーザーを含めることができます。  
  
-   **Sales Analyst US** – この役割は、米国の州の売上に関連するデータを参照できるのみにする、組織内ユーザーを含めることができます。 そのロールを定義する DAX 数式を使用する、*行フィルター*、米国のみのデータを参照するメンバーを制限します。  
  
-   **管理者**– このロールは管理者権限は、無制限のアクセスや、model データベースに対する管理タスクを実行するアクセス許可を付与するユーザーを含めることができます。  
  
組織内の Windows ユーザーおよびグループ アカウントは一意であるため、特定の組織からのアカウントをメンバーに追加できます。 しかし、このチュートリアルでは、メンバーを空白のままにすることもできます。 レッスン 12 で後で各ロールの効果をテストする: Excel で分析します。  
  
このレッスンの推定所要時間: **15 分**  
  
## <a name="prerequisites"></a>Prerequisites  

この記事では、順序で完了する必要があります、表形式モデルのチュートリアルの一部です。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 10: パーティションの作成](../tutorial-tabular-1400/as-lesson-10-create-partitions.md)です。  
  
## <a name="create-roles"></a>ロールの作成  
  
#### <a name="to-create-a-sales-manager-user-role"></a>Sales Manager ユーザー ロールを作成するには  
  
1.  表形式モデル エクスプ ローラーで右クリック**ロール** > **ロール**します。  
  
2.  ロール マネージャー をクリックして**新規**します。  
  
3.  新しいロールをクリックし、**名前**列にロールの名前を変更**営業マネージャー**。  
  
4.  **[権限]** 列で、ドロップダウン リストをクリックし、 **[読み取り]** 権限を選択します。 

    ![as-lesson11-new-role](../tutorial-tabular-1400/media/as-lesson11-new-role.png) 
  
5.  省略可能: をクリックして、**メンバー**タブをクリックし、をクリックし、**追加**します。 **[ユーザーまたはグループの選択]** ダイアログ ボックスで、ロールに含める組織の Windows ユーザーまたはグループを入力します。  
  
#### <a name="to-create-a-sales-analyst-us-user-role"></a>Sales Analyst US ユーザー ロールを作成するには  
  
1.  ロール マネージャー をクリックして**新規**します。    
  
2.  ロールの名前を変更**Sales Analyst US**します。  
  
3.  このロールを付与**読み取り**権限。  
  
4.  行フィルター タブをクリックし、 **DimGeography**テーブルのみ、DAX フィルター 列で、次の式を入力します。  
  
    ```Administrator
    =DimGeography[CountryRegionCode] = "US" 
    ```
    
    行フィルター式は、ブール値 (TRUE/FALSE) に解決される必要があります。 この数式では、US ｣ の Country Region Code 値を持つ行のみをユーザーに表示することを指定します。  
    ![as-lesson11-role-filter](../tutorial-tabular-1400/media/as-lesson11-role-filter.png) 
  
6.  省略可能: をクリックして、**メンバー**タブをクリックし、をクリックし、**追加**します。 **[ユーザーまたはグループの選択]** ダイアログ ボックスで、ロールに含める組織の Windows ユーザーまたはグループを入力します。  
  
#### <a name="to-create-an-administrator-user-role"></a>管理者ユーザー ロールを作成するには  
  
1.  **[新規]** をクリックします。  
  
2.  ロールの名前を変更**管理者**します。  
  
3.  このロールを付与**管理者**権限。  
  
4.  省略可能: をクリックして、**メンバー**タブをクリックし、をクリックし、**追加**します。 **[ユーザーまたはグループの選択]** ダイアログ ボックスで、ロールに含める組織の Windows ユーザーまたはグループを入力します。 
  
  
## <a name="whats-next"></a>次の操作

[レッスン 12: Excel で分析](../tutorial-tabular-1400/as-lesson-12-analyze-in-excel.md)します。

  
  
