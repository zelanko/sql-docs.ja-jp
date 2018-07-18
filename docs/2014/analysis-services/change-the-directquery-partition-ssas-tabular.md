---
title: DirectQuery パーティション (SSAS テーブル) の変更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f9df1e66-dd23-41b4-95eb-af110d10eda4
caps.latest.revision: 9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3115805cf5d6d8fabfa67100305f7bdffea1d339
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37312682"
---
# <a name="change-the-directquery-partition-ssas-tabular"></a>DirectQuery パーティションの変更 (SSAS テーブル)
  テーブル内で DirectQuery パーティションとして指定できるパーティションは 1 つだけであるため、Analysis Services ではテーブルに作成された最初のパーティションが既定で使用されます。 モデル プロジェクトの作成時に、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]の [パーティション マネージャー] ダイアログ ボックスを使用して DirectQuery パーティションを変更できます。 配置済みのモデルでは、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]を使用して DirectQuery パーティションを変更できます  
  
### <a name="change-the-directquery-partition-for-a-tabular-model-project"></a>テーブル モデル プロジェクトの DirectQuery パーティションの変更  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]のモデル デザイナーで、パーティション テーブルが含まれているテーブル (タブ) をクリックします。  
  
2.  **[テーブル]** メニューをクリックし、 **[パーティション]** をクリックします。  
  
3.  **[パーティション マネージャー]** で、現在の直接クエリ パーティションであるパーティションはパーティション名に **(DirectQuery)** というプレフィックスで示されます。  
  
     **[パーティション]** ボックスの一覧で別のパーティションを選択し、 **[DirectQuery として設定]** をクリックします。 **[DirectQuery として設定]** ボタンは、現在の DirectQuery パーティションが選択されている場合は無効になり、モデルが直接 Direct Query モードに対して有効になっていない場合は表示されません。  
  
4.  必要に応じて、処理オプションを変更し、 **[OK]** をクリックします。  
  
### <a name="change-the-directquery-partition-for-a-deployed-tabular-model"></a>配置済みテーブル モデルの DirectQuery パーティションの変更  
  
1.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]で、オブジェクト エクスプローラーにモデル データベースを開きます。  
  
2.  **[テーブル]** ノードを展開し、パーティション分割されたテーブルを右クリックして **[パーティション]** を選択します。  
  
     DirectQuery モードで使用するように指定されたパーティションには、パーティション名にプレフィックス (DirectQuery) があります。  
  
3.  別のパーティションに変更するには、 **[直接クエリ]** ツール バー アイコンをクリックして **[DirectQuery パーティションの設定]** ダイアログ ボックスを開きます。 [直接クエリ] ツール バー アイコンは、直接クエリに対して有効になっていないモデルでは使用できません。  
  
4.  **[パーティション名]** ボックスの一覧から別のパーティションを選択し、必要に応じてパーティションの処理オプションを変更します。  
  
## <a name="see-also"></a>参照  
 [パーティション&#40;SSAS 表形式&#41;](tabular-models/partitions-ssas-tabular.md)  
  
  
