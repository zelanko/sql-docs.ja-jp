---
title: "親子階層で親属性プロパティの定義 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 2d78fa73-a13b-4e12-bbd0-43e5307f760c
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: a7430bd3692788b8977d4c1849a599ada77dfc59
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="lesson-4-2---defining-parent-attribute-properties-in-a-parent-child-hierarchy"></a>レッスン 4 2: 親子階層の親属性プロパティを定義します。
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

親子階層とは、2 つのテーブル列に基づいたディメンション内の階層です。 この 2 つのテーブル列により、ディメンションのメンバー間の階層リレーションシップが定義されます。 一方の列は *メンバー キー列*と呼ばれ、各ディメンション メンバーを識別します。 もう一方の列は *親列*と呼ばれ、各ディメンション メンバーの親を識別します。 親属性の **NamingTemplate** プロパティは、親子階層の各レベルの名前を指定します。 **MembersWithData** プロパティは、親メンバーのデータを表示するかどうかを指定します。  
  
詳細については、「 [親子ディメンション](../analysis-services/multidimensional-models/parent-child-dimension.md), [親子階層の属性](../analysis-services/multidimensional-models/parent-child-dimension-attributes.md)」を参照してください。  
  
> [!NOTE]  
> ディメンション ウィザードを使用してディメンションを作成すると、親子リレーションシップを持つテーブルがウィザードによって認識され、親子階層が自動的に定義されます。  
  
このトピックの実習では、名前付けテンプレートを使用して、 **Employee** ディメンションの親子階層の各レベルに名前を付けます。 次に、すべての親データが非表示になるように親属性を構成します。これにより、リーフレベルのメンバーの売上高のみが表示されるようになります。  
  
## <a name="browsing-the-employee-dimension"></a>Employee ディメンションの表示  
  
1.  ソリューション エクスプローラーで、 **[ディメンション]** フォルダーの **Employee.dim** をダブルクリックし、Employee ディメンションのディメンション デザイナーを開きます。  
  
2.  **[ブラウザー]** タブをクリックし、 **[階層]** ボックスの一覧で **[Employees]** が選択されていることを確認します。次に、 **[All Employees]** メンバーを展開します。  
  
    この親子階層では、 **Ken J. Sánchez** が最上位の管理者です。  
  
3.  **[Ken J. Sánchez]** メンバーをクリックします。  
  
    このメンバーのレベル名は **Level 02**です。 (レベル名の後ろ**現在のレベル:**すぐ上に、**すべての従業員**メンバーです)。次の実習では、さらにわかりやすい名前を各レベルに定義します。  
  
4.  **[Ken J. Sánchez]** を展開し、この管理者の監督下にある従業員の名前を表示します。次に、 **[Brian S. Welcker]** をクリックし、このレベルの名前を表示します。  
  
    このメンバーのレベル名は **Level 03**です。  
  
5.  ソリューション エクスプローラーで、 **[キューブ]** フォルダー内の **Analysis Services Tutorial.cube** をダブルクリックして、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブのキューブ デザイナーを開きます。  
  
6.  **[ブラウザー]** タブをクリックします。  
  
7.  Excel アイコンをクリックし、接続の有効化を確認するメッセージが表示されたら **[有効化]** をクリックします。  
  
8.  ピボットテーブルのフィールド リストで **Reseller Sales**を展開します。 **Reseller Sales-Sales Amount** を値領域にドラッグします。  
  
9. ピボットテーブルのフィールド リストで **Employee**を展開し、 **Employees** 階層を **行** 領域にドラッグします。  
  
    Employees 階層のすべてのメンバーがピボットテーブル レポートの列 A に追加されます。  
  
    次の図は、展開された Employees 階層を示しています。  
  
10. ![Employees 階層を示すピボット テーブル](../analysis-services/media/l4-employee-1.gif "Employees 階層を示すピボット テーブル")  
  
    Level 03 の各管理者の売上は Level 04 にも表示されます。 各管理者は、他の管理者の部下でもあるからです。 次の実習では、これらの売上高を非表示にします。  
  
## <a name="modifying-parent-attribute-properties-in-the-employee-dimension"></a>Employee ディメンションの親属性プロパティの変更  
  
1.  **Employee** ディメンションのディメンション デザイナーに切り替えます。  
  
2.  **[ディメンション構造]** タブをクリックし、 **[属性]** ペインで **[Employees]** 属性階層をクリックします。  
  
    この属性だけ、他とは異なるアイコンが表示されています。 このアイコンは、Employees 属性が親子階層の親キーであることを示しています。 また、[プロパティ] ウィンドウを見ると、この属性の **Usage** プロパティが **Parent**として定義されていることがわかります。 このプロパティは、ディメンションを設計した際にディメンション ウィザードによって設定されたものです。 親子リレーションシップは、ウィザードによって自動的に検出されています。  
  
3.  [プロパティ] ウィンドウで、**NamingTemplate**プロパティ セルの参照ボタン ( **[...]** ) をクリックします。  
  
    **[レベル名前付けテンプレート]** ダイアログ ボックスでレベル名前付けテンプレートを定義します。このテンプレートは、キューブを表示するときに表示される親子階層のレベル名を決定します。  
  
4.  2 番目の行、  **\*** 行に、入力**Employee Level \*** で、**名前**列、3 番目の行をクリックします。  
  
    **[結果]** の下を確認すると、各レベルには、"Employee Level" の後ろに連番を追加した名前が付いています。  
  
    次の図は、 **[レベル名前付けテンプレート]** ダイアログ ボックスで定義を変更するようすを示しています。  
  
    ![レベル名前付けテンプレート ダイアログ ボックス](../analysis-services/media/l4-namingtemplate.gif "レベル名前付けテンプレート ダイアログ ボックス")  
  
5.  **[OK]**をクリックします。  
  
6.  **Employees** 属性の[プロパティ] ウィンドウの **MembersWithData** プロパティ セルで、 **[NonLeafDataHidden]** を選択して **Employees** 属性の値を変更します。  
  
    この操作により、親子階層内の非リーフレベル メンバーに関連付けられているデータが非表示になります。  
  
## <a name="browsing-the-employee-dimension-with-the-modified-attributes"></a>属性を変更した Employee ディメンションの表示  
  
1.  **で、** [ビルド] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]メニューの **[Analysis Services Tutorial の配置]**をクリックします。  
  
2.  チュートリアルが正常に配置されたら、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブのキューブ デザイナーに切り替え、 **[ブラウザー]** タブのツール バーで **[再接続]** をクリックします。  
  
3.  Excel アイコンをクリックし、 **[有効化]**をクリックします。  
  
4.  **Reseller Sales-Sales Amount** を値領域にドラッグします。  
  
5.  **Employees** 階層を行ラベル領域にドラッグします。  
  
    次の図は、Employees 階層を変更したようすを示しています。 Stephen Y. Jiang は、本人自身の部下として表示されなくなっています。  
  
    ![Employees 階層を変更](../analysis-services/media/l4-employee-2.png "変更 Employees 階層")  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[属性メンバーの自動的なグループ化](../analysis-services/lesson-4-3-automatically-grouping-attribute-members.md)  
  
## <a name="see-also"></a>参照  
[親子ディメンション](../analysis-services/multidimensional-models/parent-child-dimension.md)  
[親子階層の属性](../analysis-services/multidimensional-models/parent-child-dimension-attributes.md)  
  
  
  
