---
title: "作成および管理のパースペクティブ (SSAS テーブル) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.asvs.bidtoolset.perspectivedb.f1
ms.assetid: 2a411c2b-2820-4086-ad7f-ce6a941fefc7
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 37228aace939d68a3e97e9b818a8cffe62b7632a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="create-and-manage-perspectives-ssas-tabular"></a>パースペクティブの作成と管理 (SSAS テーブル)
  パースペクティブを使用すると、ビジネス固有またはアプリケーション固有のビューポイントをモデルに対して的を絞って作成するための、表示可能なサブセットを定義できます。 このトピックのタスクでは、モデル デザイナーで **[パースペクティブ]** ダイアログ ボックスを使用して、パースペクティブを作成し管理する方法について説明します。  
  
 このトピックでは、次のタスクについて説明します。  
  
-   [パースペクティブを追加するには](#bkmk_add)  
  
-   [パースペクティブを編集するには](#bkmk_edit)  
  
-   [パースペクティブの名前を変更するには](#bkmk_rename)  
  
-   [パースペクティブを削除するには](#bkmk_delete)  
  
-   [パースペクティブをコピーするには](#bkmk_copy)  
  
## <a name="tasks"></a>処理手順  
 パースペクティブを作成するには、 **[パースペクティブ]** ダイアログ ボックスを使用します。このダイアログ ボックスでは、パースペクティブの追加、編集、削除、コピー、表示の各操作を実行できます。 **[パースペクティブ]** ダイアログ ボックスを表示するには、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で **[モデル]** メニューをクリックし、 **[パースペクティブ]**をクリックします。  
  
###  <a name="bkmk_add"></a> パースペクティブを追加するには  
  
-   新しいパースペクティブを追加するには、 **[新しいパースペクティブ]**をクリックします。 パースペクティブに含めるフィールド オブジェクトのチェック ボックスをオンまたはオフにできます。新しいパースペクティブの名前を指定します。  
  
     すべてのフィールド オブジェクトのフィールドが空のパースペクティブを作成した場合、そのパースペクティブを使用するユーザーには空の "フィールドの一覧" が表示されます。 パースペクティブには 1 つ以上のテーブルおよび列を含める必要があります。  
  
###  <a name="bkmk_edit"></a> パースペクティブを編集するには  
  
-   パースペクティブに対する変更は、パースペクティブの列にあるフィールドをオンまたはオフにして、対応するパースペクティブのフィールド オブジェクトを追加または削除することによって行います。  
  
###  <a name="bkmk_rename"></a> パースペクティブの名前を変更するには  
  
-   パースペクティブの列のヘッダー (パースペクティブの名前) にマウス ポインターを合わせると、 **[名前の変更]** ボタンが表示されます。 パースペクティブの名前を変更するには、 **[名前の変更]**をクリックした後、新しい名前を入力するか、既存の名前を編集します。  
  
###  <a name="bkmk_delete"></a> パースペクティブを削除するには  
  
-   パースペクティブの列のヘッダー (パースペクティブの名前) にマウス ポインターを合わせると、 **[削除]** ボタンが表示されます。 パースペクティブを削除するには、 **[削除]** ボタンをクリックし、確認ウィンドウで **[はい]** をクリックします。  
  
###  <a name="bkmk_copy"></a> パースペクティブをコピーするには  
  
-   パースペクティブの列のヘッダーにマウス ポインターを合わせると、 **[コピー]** ボタンが表示されます。 そのパースペクティブのコピーを作成するには、 **[コピー]** ボタンをクリックします。 既存のパースペクティブの右側に、選択したパースペクティブのコピーが新しいパースペクティブとして追加されます。 新しいパースペクティブは、コピーしたパースペクティブの名前を継承しますが、名前の末尾には " *- コピー* " という注釈が追加されます。 たとえば、 *Sales* というパースペクティブのコピーを作成した場合、新しいパースペクティブの名前は " *Sales – コピー*" になります。  
  
## <a name="see-also"></a>「  
 [パースペクティブ (SSAS テーブル)](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [階層 (SSAS テーブル)](../../analysis-services/tabular-models/hierarchies-ssas-tabular.md)  
  
  
