---
title: テーブル モデル パーティション作成し、管理 |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7067449c0de9958e98a7a9dc5cc09c7f89f33fa9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62472294"
---
# <a name="create-and-manage-tabular-model-partitions"></a>テーブル モデル パーティション作成し、管理
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]

  パーティションは、テーブルを論理的な部分に分割します。 各パーティションは、他のパーティションとは個別に処理 (更新) できます。 モデル作成時にあるモデルのために定義されたパーティションが、配置済みモデルで複製されます。 いったん配置されると、 **の** [パーティション] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ダイアログ ボックスまたはスクリプトを使用して、それらのパーティションを管理できます。 このトピックで説明するタスクで、配置済みモデル用のパーティションを作成、管理する方法を示します。  
  
  > [!NOTE]  
>  1400 互換性レベルで作成された表形式モデルでパーティションを定義するには、M のクエリ ステートメントを使用します。 詳細についてを参照してください。 [M リファレンス](https://msdn.microsoft.com/library/mt211003.aspx)します。 
>
  
## <a name="tasks"></a>処理手順  
 配置済みテーブル モデル データベース用のパーティションを作成、管理するには、 **で** [パーティション] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ダイアログ ボックスを使用します。 **で** [パーティション] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ダイアログ ボックスを表示するには、任意のテーブルを右クリックし、 **[パーティション]** をクリックします。  
  
###  <a name="bkmk_create_new"></a> 新しいパーティションを作成するには  
  
1.  **[パーティション]** ダイアログ ボックスで **[新規]** をクリックします。  
  
2.  **[パーティション名]** にパーティションの名前を入力します。 既定では、既定のパーティション名に番号が付き、新しいパーティションを作成するたびにその番号が増加します。  
  
3.  **クエリ ステートメント**、入力するか、列と、クエリ ウィンドウに、パーティションに含めるすべての句を定義する、SQL または M のクエリ ステートメントを貼り付けます。  
  
4.  このステートメントを検証するため、 **[構文の確認]** をクリックします。  
  
###  <a name="bkmk_copy"></a> パーティションをコピーするには  
  
1.  **[パーティション]** ダイアログ ボックスの **[パーティション]** ボックスの一覧で、コピーするパーティションを選択し、 **[コピー]** をクリックします。  
  
2.  **[パーティション名]** にパーティションの新しい名前を入力します。  
  
3.  **クエリ ステートメント**、クエリ ステートメントを編集します。  
  
###  <a name="bkmk_merge"></a> 2 つ以上のパーティションをマージするには  
  
-   **[パーティション]** ダイアログ ボックスの **[パーティション]** ボックスの一覧で、マージするパーティションを Ctrl キーを押しながらクリックして選択し、 **[マージ]** をクリックします。  
  
> [!IMPORTANT]  
>  パーティションをマージしても、パーティションのメタデータは更新されません。 処理操作がマージされたパーティションのすべてのデータを処理することを確認して、結果パーティションの SQL または M のステートメントを編集する必要があります。  
  
###  <a name="bkmk_delete"></a> パーティションを削除するには  
  
-   **[パーティション]** ダイアログ ボックスの **[パーティション]** ボックスの一覧で、削除するパーティションを選択し、 **[削除]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [テーブル モデル パーティション](../../analysis-services/tabular-models/tabular-model-partitions-ssas-tabular.md)   
 [プロセスのテーブル モデル パーティション](../../analysis-services/tabular-models/process-tabular-model-partitions-ssas-tabular.md)  
  
  
