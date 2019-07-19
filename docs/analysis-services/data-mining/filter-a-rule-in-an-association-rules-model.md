---
title: フィルター ルール モデルのアソシエーション ルール |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 28d3601b18f792b957627e63630806453d971110
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68209994"
---
# <a name="filter-a-rule-in-an-association-rules-model"></a>アソシエーション ルール モデルのルールのフィルター選択
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  アソシエーション モデルでフィルターを使用して、結果を必要なアソシエーションだけに限定できます。 たとえば、ルールをフィルター選択して、特定の製品を含むルールだけを表示できます。  
  
 データ マイニング デザイナーで、 **アソシエーション ルール ビューアーの** [ルール] [!INCLUDE[msCoName](../../includes/msconame-md.md)] タブのコントロールを使用して、表示されるルールをフィルター選択します。  モデルに対するクエリを作成して、特定の値が格納されているアイテムセットだけを表示することもできます。  
  
> [!NOTE]  
>  このオプションは、Microsoft アソシエーション アルゴリズムを使用して作成されたマイニング モデルに対してのみ使用できます。  
  
### <a name="filter-a-rule-in-an-association-model"></a>アソシエーション モデルのルールのフィルター選択  
  
1.  **アソシエーション ルール ビューアー**を使用してマイニング モデルを開きます。 SQL Server Management Studio でマイニング モデルを開くには、モデル名を右クリックして **[参照]** をクリックします。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でマイニング モデルを開くには、モデルを含むマイニング構造をダブルクリックし、 **データ マイニング デザイナー** の **[マイニング モデル ビューアー]** タブをクリックします。  
  
2.  **アソシエーション ルール ビューアー** の **[ルール]** タブをクリックします。  
  
3.  **[ルールのフィルター]** ボックスにルールの条件を入力します。 たとえば、「Bike Stand」というルールの条件を入力すると、"Bike Stands" も返されます。  
  
     **[ルールのフィルター]** テキスト ボックスでは、.NET 言語で定義されている正規表現を使用できます。 したがって、 `((.Helmets.*Fenders.*)|(.*Fenders.*Helmets.*))`のような式を使用できます。 この式は、Helmets と Fenders という単語が任意の順序で含まれる属性を含むすべてのアイテムセットを返します。  
  
4.  **[最小の確率]** では、確率の値を大きくすると表示されるルール数が減り、値を小さくすると表示されるルール数が増えます。  
  
5.  **[最小の重要度]** では、重要度の値を大きくすると表示されるルール数が減り、値を小さくすると表示されるルール数が増えます。  
  
6.  **表示**、次のオプションのいずれかを選択します。**属性の名前と値を表示する**、 **属性名のみ**、または**属性値のみを表示する**します。  
  
7.  **[最大行数]** では、値を大きくすると指定した条件を満たすルールの総数が増え、値を小さくすると返されるルールの数が制限されます。 ルールは確率の順に並べられるので、確率または重要度に対して指定した条件を満たす余分なルールを除外できます。  
  
8.  **[長い名前を表示する]** チェック ボックスをオンまたはオフにして、ルール名の表示方法を切り替えます。  
  
     これでルールにフィルターが適用され、指定したアイテムを含むルールのみが表示されます。 フィルター条件は、ルール区切り記号 "->" の前または後の属性値に適用されます。  
  
    > [!NOTE]  
    >  ビューアーはマイニング モデルに対するクエリによって最初に作成されるルールの一覧をキャッシュしており、最大行数、確率、重要度、または長い名前の表示を設定することでクエリの条件を変更しない限り、この一覧は更新されません。 したがって、条件を入力しても表示がすぐに更新されない場合は、 **[長い名前を表示する]** チェック ボックスをオンにしてからオフにすることで、強制的にビューアーのデータを更新することができます。  
  
### <a name="create-a-query-on-the-itemsets-in-an-association-model"></a>アソシエーション モデルのアイテムセットに対するクエリの作成  
  
-   [結合モデルのクエリ例](../../analysis-services/data-mining/association-model-query-examples.md)  
  
## <a name="see-also"></a>関連項目  
 [マイニング モデル ビューアーのタスクと操作方法](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Microsoft アソシエーション ルール ビューアーを使用したモデルの参照](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)   
 [レッスン 3:マーケット バスケット シナリオの作成&#40;中級者向けデータ マイニング チュートリアル&#41;](http://msdn.microsoft.com/library/651eef38-772e-4d97-af51-075b1b27fc5a)  
  
  
