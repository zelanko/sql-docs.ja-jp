---
title: Analysis Services 表形式モデルにテーブルを追加 |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 224df75c15acf560c7eadc70fe91fbbc2b0396d9
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072289"
---
# <a name="add-a-table"></a>テーブルの追加
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  この記事では、元の以前にインポートしたデータ モデルのデータ ソースからテーブルを追加する方法について説明します。 同じデータ ソースからテーブルを追加するには、既存のデータ ソース接続を使用できます。 1 つのデータ ソースから任意の数のテーブルをインポートする場合は、常に 1 つの接続を使用することをお勧めします。  
  
### <a name="to-add-a-table-from-an-existing-data-source"></a>既存のデータ ソースからテーブルを追加するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で **[モデル]** メニューをクリックしてから **[既存の接続]** をクリックします。  
  
2.  **[既存の接続]** ページで、追加するテーブルが含まれているデータ ソースへの接続を選択し、 **[開く]** をクリックします。  
  
3.  **[テーブルとビューの選択]** ページで、データ ソースからモデルに追加するテーブルを選択します。  
  
    > [!NOTE]  
    >  **[テーブルとビューの選択]** ページには、以前にインポートされたテーブルは選択済みとして表示されません。  この接続を使用して以前にインポートされたテーブルを選択し、そのテーブルに別の表示名を指定しなかった場合は、表示名に 1 が付加されます。 この接続を使用して以前にインポートされたテーブルを再度選択する必要はありません。  
  
4.  必要に応じて、**[プレビューとフィルター]** を使用して、特定の列のみを選択するか、インポートするデータにフィルターを適用します。  
  
5.  **[完了]** をクリックして、新しいテーブルをインポートします。  
  
> [!NOTE]  
>  1 つのデータ ソースから複数のテーブルを同時にインポートする場合、それらのテーブル間のソースでのリレーションシップがモデル内に自動的に作成されます。 ただし、後からテーブルを追加する場合は、新しく追加されたテーブルと以前にインポートされたテーブルの間のリレーションシップを、モデル内に手動で作成することが必要な場合があります。  
  
## <a name="see-also"></a>関連項目  
 [データのインポート](http://msdn.microsoft.com/library/6617b2a2-9f69-433e-89e0-4c5dc92982cf)   
 [テーブルの削除](../../analysis-services/tabular-models/delete-a-table-ssas-tabular.md)  
  
  
