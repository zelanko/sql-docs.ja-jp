---
title: ビューまたはアルゴリズム パラメーターの変更 |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 49cdffc9723f7d3489f84d7f40e6c0eb24150f52
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="view-or-change-algorithm-parameters"></a>アルゴリズム パラメーターの表示または変更
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  データ マイニング モデルをビルドするためのアルゴリズムで提供されているパラメーターを変更して、モデルの結果をカスタマイズできます。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] に用意されているアルゴリズム パラメーターを使用すると、モデルのプロパティを変更できるだけでなく、データの処理方法、グループ化方法、および表示方法を根本から変更できます。 たとえば、アルゴリズム パラメーターを使用すると、次の操作を実行できます。  
  
-   分析方法 (クラスタリング方法など) を変更する。  
  
-   機能の選択動作を制御する。  
  
-   アイテムセットのサイズまたはルールの確率を指定する。  
  
-   デシジョン ツリーの分岐と深さを制御する。  
  
-   シード値またはモデルの作成に使用される内部の提示されるセットのサイズを指定する。  
  
 それぞれのアルゴリズムで提供されるパラメーターは大きく異なります。各アルゴリズムに対して設定できるパラメーターの一覧については、「[データ マイニング アルゴリズム (Analysis Services - データ マイニング)](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)」のテクニカル リファレンス トピックを参照してください。  
  
### <a name="change-an-algorithm-parameter"></a>アルゴリズム パラメーターを変更する  
  
1.  **のデータ マイニング デザイナーの** [マイニング モデル] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]タブで、アルゴリズムを調整するマイニング モデルのアルゴリズムの種類を右クリックし、 **[アルゴリズム パラメーターの設定]** をクリックします。  
  
     **[アルゴリズム パラメーター]** ダイアログ ボックスが開きます。  
  
2.  **[値]** 列で、変更するアルゴリズムの新しい値を設定します。  
  
     **[値]** 列に値を入力しない場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ではパラメーターの既定値が使用されます。 **[範囲]** 列には、入力可能な値が示されます。  
  
3.  **[OK]** をクリックします。  
  
     アルゴリズム パラメーターが新しい値で設定されます。 パラメーターの変更は、マイニング モデルを再処理するまではマイニング モデルに反映されません。  
  
### <a name="view-the-parameters-used-in-an-existing-model"></a>既存のモデルで使用されているパラメーターを表示する  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、DMX クエリ ウィンドウを開きます。  
  
2.  次のようなクエリを入力します。  
  
    ```  
    select MINING_PARAMETERS   
    from $system.DMSCHEMA_MINING_MODELS  
    WHERE MODEL_NAME = '<model name>'  
  
    ```  
  
## <a name="see-also"></a>参照  
 [マイニング モデル タスクと操作方法](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
