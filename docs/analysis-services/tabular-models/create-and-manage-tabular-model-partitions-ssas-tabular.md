---
title: "作成し、テーブル モデル パーティション (SSAS テーブル) を管理する |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/31/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dab72cf0-95bc-4b63-95dc-505b5cd881c1
caps.latest.revision: "8"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1fc4d1caf2aacf96a44b33d44e6d95cc98e955c4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="create-and-manage-tabular-model-partitions"></a>テーブル モデル パーティションの作成および管理
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]

  パーティションは、テーブルを論理的な部分に分割します。 各パーティションは、他のパーティションとは個別に処理 (更新) できます。 モデル作成時にあるモデルのために定義されたパーティションが、配置済みモデルで複製されます。 いったん配置されると、 **の** [パーティション] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ダイアログ ボックスまたはスクリプトを使用して、それらのパーティションを管理できます。 このトピックで説明するタスクで、配置済みモデル用のパーティションを作成、管理する方法を示します。  
  
  > [!NOTE]  
>  1400 互換性レベルで作成された表形式モデルでパーティションを定義するには、M クエリ ステートメントを使用します。 詳細については、次を参照してください。 [M 参照](https://msdn.microsoft.com/library/mt211003.aspx)です。 
>
  
## <a name="tasks"></a>処理手順  
 配置済みテーブル モデル データベース用のパーティションを作成、管理するには、 **で** [パーティション] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ダイアログ ボックスを使用します。 **で** [パーティション] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ダイアログ ボックスを表示するには、任意のテーブルを右クリックし、 **[パーティション]**をクリックします。  
  
###  <a name="bkmk_create_new"></a> 新しいパーティションを作成するには  
  
1.  **[パーティション]** ダイアログ ボックスで **[新規]** をクリックします。  
  
2.  **[パーティション名]**にパーティションの名前を入力します。 既定では、既定のパーティション名に番号が付き、新しいパーティションを作成するたびにその番号が増加します。  
  
3.  **クエリ ステートメント**を入力するか、列と、クエリ ウィンドウに、パーティションに含める句を定義する、SQL または M のクエリ ステートメントを貼り付けます。  
  
4.  このステートメントを検証するため、 **[構文の確認]**をクリックします。  
  
###  <a name="bkmk_copy"></a> パーティションをコピーするには  
  
1.  **[パーティション]** ダイアログ ボックスの **[パーティション]** ボックスの一覧で、コピーするパーティションを選択し、 **[コピー]** をクリックします。  
  
2.  **[パーティション名]**にパーティションの新しい名前を入力します。  
  
3.  **クエリ ステートメント**、クエリ ステートメントを編集します。  
  
###  <a name="bkmk_merge"></a> 2 つ以上のパーティションをマージするには  
  
-   **[パーティション]** ダイアログ ボックスの **[パーティション]** ボックスの一覧で、マージするパーティションを Ctrl キーを押しながらクリックして選択し、 **[マージ]** をクリックします。  
  
> [!IMPORTANT]  
>  パーティションをマージしても、パーティションのメタデータは更新されません。 処理操作がマージされたパーティションのすべてのデータを処理かどうかを確認する結果として得られるパーティションに、SQL または M のステートメントを編集する必要があります。  
  
###  <a name="bkmk_delete"></a> パーティションを削除するには  
  
-   **[パーティション]** ダイアログ ボックスの **[パーティション]** ボックスの一覧で、削除するパーティションを選択し、 **[削除]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [テーブル モデル パーティション](../../analysis-services/tabular-models/tabular-model-partitions-ssas-tabular.md)   
 [テーブル モデル パーティションの処理](../../analysis-services/tabular-models/process-tabular-model-partitions-ssas-tabular.md)  
  
  
