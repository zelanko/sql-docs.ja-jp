---
title: "マイニング構造列および構造列のプロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mining structures [Analysis Services], column properties
- data mining [Analysis Services], properties
- columns [data mining], properties
- properties [data mining]
ms.assetid: ce90f684-bb8c-4eca-b9e6-000794dbee16
caps.latest.revision: "23"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 42ee21307542c7e204ac7b4616714c2285cce032
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="properties-for-mining-structure-and-structure-columns"></a>マイニング構造と構造列のプロパティ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]設定またはを使用して、マイニング構造とその関連付けられた列および入れ子になったテーブルのプロパティを変更することができます、**マイニング構造**データ マイニング デザイナーのタブです。 このタブで設定したプロパティは、その構造に関連付けられている各マイニング モデルに反映されます。  
  
> [!NOTE]  
>  マイニング構造のプロパティ値を変更した場合は、変更したのが名前や説明などのメタデータであっても、モデルの表示またはクエリを実行する前に、マイニング構造とそのモデルを再処理する必要があります。  
  
## <a name="properties-of-mining-structures-and-mining-structure-columns"></a>マイニング構造とマイニング構造列のプロパティ  
 次の表では、マイニング構造とマイニング構造列に対して **[マイニング構造]** タブで表示または構成できる、データ マイニング固有のプロパティについて説明します。これらのプロパティを表示または構成するには、ツリー ビュー内のアイテムを右クリックし、 **[プロパティ]**をクリックします。  
  
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
|**Name**|マイニング構造の名前または別名を指定します。<br /><br /> Name プロパティの値を変更した場合、新しい名前はキャプションまたは別名としてのみ使用されます。マイニング構造の識別子は変化しません。|  
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
|**Name**|列の名前です。|  
|**NameColumn**|親要素の名前を指定する列を示します。|  
|**ソース**|列のソースを表示します。<br /><br /> リレーショナル データ ソースの場合、値は常に **(なし)**です。<br /><br /> OLAP キューブに基づく構造の場合、値は、入れ子になったテーブルのソースとして使用するスライスを定義する MDX ステートメントです。|  
|**SourceMeasureGroup**|メジャー グループのソースを表示します。<br /><br /> リレーショナル データ ソースの場合、値は常に **(なし)**です。<br /><br /> OLAP キューブに基づく構造の場合、値は、入れ子になったテーブルのソースとして使用するスライスを定義する MDX ステートメントです。|  
|**型**|列のコンテンツのデータ型です。|  
  
 プロパティの設定または変更の詳細については、「 [マイニング構造のタスクと操作方法](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [リレーショナル マイニング構造の作成](../../analysis-services/data-mining/create-a-relational-mining-structure.md)   
 [マイニング構造列](../../analysis-services/data-mining/mining-structure-columns.md)  
  
  
