---
title: マーケットバスケットモデルの変更と処理 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b6019413-aebd-4ff7-831a-644572ad88b1
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 4987e3497b7d52ff11f8f52bc403105340f7f508
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63301373"
---
# <a name="modifying-and-processing-the-market-basket-model-intermediate-data-mining-tutorial"></a>マーケット バスケット モデルの変更と処理 (中級者向けデータ マイニング チュートリアル)
  作成した association マイニングモデルを処理する前に、*サポート*と*確率*の2つのパラメーターの既定値を変更する必要があります。  
  
-   *サポート*は、ルールが有効と見なされる前に存在している必要があるケースの割合を定義します。 ここでは、1% 以上のケースでルールが検出される必要があるように指定します。  
  
-   *確率*は、アソシエーションが有効と見なされるまでの確率を定義します。 ここでは、確率が 10% 以上のアソシエーションを対象とします。  
  
 サポートと確率の増減による影響の詳細については、「 [Microsoft アソシエーションアルゴリズムテクニカルリファレンス](../../2014/analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md)」を参照してください。  
  
 **アソシエーション**マイニングモデルの構造とパラメーターを定義した後は、モデルを処理します。  
  
### <a name="to-adjust-the-parameters-of-the-association-model"></a>Association モデルのパラメーターを調整するには  
  
1.  データマイニングデザイナーの [**マイニングモデル**] タブを開きます。  
  
2.  デザイナーのグリッドで [ **Association** ] 列を右クリックし、[**アルゴリズムパラメーターの設定**] をクリックして [アルゴリズムパラメーター] ダイアログボックスを開きます。  
  
3.  [**アルゴリズムパラメーター** ] ダイアログボックスの [**値**] 列で、次のパラメーターを設定します。  
  
     MINIMUM_PROBABILITY = 0.1  
  
     MINIMUM_SUPPORT = 0.01  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-process-the-mining-model"></a>マイニング モデルを処理するには  
  
1.  の [**マイニングモデル**] メニュー [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、[**マイニング構造とすべてのモデルの処理**] を選択します。  
  
2.  プロジェクトをビルドして配置するかどうかを確認する警告が表示されたら、[**はい]** をクリックします。  
  
     [**マイニング構造の処理-アソシエーション**] ダイアログボックスが表示されます。  
  
3.  **[実行]** をクリックします。  
  
     [**処理の進行状況**] ダイアログボックスが開き、モデルの処理に関する情報が表示されます。 新しい構造とモデルの処理には、時間がかかることがあります。  
  
4.  処理が完了したら、[**閉じる**] をクリックして [**処理の進行状況**] ダイアログボックスを閉じます。  
  
5.  もう一度 [**閉じる**] をクリックして [**マイニング構造の処理-アソシエーション**] ダイアログボックスを閉じます。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [&#40;中級者向けデータマイニングチュートリアルに関するマーケットバスケットモデルの調査&#41;](../../2014/tutorials/exploring-the-market-basket-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [データマイニング&#41;&#40;処理の要件と考慮事項](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
