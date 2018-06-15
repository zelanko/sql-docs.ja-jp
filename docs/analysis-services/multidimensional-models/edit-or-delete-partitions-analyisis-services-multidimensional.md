---
title: 編集または削除パーティション (Analyisis Services - 多次元) |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 739775890b324c89357ec4f1ba8f627277788087
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34024329"
---
# <a name="edit-or-delete-partitions-analyisis-services---multidimensional"></a>パーティションの編集または削除 (Analysis Services - 多次元)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  キューブ パーティションを変更するには、[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] でキューブ デザイナーの **[パーティション]** タブを使用します。 **[パーティション]** タブには、キューブのすべてのメジャー グループのパーティションが一覧表示されます。 また、書き戻しが有効な書き戻しパーティションも表示されます。  
  
 メジャー グループのパーティションを編集するには、 **[パーティション]** タブでメジャー グループを展開します。メジャー グループのパーティションは、次の表に記載されている列を持つテーブル形式で序数ごとに一覧表示されます。  
  
 リンク メジャー グループの設定は、ソース キューブで編集する必要があります。  
  
 マージ元のパーティションをマージ先のパーティションにマージすると、自動的にパーティションが削除されます。 マージ元として指定されたパーティションは、マージが完了した後に削除されます。 パーティションは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、または [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]の [パーティション] タブで手動で削除することもできます。 右クリックして **[削除]** をクリックします。 パーティションを削除すると、データと集計も削除されることに注意してください。 念のため、後でこの手順を元に戻すことが必要になった場合に備えて、データベースの最新のバックアップを用意しておいてください。  
  
> [!NOTE]  
>  代わりに、パーティションの作成、マージ、および削除を実行するためのタスクを自動化する XMLA スクリプトを使用することもできます。 XMLA スクリプトは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、または定期タスクとして実行されるカスタム SSIS パッケージで作成および実行できます。 詳細については、「 [SSIS による Analysis Services 管理タスクの自動化](../../analysis-services/instances/automate-analysis-services-administrative-tasks-with-ssis.md)」を参照してください。  
  
## <a name="partition-source"></a>パーティション ソース  
 パーティションのソース テーブルまたは名前付きクエリを指定します。 ソース テーブルを変更するには、セルをクリックし、参照ボタン (**[...]**) をクリックします。  
  
 ![[パーティション] ペイン内のソース列](../../analysis-services/multidimensional-models/media/ssas-partitionsource.png "[パーティション] ペイン内のソース列")  
  
 パーティションがクエリに基づいている場合は、参照ボタン (**[...]**) をクリックしてクエリを編集します。 これにより、パーティションの **[ソース]** プロパティが編集されます。 詳しくは、「 [別のファクト テーブルを使用するためのパーティション ソースの変更](../../analysis-services/multidimensional-models/change-a-partition-source-to-use-a-different-fact-table.md)」をご覧ください。  
  
 (データの取得元となる外部データ ソース内の) 元のソース テーブルと同じ構造を持つ、データ ソース ビュー内のテーブルを指定できます。 ソースには、キューブ データベースのデータ ソースまたはデータ ソース ビューを使用できます。  
  
## <a name="storage-settings"></a>ストレージ設定  
 キューブ デザイナーの [パーティション] タブでは、 **[ストレージ設定]** をクリックすると、MOLAP、ROLAP、または HOLAP ストレージの標準設定のいずれかを選択したり、ストレージ モードやプロアクティブ キャッシュのカスタム設定を構成したりできます。 既定では MOLAP が選択されており、最も高速なクエリ パフォーマンスを実現します。 各設定について詳しくは、「[パーティション ストレージの設定 &#40;Analysis Services - 多次元&#41;](../../analysis-services/multidimensional-models/set-partition-storage-analysis-services-multidimensional.md)」をご覧ください。  
  
 ストレージは、キューブ内の各メジャー グループのパーティションごとに個別に構成できます。 キューブまたはメジャー グループの既定のストレージ設定を構成することもできます。 ストレージは、キューブ ウィザードの **[パーティション]** タブで構成します。  
  
## <a name="see-also"></a>参照  
 [作成し、ローカル パーティション & #40; を管理Analysis Services & #41;](../../analysis-services/multidimensional-models/create-and-manage-a-local-partition-analysis-services.md)   
 [デザインの集計 & #40 です。Analysis Services - 多次元 & #41;](../../analysis-services/multidimensional-models/designing-aggregations-analysis-services-multidimensional.md)   
 [Analysis Services & #40; 内のパーティションをマージします。SSAS - 多次元 & #41;](../../analysis-services/multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md)  
  
  
