---
title: "テーブルの追加 (SSAS 表形式) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d713c432-db99-4983-acc1-52b0fdd58bd6
caps.latest.revision: "5"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 71a4385d5f6ab0a2fd396b78651a8609d55e74ac
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="add-a-table-ssas-tabular"></a>テーブルの追加 (SSAS テーブル)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]このトピックでは、元が以前にインポートしたデータをモデルにデータ ソースからテーブルを追加する方法について説明します。 同じデータ ソースからテーブルを追加するには、既存のデータ ソース接続を使用できます。 1 つのデータ ソースから任意の数のテーブルをインポートする場合は、常に 1 つの接続を使用することをお勧めします。  
  
### <a name="to-add-a-table-from-an-existing-data-source"></a>既存のデータ ソースからテーブルを追加するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で **[モデル]** メニューをクリックしてから **[既存の接続]**をクリックします。  
  
2.  **[既存の接続]** ページで、追加するテーブルが含まれているデータ ソースへの接続を選択し、 **[開く]**をクリックします。  
  
3.  **[テーブルとビューの選択]** ページで、データ ソースからモデルに追加するテーブルを選択します。  
  
    > [!NOTE]  
    >  **[テーブルとビューの選択]** ページには、以前にインポートされたテーブルは選択済みとして表示されません。  この接続を使用して以前にインポートされたテーブルを選択し、そのテーブルに別の表示名を指定しなかった場合は、表示名に 1 が付加されます。 この接続を使用して以前にインポートされたテーブルを再度選択する必要はありません。  
  
4.  必要に応じて、**[プレビューとフィルター]** を使用して、特定の列のみを選択するか、インポートするデータにフィルターを適用します。  
  
5.  **[完了]** をクリックして、新しいテーブルをインポートします。  
  
> [!NOTE]  
>  1 つのデータ ソースから複数のテーブルを同時にインポートする場合、それらのテーブル間のソースでのリレーションシップがモデル内に自動的に作成されます。 ただし、後からテーブルを追加する場合は、新しく追加されたテーブルと以前にインポートされたテーブルの間のリレーションシップを、モデル内に手動で作成することが必要な場合があります。  
  
## <a name="see-also"></a>参照  
 [データのインポート &#40;SSAS テーブル&#41;](http://msdn.microsoft.com/library/6617b2a2-9f69-433e-89e0-4c5dc92982cf)   
 [テーブルの削除 &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/delete-a-table-ssas-tabular.md)  
  
  
