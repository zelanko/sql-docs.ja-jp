---
title: 'タスク 2: Excel の列を DQS ドメインにマップする |Microsoft ドキュメント'
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
ms.topic: article
ms.assetid: f347cc92-950f-4021-b7af-393640dfe821
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: ff48d56555d3eca2bbcb961d753a47d8db38c69e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177003"
---
# <a name="task-2-mapping-excel-columns-to-dqs-domains"></a>タスク 2: DQS ドメインに Excel 列をマップする
    
1.  **[マップ]** ページの **[データ ソース]** で **[Excel ファイル]** を選択します。  
  
2.  をクリックして**参照**[ **Suppliers.xlsx**、] をクリック**開く**です。  
  
3.  選択**IncomingSuppliers$** の**ワークシート**です。  
  
4.  次の表とスクリーン ショットのように列をマップします。 マッピングを作成するときに、**状態**ドメイン をクリックして**列マッピングの追加**リストのすぐ上にあるツールバーのボタンをクリックします。  
  
    > [!TIP]  
    >  使用していない**Supplier ID**列/ドメインをクレンジングします。 使用して、 **Supplier ID**照合アクティビティの後でドメイン。  
  
    |Excel 列|DQS ドメイン|  
    |------------------|----------------|  
    |Supplier Name|Supplier Name|  
    |ContactEmailAddress|Contact Email|  
    |Address Line|Address Line|  
    |City|City|  
    |状態|状態|  
    |国 (をクリックして **(列マッピングの追加) +** 行を追加するツールバー)|Country|  
    |Zip Code|Zip|  
  
     ![ドメインに Excel 列のマッピング](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-01.jpg "ドメインに Excel 列のマッピング")  
  
5.  内のすべての個別ドメインをマップしているため、 **Address Validation**複合ドメインは、複合ドメインは自動的にクレンジング プロセスに参加しています。 をクリックして**複合ドメインの表示と選択**ことを確認するにはボタン、 **Address Validation**複合ドメインが自動的に選択され、をクリックして**OK**です。  
  
     ![複合ドメイン ダイアログ ボックスの表示と選択](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-02.jpg "複合ドメイン ダイアログ ボックスの表示と選択")  
  
6.  をクリックして**次**に切り替えるには、 **Cleanse**ページ。  
  
## <a name="next-step"></a>次の手順  
 [タスク 3: Suppliers ナレッジ ベースに対してデータをクレンジングする](../../2014/tutorials/task-3-cleansing-data-against-the-suppliers-knowledge-base.md)  
  
  