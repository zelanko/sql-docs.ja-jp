---
title: 名前付きセットを作成 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 52248437e6de4039fd0b2d7d3cc7bec42686a312
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="create-named-sets"></a>名前付きセットの作成
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  名前付きセットはディメンション メンバーのセットまたはセット式で、たとえば多次元式 (MDX) のクエリなどで再利用するために作成されます。 名前付きセットは、キューブ データ、算術演算子、数値、および関数を組み合わせることによって作成できます。 たとえば、Top Ten Factories という名前付きセットを作成して、その中に Factories ディメンションのメンバーのうち Production メジャーの最高値を持つものを上から 10 個含めることができます。 この結果、エンド ユーザーがクエリで Top Ten Factories を使用できるようになります。 たとえば、エンド ユーザーは Top Ten Factories を 1 つの軸に配置し、Production などの Measures ディメンションを別の軸に配置できます。 詳細については、「[多次元モデルの計算](../../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md)」および「[MDX での名前付きセットの作成 (MDX)](../../analysis-services/multidimensional-models/mdx/mdx-named-sets-building-named-sets.md)」を参照してください。  
  
 名前付きセットを作成するには、キューブ デザイナーの **[計算]** タブで **[新しい名前付きセット]** コマンドを使用します。 このコマンドは、 **[計算]** タブのツール バー上にある **[キューブ]** メニューから起動できます。 このコマンドでは、名前付きセットの次のオプションを指定するためのフォームが表示されます。  
  
 **名前**  
 名前付きセットの名前を選択します。 この名前は、エンド ユーザーがキューブを参照したときに表示されます。  
  
 **式**  
 名前付きセットを作成する式を指定します。 この式は、MDX で記述することもできます。 式には、次の要素を含めることができます。  
  
-   ディメンション、レベル、メジャーなど、キューブのコンポーネントを表すデータ式  
  
-   算術演算子  
  
-   数値  
  
-   関数  
  
 キューブ コンポーネントは、 **[計算ツール]** ペインの **[メタデータ]** タブから **名前付きセット フォーム エディター** ペインの **[式]** ボックスにコピーまたはドラッグできます。 関数は、 **[計算ツール]** ペインの **[関数]** タブから **名前付きセット フォーム エディター** ペインの **[式]** ボックスにコピーまたはドラッグできます。  
  
> [!IMPORTANT]  
>  セット内のメンバーを明示的に指定することによって、セット式を作成する場合は、中かっこのペアでメンバーの一覧を囲みます ({})。  
  
## <a name="see-also"></a>参照  
 [多次元モデルでの計算](../../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md)  
  
  
