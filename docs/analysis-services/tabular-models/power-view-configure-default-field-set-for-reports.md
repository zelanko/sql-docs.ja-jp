---
title: "Power View レポートの既定のフィールド セットの構成 |Microsoft ドキュメント"
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
f1_keywords:
- ql12.asvs.bidtoolset.deffieldset.f1
ms.assetid: 6836b42f-28b8-4a98-a86d-2c3c109f0189
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 41d0e52ae037e05f60409d891dc1f3f167f7459f
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2018
---
# <a name="power-view---configure-default-field-set-for-reports"></a>Power View - レポートの既定のフィールド セットを構成します。
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
既定のフィールド セットは、列とメジャーの定義済みリストであり、レポート フィールド リストでテーブルを選択したときに、自動的に [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] レポート キャンバスに追加されます。 テーブル モデルの作成者が既定のフィールド セットを作成しておけば、レポートの作成者がレポートのためにモデルを使用するときに、余分な手順を省くことができます。 たとえば、顧客の連絡先情報を参照するほとんどのレポート作成者が、連絡先の名前、通常の電話番号、電子メール アドレス、および会社名を常に確認する必要があることがわかっている場合は、これらの列をあらかじめ選択し、作成者が Customer Contact テーブルをクリックしたときに、これらの列が常にレポート キャンバスに追加されるようにすることができます。  
  
> [!NOTE]  
>  既定のフィールド セットは、 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]でデータ モデルとして使用されるテーブル モデルのみに適用されます。 既定のフィールド セットは、Excel ピボット レポートではサポートされません。  
  
## <a name="creating-a-default-field-set"></a>既定のフィールド セットの作成  
 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]で特定のテーブルが選択されたときに、どのフィールドが既定で含まれるかを決定できます。 フィールドが一覧に表示される順序も決定できます。 既定のフィールド セットを指定するには、テーブル モデル プロジェクトにレポート プロパティを設定します。  
  
#### <a name="to-add-a-default-field-set"></a>既定のフィールド セットを追加するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、既定のフィールド セットを構成する対象のテーブル (タブ) をクリックします。  
  
2.  **[プロパティ]** ウィンドウの **既定のフィールド セット** プロパティで、 **[クリックして編集]**をクリックします。  
  
3.  [既定のフィールド セット] ダイアログで、フィールドを 1 つ以上選択します。 メジャーを含め、テーブル内の任意のフィールドを選択できます。 Shift キーを押しながら範囲を選択するか、Ctrl キーを押しながら個別のフィールドを選択します。  
  
4.  **[追加]** をクリックして、選択したフィールドを既定のフィールド セットに追加します。  
  
5.  上矢印ボタンと下矢印ボタンを使用して、フィールド リストに順番を指定します。 フィールドは、フィールド リストに定義された順番でレポートに追加されます。  
  
6.  ブックの他のテーブルについて、この手順を繰り返します。  
  
## <a name="next-step"></a>次の手順  
 既定のフィールド セットを作成した後、既定のラベル、既定の画像、既定のグループ動作、または同じ値を含む行を 1 行にグループ化するか個別に表示するかを指定することによって、レポートのデザイン作業にさらに影響を与えることができます。 詳細については、次を参照してください。 [Power View レポート用のテーブル動作プロパティの構成](../../analysis-services/tabular-models/power-view-configure-table-behavior-properties-for-reports.md)です。  
  
  
