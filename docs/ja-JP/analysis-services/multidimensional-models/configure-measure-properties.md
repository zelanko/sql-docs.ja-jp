---
title: メジャーのプロパティを構成する |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f853302ed7504d18aae8c962adb3ab3f14730bae
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="configure-measure-properties"></a>メジャーのプロパティの構成
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  メジャーには、メジャーの動作を定義し、メジャーがユーザーに表示される方法を制御できるプロパティがあります。  
  
 キューブまたはメジャーを作成または編集する際、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] でプロパティを設定できます。 また、MDX または AMO を使用してプログラムで設定することもできます。 詳細については、「[多次元モデル内のメジャーおよびメジャー グループの作成](../../analysis-services/multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md)」、「[CREATE MEMBER ステートメント &#40;MDX&#41;](../../mdx/mdx-data-definition-create-member.md)」、または「[AMO OLAP 基本オブジェクトのプログラミング](../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-olap-basic-objects.md)」を参照してください。  
  
## <a name="measure-properties"></a>メジャーのプロパティ  
 プロパティがメジャー レベルで上書きされない限り、メジャーはメンバーになっているメジャー グループから特定のプロパティを継承します。 メジャーのプロパティは、メジャーの集計方法、データ型、表示名、メジャーの表示フォルダー、書式設定文字列、メジャーの式、基になるソース列、およびユーザーに対する表示や非表示を決定します。  
  
|プロパティ|定義|  
|--------------|----------------|  
|**AggregateFunction**|必須。 メジャーの集計方法を決定します。 **Sum** は既定の集計です。 各関数の詳しい説明については、「 [集計関数の使用](../../analysis-services/multidimensional-models/use-aggregate-functions.md) 」を参照してください。|  
|**DataType**|必須。 メジャーのバインド先である、基になるファクト テーブル列のデータ型を指定します。 既定では、この値は基になる列から継承されます。|  
|**Description**|メジャーの説明を指定します。クライアント アプリケーションに表示される場合があります。|  
|**DisplayFolder**|ユーザーがキューブに接続するとメジャーが表示されるフォルダーです。 キューブに多くのメジャーがある場合、表示フォルダーを使用すると、メジャーを分類して表示を見やすく改善できます。|  
|**FormatString**|メジャーの **FormatString** プロパティを使用すると、メジャー値の表示に使用する形式を選択できます。<br /><br /> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]に表示形式の一覧が用意されていますが、一覧にはない追加形式を複数指定できます。 Microsoft Visual Basic で有効な名前付き形式またはユーザー定義形式を指定できます。|  
|**ID**|必須。 メジャーの一意識別子 (ID) です。 このプロパティは読み取り専用です。|  
|**MeasureExpression**|メジャーの値を定義する、制約付きの MDX 式を指定します。 式は、集計前にリーフ レベルで評価され、値の重み付けができるようになります。 たとえば、売上高が為替レートで重み付けされる通貨の換算などです。|  
|**名前**|必須。 メジャーの名前を指定します。|  
|**ソース**|必須。 メジャーがバインドされるデータ ソース ビューの列を指定します。 詳細については、「[データ ソースとバインド &#40;SSAS 多次元&#41;](../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)」を参照してください。|  
|**[表示]**|クライアント アプリケーションでメジャーの表示/非表示を決定します。|  
  
## <a name="see-also"></a>参照  
 [メジャー グループのプロパティを構成します。](../../analysis-services/multidimensional-models/configure-measure-group-properties.md)   
 [メジャーの変更](../../analysis-services/lesson-3-1-modifying-measures.md)  
  
  
