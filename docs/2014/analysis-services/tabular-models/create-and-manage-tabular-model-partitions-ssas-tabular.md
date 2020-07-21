---
title: テーブルモデルパーティションの作成および管理 (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: dab72cf0-95bc-4b63-95dc-505b5cd881c1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 27f6bda21381a3388e51c387b072c80026b44c6a
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84939783"
---
# <a name="create-and-manage-tabular-model-partitions-ssas-tabular"></a>テーブル モデル パーティションの作成および管理 (SSAS テーブル)
  パーティションは、テーブルを論理的な部分に分割します。 各パーティションは、他のパーティションとは個別に処理 (更新) できます。 モデル作成時にあるモデルのために定義されたパーティションが、配置済みモデルで複製されます。 いったん配置されると、 **の** [パーティション] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ダイアログ ボックスまたはスクリプトを使用して、それらのパーティションを管理できます。 このトピックで説明するタスクで、配置済みモデル用のパーティションを作成、管理する方法を示します。  
  
 このトピックでは、次のタスクについて説明します。  
  
-   [新しいパーティションを作成するには](#bkmk_create_new)  
  
-   [パーティションをコピーするには](#bkmk_copy)  
  
-   [2つ以上のパーティションをマージするには](#bkmk_merge)  
  
-   [パーティションを削除するには](#bkmk_delete)  
  
## <a name="tasks"></a>タスク  
 配置済みテーブル モデル データベース用のパーティションを作成、管理するには、 **で** [パーティション] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ダイアログ ボックスを使用します。 **で** [パーティション] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ダイアログ ボックスを表示するには、任意のテーブルを右クリックし、 **[パーティション]** をクリックします。  
  
###  <a name="to-create-a-new-partition"></a><a name="bkmk_create_new"></a>新しいパーティションを作成するには  
  
1.  **[パーティション]** ダイアログ ボックスで **[新規]** をクリックします。  
  
2.  **[パーティション名]** にパーティションの名前を入力します。 既定では、既定のパーティション名に番号が付き、新しいパーティションを作成するたびにその番号が増加します。  
  
3.  **[SQL ステートメント]** で、列を定義する SQL クエリ ステートメント、およびパーティションに含める句をクエリ ウィンドウに入力するか貼り付けます。  
  
4.  このステートメントを検証するため、 **[構文の確認]** をクリックします。  
  
###  <a name="to-copy-a-partition"></a><a name="bkmk_copy"></a>パーティションをコピーするには  
  
1.  **[パーティション]** ダイアログ ボックスの **[パーティション]** ボックスの一覧で、コピーするパーティションを選択し、 **[コピー]** をクリックします。  
  
2.  **[パーティション名]** にパーティションの新しい名前を入力します。  
  
3.  **[SQL ステートメント]** で、SQL クエリ ステートメントを編集します。  
  
###  <a name="to-merge-two-or-more-partitions"></a><a name="bkmk_merge"></a> 2 つ以上のパーティションをマージするには  
  
-   **[パーティション]** ダイアログ ボックスの **[パーティション]** ボックスの一覧で、マージするパーティションを Ctrl キーを押しながらクリックして選択し、 **[マージ]** をクリックします。  
  
> [!IMPORTANT]  
>  パーティションをマージしても、パーティションのメタデータは更新されません。 管理者は、マージ後のパーティションの SQL ステートメントを変更し、マージされたパーティション内のすべてのデータが処理操作で確実に処理されるようにする必要があります。  
  
###  <a name="to-delete-a-partition"></a><a name="bkmk_delete"></a> パーティションを削除するには  
  
-   **[パーティション]** ダイアログ ボックスの **[パーティション]** ボックスの一覧で、削除するパーティションを選択し、 **[削除]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [SSAS 表形式&#41;&#40;テーブルモデルパーティション](partitions-ssas-tabular.md)   
 [テーブル モデル パーティションの処理 (SSAS テーブル)](process-tabular-model-partitions-ssas-tabular.md)  
  
  
