---
title: 絞り込みメールマイニングモデル構造の作成 (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a9c67f29-0c47-4a5a-862b-db0f5213c2c9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2bd2e9d0decc730a59b63ee600bec2d080cc85fb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62856163"
---
# <a name="creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial"></a>絞り込みメール配信マイニング モデル構造の作成 (基本的なデータ マイニング チュートリアル)
  絞り込みメール配信シナリオを作成するには、まず、[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] のデータ マイニング ウィザードを使用して、新しいマイニング構造とデシジョン ツリー マイニング モデルを作成します。  
  
 このタスクでは、新しいマイニング構造を設定し、 [!INCLUDE[msCoName](../includes/msconame-md.md)]デシジョンツリーアルゴリズムに基づいて初期マイニングモデルを追加します。 マイニング構造を作成するには、まずテーブルとビューを選択し、トレーニングに使用する列とテストに使用する列を特定します。  
  
### <a name="to-create-a-mining-structure-for-the-targeted-mailing-scenario"></a>絞り込みメール配信シナリオ用のマイニング構造を作成するには  
  
1.  ソリューションエクスプローラーで、[**マイニング構造**] を右クリックし、[**新しいマイニング構造**] をクリックして、データマイニングウィザードを起動します。  
  
2.  **[データ マイニング ウィザードへようこそ]** ページで **[次へ]** をクリックします。  
  
3.  [**定義方法の選択**] ページで、[**既存のリレーショナルデータベースまたはデータウェアハウスから**] が選択されていることを確認し、[**次へ**] をクリックします。  
  
4.  [**データマイニング構造の作成**] ページの [**使用するデータマイニング技法を指定**してください] で、[ **Microsoft デシジョンツリー**] を選択します。  
  
    > [!NOTE]  
    >  データ マイニング アルゴリズムが見つからないという警告が発生する場合は、プロジェクトのプロパティが適切に構成されていない可能性があります。 この警告は、プロジェクトが [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーからデータ マイニング アルゴリズムの一覧を取得しようとして、サーバーが見つからない場合に発生します。 既定では[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 、は**localhost**をサーバーとして使用します。 別のインスタンスまたは名前付きインスタンスを使用している場合は、プロジェクトのプロパティを変更する必要があります。 詳細については、「[基本的なデータマイニングチュートリアル&#41;&#40;Analysis Services プロジェクトの作成](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md)」を参照してください。  
  
5.  **[次へ]** をクリックします。  
  
6.  [**データソースビューの選択**] ページの [**使用できるデータソースビュー** ] ペインで、[**対象メーリング**] を選択します。 [**参照**] をクリックしてデータソースビュー内のテーブルを表示し、[**閉じる**] をクリックしてウィザードに戻ります。  
  
7.  **[次へ]** をクリックします。  
  
8.  [**テーブルの種類の指定**] ページで、[vTargetMail] の [**ケース**] 列のチェックボックスをオンにして、ケーステーブルとして使用し、[**次へ**] をクリックします。 ProspectiveBuyer テーブルは後でテストに使用するので、ここでは無視します。  
  
9. [**トレーニングデータの指定**] ページで、少なくとも1つの予測可能列、1つのキー列、およびモデルの1つの入力列を指定します。 [ **Bikebuyer** ] 行の [**予測可能**] 列のチェックボックスをオンにします。  
  
    > [!NOTE]  
    >  ウィンドウの下部に表示される警告に注意してください。 少なくとも1つの**入力**と1つの**予測可能**列を選択するまで、次のページに移動することはできません。  
  
10. [**提案**] をクリックして [**関連列の提示**] ダイアログボックスを開きます。  
  
     少なくとも1つの予測可能な属性が選択されている場合は、[**提案**] ボタンが有効になります。 [**関連列の提示**] ダイアログボックスには、予測可能列に最も密接に関連する列が一覧表示され、予測可能な属性との相関関係によって属性が並べ替えられます。 相関性の高い列 (信頼スコアが 95% を超えている場合) は、モデルに追加する対象として自動的に選択されます。  
  
     提案を確認し、[**キャンセル**] をクリックして提案を無視します。  
  
    > [!NOTE]  
    >  [ **OK**] をクリックすると、一覧表示されたすべての候補がウィザードの入力列としてマークされます。 提示内容の一部のみを使用する場合、値を手動で変更する必要があります。  
  
11. [**キー** ] 列のチェックボックスが [**顧客キー** ] 行で選択されていることを確認します。  
  
    > [!NOTE]  
    >  データ ソース ビューのソース テーブルにキーが表示されていれば、その列がモデルのキーとして自動的に選択されます。  
  
12. 次の行の [**入力**] 列のチェックボックスをオンにします。 複数の列をオンにするには、セルの範囲を強調表示し、&lt;localizedText&gt;Ctrl&lt;/localizedText&gt; キーを押しながらチェック ボックスをオンにします。  
  
    -   **変更**  
  
    -   **CommuteDistance**  
  
    -   **EnglishEducation**  
  
    -   **EnglishOccupation**  
  
    -   **性別**  
  
    -   **GeographyKey**  
  
    -   **HouseOwnerFlag**  
  
    -   **MaritalStatus**  
  
    -   **NumberCarsOwned**  
  
    -   **NumberChildrenAtHome**  
  
    -   **リージョン**  
  
    -   **TotalChildren**  
  
    -   **YearlyIncome**  
  
13. ページの左端の列で、次の行のチェック ボックスをオンにします。  
  
    -   **AddressLine1**  
  
    -   **AddressLine2**  
  
    -   **DateFirstPurchase**  
  
    -   **EmailAddress**  
  
    -   **FirstName**  
  
    -   **タイトル**  
  
     上記の行の左の列のみがオンになっていることを確認します。 これらの列は構造に追加されますが、モデルには追加されません。 ただし、モデル作成後は、ドリルスルーやテストに使用できるようになります。 ドリルスルーの詳細については、「[データマイニング &#40;のドリルスルークエリ](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)」を参照してください&#41;  
  
14. **[次へ]** をクリックします。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [データ型とコンテンツの種類の指定 &#40;基本的なデータマイニングチュートリアル&#41;](../../2014/tutorials/specifying-the-data-type-and-content-type-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [データマイニングウィザード &#40;テーブルの種類の指定&#41;](../../2014/analysis-services/specify-table-types-data-mining-wizard.md)   
 [データマイニングデザイナー](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Microsoft デシジョンツリーアルゴリズム](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)  
  
  
