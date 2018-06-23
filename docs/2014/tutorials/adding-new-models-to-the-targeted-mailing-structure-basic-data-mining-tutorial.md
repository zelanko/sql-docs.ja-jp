---
title: ターゲット メーリング構造 (基本的なデータ マイニング チュートリアル) に新しいモデルの追加 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 512c6888-60f1-46e4-9639-bc448395b8d7
caps.latest.revision: 45
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c5e31e06a489b1807335f63dd1675fc9e77c45b4
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312380"
---
# <a name="adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial"></a>絞り込みメール配信構造への新しいモデルの追加 (基本的なデータ マイニング チュートリアル)
  このタスクを使用して追加の 2 つのモデルを定義、**マイニング モデル**データ マイニング デザイナーのタブです。 モデルの作成には、Microsoft クラスタリング アルゴリズムと Microsoft Naive Bayes アルゴリズムを使用します。 この 2 つのアルゴリズムを選択する理由は、不連続値 (自転車の購入) を予測できるためです。 これらのアルゴリズムの詳細については、次を参照してください[Microsoft クラスタ リング アルゴリズム](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)と[Microsoft Naive Bayes アルゴリズム。](../../2014/analysis-services/data-mining/microsoft-naive-bayes-algorithm.md)  
  
### <a name="to-create-a-clustering-mining-model"></a>クラスター マイニング モデルを作成するには  
  
1.  切り替えて、**マイニング モデル** タブで、データ マイニング デザイナーで[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]です。  
  
     デザイナーが 2 つの列のいずれかと、マイニング構造のいずれかを表示することに注意してください、`TM_Decision_Tree`前のレッスンで作成したマイニング モデルです。  
  
2.  右クリックし、**構造**列と select**新しいマイニング モデル**です。  
  
3.  **新しいマイニング モデル**ダイアログ ボックスで、**モデル名**、型`TM_Clustering`です。  
  
4.  **アルゴリズム名** **Microsoft クラスタ リング**です。  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 新しいモデルに表示されるよう、**マイニング モデル**データ マイニング デザイナーのタブです。 このモデルでビルドされた、[!INCLUDE[msCoName](../includes/msconame-md.md)]クラスタ リング アルゴリズム、クラスターに似た特性を持つ顧客グループし、自転車の各クラスターの購買を予測します。 列の使用法と、新しいモデルに変更なしのプロパティを変更できますが、`TM_Clustering`モデルは、このチュートリアルで必要です。  
  
### <a name="to-create-a-naive-bayes-mining-model"></a>Naive Bayes マイニング モデルを作成するには  
  
1.  **マイニング モデル**データ マイニング デザイナーのタブを右**構造**列、および選択**新しいマイニング モデル**です。  
  
2.  **新しいマイニング モデル**ダイアログ ボックスで、**モデル名**、型`TM_NaiveBayes`です。  
  
3.  **アルゴリズム名** **Microsoft Naive Bayes**、順にクリックして**ok**です。  
  
     示すメッセージが表示されます、 [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes アルゴリズムはサポートされていません、 **Age**と**Yearly Income**が連続する列。  
  
4.  をクリックして**はい**メッセージを無視して続行します。  
  
 新しいモデルに表示されます、**マイニング モデル**データ マイニング デザイナーのタブです。 列の使用法やこれですべてのモデルのプロパティを変更することができます タブでは変更されません、`TM_NaiveBayes`モデルは、このチュートリアルで必要です。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [ターゲット メーリング構造でモデルを処理&#40;基本的なデータ マイニングのチュートリアル&#41;](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [構造にマイニング モデルを追加&#40;Analysis Services - データ マイニング&#41;](../../2014/analysis-services/data-mining/add-mining-models-to-a-structure-analysis-services-data-mining.md)   
 [データ マイニング デザイナー](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [データ マイニング オブジェクトの移動](../../2014/analysis-services/data-mining/moving-data-mining-objects.md)  
  
  