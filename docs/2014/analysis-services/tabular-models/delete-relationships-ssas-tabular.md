---
title: リレーションシップ (SSAS テーブル) の削除 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d40e3f05-54e8-4c4b-807a-0b06f446079b
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 530e00790a649ad7ccaebfddfc3582d23ee1b1e2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249172"
---
# <a name="delete-relationships-ssas-tabular"></a>リレーションシップの削除 (SSAS テーブル)
  ダイアグラム ビューのモデル デザイナーまたは [リレーションシップの管理] ダイアログ ボックスを使用して、既存のリレーションシップを削除できます。 表形式モデルでリレーションシップを使用する方法については、次を参照してください。[リレーションシップ&#40;SSAS 表形式&#41;](relationships-ssas-tabular.md)します。  
  
## <a name="considerations-for-deleting-relationships"></a>リレーションシップの削除に関する注意事項  
 リレーションシップを削除するかどうかを判断する際には、以下の点に注意してください。  
  
-   リレーションシップの削除を元に戻す方法はありません。 リレーションシップを再作成することはできますが、これを行うには、モデル内の数式をすべて再計算する必要があります。 そのため、数式で使用されているリレーションシップを削除する場合は、このことを事前にチェックすることが重要です。  
  
-   2 つのテーブル間のリレーションシップを削除すると、それらのテーブルを参照する数式でエラーが発生します。  
  
-   Data Analysis Expression (DAX) の RELATED 関数は、テーブル間のリレーションシップを使用して関連する値をもう一方のテーブルで検索します。 リレーションシップが削除されると、この関数は異なる結果を返します。 詳細については、RELATED 関数 (DAX) を参照してください。  
  
-   リレーションシップを作成および削除すると、ピボットテーブルと数式の結果が変わるだけでなく、ブックの再計算も実行されます。この処理には、時間がかかることがあります。  
  
## <a name="delete-relationships"></a>リレーションシップの削除  
  
#### <a name="to-delete-a-relationship-by-using-diagram-view"></a>ダイアグラム ビューを使用してリレーションシップを削除するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、 **[モデル]** メニューをクリックし、 **[モデル ビュー]** をポイントして、 **[ダイアグラム ビュー]** をクリックします。  
  
2.  2 つのテーブルの間のリレーションシップの線を右クリックし、 **[削除]** をクリックします。  
  
#### <a name="to-delete-a-relationship-by-using-the-manage-relationships-dialog-box"></a>[リレーションシップの管理] ダイアログ ボックスを使用してリレーションシップを削除するには  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、 **[テーブル]** メニューをクリックし、 **[リレーションシップの管理]** をクリックします。  
  
2.  **[リレーションシップの管理]** ダイアログ ボックスで、一覧から 1 つまたは複数のリレーションシップを選択します。  
  
     複数のリレーションシップを選択するには、Ctrl キーを押しながら各リレーションシップをクリックします。  
  
3.  **[リレーションシップの削除]** をクリックします。  
  
4.  **[リレーションシップの管理]** ダイアログ ボックスで、 **[閉じる]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [リレーションシップ&#40;SSAS 表形式&#41;](relationships-ssas-tabular.md)   
 [2 つのテーブル間のリレーションシップを作成する&#40;SSAS 表形式&#41;](create-a-relationship-between-two-tables-ssas-tabular.md)  
  
  
