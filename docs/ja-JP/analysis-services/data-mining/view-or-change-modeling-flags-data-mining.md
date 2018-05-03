---
title: 表示または変更するモデリング フラグ (データ マイニング) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d1169735-fb18-417b-b8d6-9a161e444020
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 5ca890dca3e0ffb966f1b87a745b189db4af6d81
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="view-or-change-modeling-flags-data-mining"></a>モデリング フラグの表示または変更 (データ マイニング)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  モデリング フラグは、マイニング構造列またはマイニング モデル列に設定して、分析時にアルゴリズムがデータを処理する方法を制御するためのプロパティです。  
  
 データ マイニング デザイナーでは、マイニング構造やマイニング列に関連付けられているモデリング フラグを、その構造またはモデルのプロパティを表示することによって表示および変更することができます。 DMX、AMO、または XMLA を使用してモデリング フラグを設定することもできます。  
  
 この手順では、デザイナーでモデリング フラグを変更する方法について説明します。  
  
### <a name="view-or-change-the-modeling-flag-for-a-structure-column-or-model-column"></a>構造列またはモデル列のモデリング フラグの表示または変更  
  
1.  SQL Server Design Studio で、ソリューション エクスプローラーを開き、マイニング構造をダブルクリックします。  
  
2.  NOT NULL モデリング フラグを設定するには、 **[マイニング構造]** タブをクリックします。REGRESSOR フラグまたは MODEL_EXISTENCE_ONLY フラグを設定するには、 **[マイニング モデル]** タブをクリックします。  
  
3.  表示または変更する列を右クリックし、 **[プロパティ]** をクリックします。  
  
4.  新しいモデリング フラグを追加するには、 **[ModelingFlags]** プロパティの横にあるテキスト ボックスをクリックし、使用するモデリング フラグのチェック ボックスをオンにします。  
  
     その列のデータ型に合ったモデリング フラグのみが表示されます。  
  
    > [!NOTE]  
    >  モデリング フラグを変更した後、モデルを再処理する必要があります。  
  
### <a name="get-the-modeling-flags-used-in-the-model"></a>モデルで使用されているモデリング フラグの取得  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、DMX クエリ ウィンドウを開き、次のようなクエリを入力します。  
  
    ```  
    SELECT COLUMN_NAME, CONTENT_TYPE, MODELING_FLAG  
    FROM $system.DMSCHEMA_MINING_COLUMNS  
    WHERE MODEL_NAME = 'Forecasting'  
  
    ```  
  
## <a name="see-also"></a>参照  
 [マイニング モデル タスクと操作方法](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [モデリング フラグ (&) #40 です。 データ マイニング & #41;](../../analysis-services/data-mining/modeling-flags-data-mining.md)  
  
  
