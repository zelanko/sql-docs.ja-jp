---
title: パースペクティブの定義と参照 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 766004b9-6578-4914-a445-6f44843a5fb0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7889bb81d9bb1f1e3fefa229c0a6a0ee0dc1f1dd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "69493770"
---
# <a name="defining-and-browsing-perspectives"></a>パースペクティブの定義と表示
  パースペクティブを使用すれば、特定の目的に従ってキューブの表示を単純化できます。 既定では、ユーザーはアクセスする権限のあるキューブ内のすべての要素を表示できます。 
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] キューブ全体の表示時に表示されるものが、キューブの既定のパースペクティブです。 キューブ全体を表示すると、操作が非常に複雑になる可能性があります。特に、ビジネス インテリジェンスやレポートの要件に応じてキューブのごく一部分しか操作する必要のないユーザーにとっては複雑すぎます。  
  
 キューブの表示上の複雑さを軽減するために、 *パースペクティブ*、つまりキューブの表示可能なサブセットを作成することができます。こうすれば、キューブ内のメジャー グループ、メジャー、ディメンション、属性、階層、主要業績評価指標 (KPI)、アクション、計算されるメンバーのうちの一部分だけがユーザーに表示されます。 これは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]の以前のリリース用に作成されたクライアント アプリケーションを使用する場合は特に有効です。 たとえば、これらのクライアントにはフォルダーやパースペクティブを表示する概念はありませんが、パースペクティブはあたかもキューブであるかのように古いクライアントに表示されます。 詳細については、「 [パースペクティブ](multidimensional-models-olap-logical-cube-objects/perspectives.md)」および「 [多次元モデルのパースペクティブ](multidimensional-models/perspectives-in-multidimensional-models.md)」を参照してください。  
  
> [!NOTE]  
>  パースペクティブはセキュリティ上のメカニズムではなく、ユーザー エクスペリエンスを改善するためのツールです。 パースペクティブのセキュリティはすべて、基になるキューブから継承されます。  
  
 このトピックの作業では、いくつかの異なるパースペクティブを定義した後、それぞれの新しいパースペクティブを使用してキューブを表示します。  
  
## <a name="defining-an-internet-sales-perspective"></a>Internet Sales パースペクティブの定義  
  
1.  
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブのキューブ デザイナーを開いて、 **[パースペクティブ]** タブをクリックします。  
  
     次の図のように、すべてのオブジェクトとその種類が **[パースペクティブ]** ペインに表示されます。  
  
     ![キューブ デザイナーの [パースペクティブ] ペイン](../../2014/tutorials/media/l9-perspectives-1.gif "キューブ デザイナーの [パースペクティブ] ペイン")  
  
2.  
  **[パースペクティブ]** タブのツール バーの **[新しいパースペクティブ]** ボタンをクリックします。  
  
     次の図のように、新しいパースペクティブの既定の名前 " **パースペクティブ** " が **[パースペクティブ名]** 列に表示されます。 各オブジェクトのチェック ボックスはオンになっています。いずれかのオブジェクトのチェック ボックスをオフにするまでは、このキューブの既定のパースペクティブと同じ表示内容になります。  
  
     ![[パースペクティブ名] 列の新しいパースペクティブ](../../2014/tutorials/media/l9-perspectives-2.gif "[パースペクティブ名] 列の新しいパースペクティブ")  
  
3.  パースペクティブ名をに`Internet Sales`変更します。  
  
4.  次の行で、DefaultMeasure を **[Internet Sales-Sales Amount]** に設定します。  
  
     ユーザーがこのパースペクティブを使ってキューブを表示する場合、他のメジャーをユーザーが指定しない限り、このメジャーがユーザーに表示されます。  
  
    > [!NOTE]  
    >  
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブ全体の既定のメジャーは、キューブの **[キューブ構造]** タブのプロパティ ウィンドウでも設定できます。  
  
5.  次のオブジェクトのチェック ボックスをオフにします。  
  
    -   `Reseller Sales`メジャーグループ  
  
    -   **Sales quota**メジャーグループ  
  
    -   **Sales quota 1**メジャーグループ  
  
    -   **再販業者**キューブディメンション  
  
    -   **再販業者の Geography**キューブディメンション  
  
    -   **販売区域**キューブディメンション  
  
    -   **Employee**キューブディメンション  
  
    -   **昇格**キューブディメンション  
  
    -   **再販業者の収益**KPI  
  
    -   **大規模な再販業者**の名前付きセット  
  
    -   計算されるメンバー **Total Sales Amount**  
  
    -   計算されるメンバー **Total Product Cost**  
  
    -   **再販業者の GPM**の計算されるメンバー  
  
    -   **TOTAL GPM**計算されるメンバー  
  
    -   計算されるメンバー**すべてに対する再販業者の売上比率**  
  
    -   計算されるメンバー**すべてに対する総売上比率**  
  
     これらのオブジェクトはインターネット販売とは関係がありません。  
  
    > [!NOTE]  
    >  さらに、ディメンションごとに、パースペクティブに表示するユーザー定義階層と属性を個別に選択できます。  
  
## <a name="defining-a-reseller-sales-perspective"></a>Reseller Sales パースペクティブの定義  
  
1.  
  **[パースペクティブ]** タブのツール バーの **[新しいパースペクティブ]** ボタンをクリックします。  
  
2.  新しいパースペクティブの名前をに`Reseller Sales`変更します。  
  
3.  既定のメジャーとして **[Reseller Sales-Sales Amount]** を設定します。  
  
     ユーザーがこのパースペクティブを使用してキューブを表示するとき、他のメジャーをユーザーが指定しない限り、このメジャーがユーザーに表示されます。  
  
4.  次のオブジェクトのチェック ボックスをオフにします。  
  
    -   `Internet Sales`メジャーグループ  
  
    -   **Internet Sales Reason**メジャーグループ  
  
    -   **Customer**キューブディメンション  
  
    -   **Internet Sales Order Details**キューブディメンション  
  
    -   **Sales Reason**キューブディメンション  
  
    -   **Internet Sales Details ドリルスルーアクション**のドリルスルーアクション  
  
    -   計算されるメンバー **Total Sales Amount**  
  
    -   計算されるメンバー **Total Product Cost**  
  
    -   **インターネット GPM**の計算されるメンバー  
  
    -   **TOTAL GPM**計算されるメンバー  
  
    -   計算されるメンバー**すべてのインターネット販売比率**  
  
    -   計算されるメンバー**すべてに対する総売上比率**  
  
     これらのオブジェクトは再販業者の販売とは関係がありません。  
  
## <a name="defining-a-sales-summary-perspective"></a>Sales Summary パースペクティブの定義  
  
1.  
  **[パースペクティブ]** タブのツール バーの **[新しいパースペクティブ]** ボタンをクリックします。  
  
2.  新しいパースペクティブの名前をに`Sales Summary`変更します。  
  
    > [!NOTE]  
    >  計算されるメジャーを既定のメジャーとして指定することはできません。  
  
3.  次のオブジェクトのチェック ボックスをオフにします。  
  
    -   `Internet Sales`メジャーグループ  
  
    -   `Reseller Sales`メジャーグループ  
  
    -   **Internet Sales Reason**メジャーグループ  
  
    -   **Sales quota**メジャーグループ  
  
    -   **Sales Quotas1**メジャーグループ  
  
    -   **Internet Sales Order Details**キューブディメンション  
  
    -   **Sales Reason**キューブディメンション  
  
    -   **Internet Sales Details ドリルスルーアクション**のドリルスルーアクション  
  
4.  次のオブジェクトのチェック ボックスをオンにします。  
  
    -   **Internet Sales Count**メジャー  
  
    -   **再販業者の販売数**メジャー  
  
## <a name="browsing-the-cube-through-each-perspective"></a>各パースペクティブを使用したキューブの表示  
  
1.  
  **[ビルド]** メニューの **[Analysis Services Tutorial の配置]** をクリックします。  
  
2.  配置が正常に完了したら、 **[ブラウザー]** タブに切り替えて、 **[再接続]** ボタンをクリックします。  
  
3.  Excel を起動します。  
  
4.  次の図のように、Excel の分析機能では、Excel でモデルを参照するときに使用するパースペクティブを選択することができます。  
  
     ![[Internet Sales] パースペクティブのオブジェクト](../../2014/tutorials/media/l9-perspectives-3.gif "[Internet Sales] パースペクティブのオブジェクト")  
  
5.  または、Windows の [スタート] メニューから Excel を起動して、次の図のように、データ接続ウィザードで localhost 上の Analysis Services Tutorial データベースへの接続を定義し、パースペクティブを選択することもできます。  
  
     ![Excel でのデータ接続ウィザード](../../2014/tutorials/media/l9-perspectives-3b.gif "Excel でのデータ接続ウィザード")  
  
6.  [ `Internet Sales` **パースペクティブ**] ボックスの一覧でを選択し、[メタデータ] ペインでメジャーとディメンションを確認します。  
  
     Internet Sales パースペクティブ用に指定されたオブジェクトだけが表示されます。  
  
7.  メタデータ ペインで、 **[Measures]** を展開します。  
  
     メジャーグループのみが表示され、**インターネット GPM**と、計算される**すべての製品の internet Sales 比率**が計算されるメンバーになります。 `Internet Sales`  
  
8.  モデルで再度 Excel を選択します。 [`Sales Summary`] を選択します。  
  
     次の図のように、これらの各メジャー グループには 1 つのメジャーだけが表示されます。  
  
     ![[Internet Sales] および [Reseller Sales] メジャー](../../2014/tutorials/media/l9-perspectives-4.gif "[Internet Sales] および [Reseller Sales] メジャー")  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [翻訳の定義と表示](lesson-9-2-defining-and-browsing-translations.md)  
  
## <a name="see-also"></a>参照  
 [ビジョン](multidimensional-models-olap-logical-cube-objects/perspectives.md)   
 [多次元モデルのパースペクティブ](multidimensional-models/perspectives-in-multidimensional-models.md)  
  
  
