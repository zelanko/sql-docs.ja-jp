---
title: 'タスク 2: Excel の列を DQS ドメインにマップする |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f347cc92-950f-4021-b7af-393640dfe821
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 89be07ed1cdd07fc8cd923d9672147b87a165d71
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37202032"
---
# <a name="task-2-mapping-excel-columns-to-dqs-domains"></a>タスク 2: DQS ドメインに Excel 列をマップする
    
1.  **[マップ]** ページの **[データ ソース]** で **[Excel ファイル]** を選択します。  
  
2.  クリックして**参照**を選択します**Suppliers.xlsx**、 をクリック**オープン**します。  
  
3.  選択**IncomingSuppliers$** の**ワークシート**します。  
  
4.  次の表とスクリーン ショットのように列をマップします。 マッピングを作成するときに、**状態**ドメイン、 をクリックして**列マッピングの追加**リストのすぐ上にあるツールバーのボタンをクリックします。  
  
    > [!TIP]  
    >  使用していない**Supplier ID**列/ドメインをクレンジングします。 使用する、 **Supplier ID**照合アクティビティの後でドメイン。  
  
    |Excel 列|DQS ドメイン|  
    |------------------|----------------|  
    |Supplier Name|Supplier Name|  
    |ContactEmailAddress|Contact Email|  
    |Address Line|Address Line|  
    |City|City|  
    |状態|状態|  
    |国 (をクリックして **(列マッピングの追加) +** 行を追加するツールバー)|Country|  
    |Zip Code|Zip|  
  
     ![ドメインに Excel 列のマッピング](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-01.jpg "のドメインに Excel 列のマッピング")  
  
5.  内の個々 のすべてのドメインをマップしているため、 **Address Validation**複合ドメインは、複合ドメインは自動的にクレンジング プロセスに参加します。 をクリックして**複合ドメインの表示/選択**ボタンをクリックしている、 **Address Validation**複合ドメインが自動的に選択し、順にクリックします**OK**。  
  
     ![複合ドメイン ダイアログ ボックスの表示と選択](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-02.jpg "複合ドメインの表示と選択 ダイアログ ボックス")  
  
6.  をクリックして**次**に切り替える、 **Cleanse**ページ。  
  
## <a name="next-step"></a>次の手順  
 [タスク 3: Suppliers ナレッジ ベースに対してデータをクレンジングする](../../2014/tutorials/task-3-cleansing-data-against-the-suppliers-knowledge-base.md)  
  
  
