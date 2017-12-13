---
title: "ビューまたはアルゴリズム パラメーターの変更 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- algorithms [data mining]
- mining models [Analysis Services], algorithms
ms.assetid: 151b899b-c27a-4a09-bcf5-5c9f0ec24168
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9f547511bc918c4b55693207aaf1181da7378c43
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="view-or-change-algorithm-parameters"></a>アルゴリズム パラメーターの表示または変更
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]モデルの結果をカスタマイズするデータ マイニング モデルの作成に使用したアルゴリズムで提供されるパラメーターを変更することができます。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] に用意されているアルゴリズム パラメーターを使用すると、モデルのプロパティを変更できるだけでなく、データの処理方法、グループ化方法、および表示方法を根本から変更できます。 たとえば、アルゴリズム パラメーターを使用すると、次の操作を実行できます。  
  
-   分析方法 (クラスタリング方法など) を変更する。  
  
-   機能の選択動作を制御する。  
  
-   アイテムセットのサイズまたはルールの確率を指定する。  
  
-   デシジョン ツリーの分岐と深さを制御する。  
  
-   シード値またはモデルの作成に使用される内部の提示されるセットのサイズを指定する。  
  
 それぞれのアルゴリズムで提供されるパラメーターは大きく異なります。各アルゴリズムに対して設定できるパラメーターの一覧については、「[データ マイニング アルゴリズム (Analysis Services - データ マイニング)](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)」のテクニカル リファレンス トピックを参照してください。  
  
### <a name="change-an-algorithm-parameter"></a>アルゴリズム パラメーターを変更する  
  
1.  **のデータ マイニング デザイナーの** [マイニング モデル] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]タブで、アルゴリズムを調整するマイニング モデルのアルゴリズムの種類を右クリックし、 **[アルゴリズム パラメーターの設定]**をクリックします。  
  
     **[アルゴリズム パラメーター]** ダイアログ ボックスが開きます。  
  
2.  **[値]** 列で、変更するアルゴリズムの新しい値を設定します。  
  
     **[値]** 列に値を入力しない場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ではパラメーターの既定値が使用されます。 **[範囲]** 列には、入力可能な値が示されます。  
  
3.  **[OK]**をクリックします。  
  
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
  
  
