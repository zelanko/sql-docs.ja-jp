---
title: 予測関数をモデルに適用する |Microsoft ドキュメント
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: data-mining
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4f1bbde465ec10e9a218ab096ba9b920bd68bdda
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="apply-prediction-functions-to-a-model"></a>モデルへの予測関数の適用
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ マイニングで予測クエリを作成するには、クエリの基になるマイニング モデルを選択する必要があります。 現在のプロジェクトに存在するマイニング モデルを選択できます。  
  
 モデルを選択した後は、クエリに " *予測関数* " を追加します。 予測関数を使用して予測を取得する以外に、予測値の確率や、予測の生成に使用された情報など、関連する統計情報を返す予測関数を追加することもできます。  
  
 予測関数は、次の種類の値を返すことができます。  
  
-   予測可能な属性の名前と、予測された値。  
  
-   予測値の分布と分散に関する統計。  
  
-   指定した結果、またはすべての可能な結果の確率。  
  
-   トップ (最高) またはボトム (最低) のスコアまたは値。  
  
-   指定したノード、オブジェクト、または属性に関連付けられた値。  
  
 使用できる予測関数の種類は、使用しているモデルの種類によって異なります。 たとえば、デシジョン ツリー モデルに適用される予測関数では規則とノードの説明を返すことができ、時系列モデル用の予測関数では時差や時系列に特化した情報を返すことができす。  
  
 ほぼすべてのモデルの種類でサポートされている予測関数の一覧については、「[一般的な予測関数 &#40;DMX&#41;](../../dmx/general-prediction-functions-dmx.md)」を参照してください。  
  
 特定の種類のマイニング モデルに対するクエリの実行方法の例については、「[データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)」のアルゴリズム リファレンス トピックを参照してください。  
  
### <a name="choose-a-mining-model-to-use-for-prediction"></a>予測に使用するマイニング モデルの選択  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でモデルを右クリックし、 **[予測クエリの作成]** を選択します。  
  
     -- または --  
  
     [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で **[マイニング モデル予測]** タブをクリックし、 **[マイニング モデル]** テーブルの  **[モデルの選択]** をクリックします。  
  
2.  **[マイニング モデルの選択]** ダイアログ ボックスでマイニング モデルを選択し、 **[OK]** をクリックします。  
  
     現在の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース内の任意のモデルを選択できます。 別のデータベース内のモデルを使用してクエリを作成するには、そのデータベースのコンテキストで新しいクエリ ウィンドウを開くか、そのモデルを含んでいるソリューション ファイルを開く必要があります。  
  
### <a name="add-prediction-functions-to-a-query"></a>クエリへの予測関数の追加  
  
1.  **[予測クエリ ビルダー]** で、 **[単一クエリ入力]** ダイアログ ボックスで値を指定するか、モデルを外部データ ソースにマップして、予測に使用する入力データを構成します。  
  
     詳細については、「 [予測クエリの入力データの選択およびマップ](../../analysis-services/data-mining/choose-and-map-input-data-for-a-prediction-query.md)」を参照してください。  
  
    > [!WARNING]  
    >  予測を生成するための入力を用意する必要はありません。 入力がない場合は、通常、アルゴリズムがすべての可能な入力を通じて最も可能性の高い予測値を返します。  
  
2.  **[ソース]** 列をクリックし、一覧から値を選択します。  
  
    |||  
    |-|-|  
    |**\<モデル名 >**|このオプションを選択すると、マイニング モデルの値が結果に含められます。 予測可能な列のみを追加できます。<br /><br /> モデルから列を追加すると、返される結果はその列の値の個別でないリストになります。<br /><br /> このオプションで追加する列は、作成される DMX ステートメントの SELECT 部分に含まれます。|  
    |**Prediction Function**|このオプションを選択すると、予測関数の一覧を参照できます。<br /><br /> 選択した値または関数は、作成される DMX ステートメントの SELECT 部分に追加されます。<br /><br /> 予測関数の一覧が、選択したモデルの種類によってフィルター処理や制限を受けることはありません。 そのため、現在のモデルの種類で関数がサポートされていることが確実でない場合は、関数を一覧に追加して、エラーが起きないかどうかを確認します。<br /><br /> $ で始まる一覧の項目 ($AdjustedProbability など) は、関数の **PredictHistogram**を使用した場合の結果である、入れ子になったテーブルの列を表しています。 これらは、入れ子になったテーブルの代わりに単一の列を返すために使用できるショートカットです。|  
    |**カスタム式**|このオプションを選択すると、カスタム式を入力し、結果に別名を割り当てることができます。<br /><br /> カスタム式は、作成される DMX 予測クエリの SELECT 部分に追加されます。<br /><br /> このオプションは、各行で結果のためのテキストを追加して、VB 関数やカスタム ストアド プロシージャを呼び出す場合に便利です。<br /><br /> DMX から VBA および Excel 関数を使用する方法の詳細については、「 [MDX および DAX での VBA 関数](../../mdx/vba-functions-in-mdx-and-dax.md)」を参照してください。|  
  
3.  各関数または式の追加後は、DMX ビューに切り替えて、関数がどのように DMX ステートメント内に追加されたかを確認します。  
  
    > [!WARNING]  
    >  予測クエリ ビルダーでは、 **[結果]** をクリックするまで、DMX は検証されません。 クエリ ビルダーによって生成された式は、有効な DMX でないことがよくあります。 主な原因は、予測可能列に関連付けられていない列の参照や、入れ子になったテーブル内の列の予測 (サブ SELECT ステートメントが必要) です。 この時点で、DMX ビューに切り替えて、ステートメントの編集を続行できます。  
  
### <a name="example-create-a-query-on-a-clustering-model"></a>例: クラスター モデルに対するクエリの作成  
  
1.  このサンプル クエリを作成するために使用できるクラスター モデルがない場合は、 [基本的なデータ マイニング チュートリアル](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)を使用して、モデルの [TM_Clustering] を作成してください。  
  
2.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でモデルの [TM_Clustering] を右クリックし、 **[予測クエリの作成]** を選択します。  
  
3.  **[マイニング モデル]** メニューの **[単一クエリ]** を選択します。  
  
4.  **[単一クエリ入力]** ダイアログ ボックスで、入力として次の値を設定します。  
  
    -   Gender = M  
  
    -   Commute Distance = 5-10 miles  
  
5.  クエリ グリッドの **[ソース]** で TM_Clustering マイニング モデルを選択し、列の [Bike Buyer] を追加します。  
  
6.  **[ソース]** で **[予測関数]** を選択し、関数の **Cluster**を追加します。  
  
7.  **[ソース]** で **[予測関数]** を選択し、関数の **PredictSupport**を追加して、モデル列の [Bike Buyer] を **[条件と引数]** ボックスにドラッグします。 **[別名]** 列に「 **Support** 」と入力します。  
  
     予測関数を表す式および列参照を **[条件と引数]** ボックスからコピーします。  
  
8.  **[ソース]** で **[カスタム式]** を選択し、別名を入力してから、次の構文を使用して Excel の CEILING 関数を参照します。  
  
    ```  
    Excel![CEILING](<arguments) as <return type>  
    ```  
  
     関数の引数として列参照を貼り付けます。  
  
     たとえば、次の式ではサポート値の CEILING が返されます。  
  
    ```  
    EXCEL!CEILING(PredictSupport([TM_Clustering].[Bike Buyer]),2)  
    ```  
  
     **[別名]** 列に「CEILING」と入力します。  
  
9. **[クエリ テキスト ビューに切り替え]** をクリックして、生成された DMX ステートメントを確認してから、 **[クエリ結果ビューに切り替え]** をクリックして、予測クエリによって出力された列を表示します。  
  
     予想される結果を次の表に示します。  
  
    |Bike Buyer|$Cluster|[別名]|CEILING|  
    |----------------|--------------|-------------|-------------|  
    |0|Cluster 8|954|953.948638926372|  
  
 他の句 (たとえば WHERE 句) をステートメントのどこかに追加する場合、グリッドを使用して追加することはできません。まず、DMX ビューに切り替える必要があります。  
  
## <a name="see-also"></a>参照  
 [データ マイニング クエリ](../../analysis-services/data-mining/data-mining-queries.md)  
  
  
