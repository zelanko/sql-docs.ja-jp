---
title: 名前付きセットを作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- calculations [Analysis Services], named sets
- named sets [Analysis Services]
- members [Analysis Services], named sets
ms.assetid: 03cf97a4-1a18-45f3-acb0-35123bd619be
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: bf758860212adbd100a8385802d769f031b2bf64
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084433"
---
# <a name="create-named-sets"></a>名前付きセットの作成
  名前付きセットはディメンション メンバーのセットまたはセット式で、たとえば多次元式 (MDX) のクエリなどで再利用するために作成されます。 名前付きセットは、キューブ データ、算術演算子、数値、および関数を組み合わせることによって作成できます。 たとえば、Top Ten Factories という名前付きセットを作成して、その中に Factories ディメンションのメンバーのうち Production メジャーの最高値を持つものを上から 10 個含めることができます。 この結果、エンド ユーザーがクエリで Top Ten Factories を使用できるようになります。 たとえば、エンド ユーザーは Top Ten Factories を 1 つの軸に配置し、Production などの Measures ディメンションを別の軸に配置できます。 詳細については、「[多次元モデルの計算](calculations-in-multidimensional-models.md)」および「[MDX での名前付きセットの作成 (MDX)](mdx/mdx-named-sets-building-named-sets.md)」を参照してください。  
  
 名前付きセットを作成するには、キューブ デザイナーの **[計算]** タブで **[新しい名前付きセット]** コマンドを使用します。 このコマンドは、 **[計算]** タブのツール バー上にある **[キューブ]** メニューから起動できます。 このコマンドでは、名前付きセットの次のオプションを指定するためのフォームが表示されます。  
  
 **Name**  
 名前付きセットの名前を選択します。 この名前は、エンド ユーザーがキューブを参照したときに表示されます。  
  
 **[式]**  
 名前付きセットを作成する式を指定します。 この式は、MDX で記述することもできます。 式には、次の要素を含めることができます。  
  
-   ディメンション、レベル、メジャーなど、キューブのコンポーネントを表すデータ式  
  
-   算術演算子  
  
-   数値  
  
-   関数  
  
 キューブ コンポーネントは、 **[計算ツール]** ペインの **[メタデータ]** タブから **名前付きセット フォーム エディター** ペインの **[式]** ボックスにコピーまたはドラッグできます。 関数は、 **[計算ツール]** ペインの **[関数]** タブから **名前付きセット フォーム エディター** ペインの **[式]** ボックスにコピーまたはドラッグできます。  
  
> [!IMPORTANT]  
>  セット内のメンバーを明示的に指定することによって、セット式を作成する場合は、中かっこのペアでメンバーの一覧を囲みます ({})。  
  
## <a name="see-also"></a>参照  
 [多次元モデルでの計算](calculations-in-multidimensional-models.md)  
  
  