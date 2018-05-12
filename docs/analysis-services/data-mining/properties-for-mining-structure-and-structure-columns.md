---
title: マイニング構造列および構造列のプロパティ |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 72f89879ac7b50f35af283e13b25fb8c8b439b2d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="properties-for-mining-structure-and-structure-columns"></a>マイニング構造と構造列のプロパティ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  データ マイニング デザイナーの **[マイニング構造]** タブを使用すると、マイニング構造のプロパティと、そのマイニング構造に関連付けられた列および入れ子になったテーブルのプロパティを設定または変更できます。 このタブで設定したプロパティは、その構造に関連付けられている各マイニング モデルに反映されます。  
  
> [!NOTE]  
>  マイニング構造のプロパティ値を変更した場合は、変更したのが名前や説明などのメタデータであっても、モデルの表示またはクエリを実行する前に、マイニング構造とそのモデルを再処理する必要があります。  
  
## <a name="properties-of-mining-structures-and-mining-structure-columns"></a>マイニング構造とマイニング構造列のプロパティ  
 次の表では、マイニング構造とマイニング構造列に対して **[マイニング構造]** タブで表示または構成できる、データ マイニング固有のプロパティについて説明します。これらのプロパティを表示または構成するには、ツリー ビュー内のアイテムを右クリックし、 **[プロパティ]** をクリックします。  
  
-   構造のプロパティを表示するには、マイニング構造の見出しをクリックします。  
  
-   列または入れ子になったテーブルのプロパティを表示するには、列名をクリックします。  
  
### <a name="properties-of-the-mining-structure"></a>マイニング構造のプロパティ  
  
|プロパティ|Description|  
|--------------|-----------------|  
|**CacheMode**|トレーニングに使用したケースを、トレーニングの完了後にキャッシュするか破棄するかを指定します。 **注:**  ドリルスルーおよび提示データを有効にするには、このプロパティを **KeepTrainingCases** に設定する必要があります。|  
|**[照合順序]**|列の既定の照合順序を指定します。 照合順序を指定しない場合は、サーバーの照合順序が使用されます。|  
|**Description**|マイニング構造について説明します。 構造のデータの目的と構成について説明することをお勧めします。|  
|**ErrorConfiguration (既定)**|特別なエラー処理が行われる場合のオプションを指定します。|  
|**HoldoutMaxCases**|テスト データセットとして予約できる構造ケースの最大数を指定します。  **HoldoutMaxCases** と **HoldoutPercent**の両方に値を指定すると、それらの条件が結合されます。 **注:**  このプロパティを設定するには、 <xref:Microsoft.AnalysisServices.MiningStructure.CacheMode%2A> を **KeepTrainingCases**をクリックします。|  
|**HoldoutPercent**|テスト データセットとして予約する構造ケースの割合を指定します。 **HoldoutMaxCases** と **HoldoutPercent**の両方に値を指定すると、それらの条件が結合されます。 **注:**  このプロパティを設定するには、 <xref:Microsoft.AnalysisServices.MiningStructure.CacheMode%2A> を **KeepTrainingCases**をクリックします。|  
|**HoldoutSeed**|提示されたテスト セットのパーティション分割を初期化するシードを指定して、テスト データセットを確実に再作成できるようにします。 **注:**  このプロパティを設定するには、 <xref:Microsoft.AnalysisServices.MiningStructure.CacheMode%2A> を **KeepTrainingCases**をクリックします。|  
|**ID**|マイニング構造の一意識別子を表示します。<br /><br /> マイニング構造の作成時に構造に割り当てた名前が、ID として使用されます。 その後 **Name** プロパティに新しい値を入力して名前を変更した場合、新しい名前は別名としてのみ使用され、ID は変化しません。|  
|**言語**|マイニング構造内のキャプションの言語を指定します。|  
|**名前**|マイニング構造の名前または別名を指定します。<br /><br /> Name プロパティの値を変更した場合、新しい名前はキャプションまたは別名としてのみ使用されます。マイニング構造の識別子は変化しません。|  
|**ソース**|データ ソースの名前と種類を表示します。|  
  
### <a name="properties-of-the-mining-structure-columns"></a>マイニング構造列のプロパティ  
  
|プロパティ|Description|  
|--------------|-----------------|  
|**ClassifiedColumns**|分類列が示す列を指定します。|  
|**コンテンツ**|列のコンテンツの種類です。|  
|**Description**|列を説明します。 列の説明では、列データの派生方法やデータ マイニング用の変更について情報を提供することをお勧めします。|  
|**DiscretizationBucketCount**|離散化列のバケットの数を表示します。<br /><br /> コンテンツの種類が **Discretized**に設定されている場合にのみ有効です。<br /><br /> このプロパティは読み取り専用です。|  
|**DiscretizationMethod**|列の離散化に使用されたメソッドを表示します。<br /><br /> コンテンツの種類が **Discretized**に設定されている場合にのみ有効です。<br /><br /> このプロパティは読み取り専用です。|  
|**Distribution**|列のコンテンツの分布を指定します。|  
|**ID**|列の識別子を表示します。<br /><br /> 列の Name プロパティの値を変更しても、ID プロパティの値には影響を与えません。|  
|**IsKey**|列がキー列であるかどうかを示します。|  
|**[KeyColumns]**|キーであるか、属性のキーの一部である列の定義を含みます。|  
|**ModelingFlags**|アルゴリズムによって使用可能になる追加のパラメーターを設定します。|  
|**名前**|列の名前です。|  
|**NameColumn**|親要素の名前を指定する列を示します。|  
|**ソース**|列のソースを表示します。<br /><br /> リレーショナル データ ソースの場合、値は常に **(なし)** です。<br /><br /> OLAP キューブに基づく構造の場合、値は、入れ子になったテーブルのソースとして使用するスライスを定義する MDX ステートメントです。|  
|**SourceMeasureGroup**|メジャー グループのソースを表示します。<br /><br /> リレーショナル データ ソースの場合、値は常に **(なし)** です。<br /><br /> OLAP キューブに基づく構造の場合、値は、入れ子になったテーブルのソースとして使用するスライスを定義する MDX ステートメントです。|  
|**型**|列のコンテンツのデータ型です。|  
  
 プロパティの設定または変更の詳細については、「 [マイニング構造のタスクと操作方法](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [リレーショナル マイニング構造の作成](../../analysis-services/data-mining/create-a-relational-mining-structure.md)   
 [マイニング構造列](../../analysis-services/data-mining/mining-structure-columns.md)  
  
  
