---
title: 'タスク 2: DQS ドメインに Excel 列をマップする |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: f347cc92-950f-4021-b7af-393640dfe821
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 29d45e06dcd3e67af3abbc6b356d44877e40f46b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65484703"
---
# <a name="task-2-mapping-excel-columns-to-dqs-domains"></a>タスク 2: DQS ドメインに Excel 列をマップする
    
1.  
  **[マップ]** ページの **[データ ソース]** で **[Excel ファイル]** を選択します。  
  
2.  [**参照**] をクリックし、[**仕入先 .xlsx**] を選択して、[**開く**] をクリックします。  
  
3.  **ワークシート**の [ **IncomingSuppliers $** ] を選択します。  
  
4.  次の表とスクリーン ショットのように列をマップします。 **状態**ドメインのマッピングを作成する場合は、一覧のすぐ上にあるツールバーの [**列マッピングの追加**] ボタンをクリックします。  
  
    > [!TIP]  
    >  クレンジングに**SUPPLIER ID**列またはドメインを使用していません。 この照合アクティビティでは、後で**SUPPLIER ID**ドメインを使用します。  
  
    |Excel 列|DQS ドメイン|  
    |------------------|----------------|  
    |Supplier Name|Supplier Name|  
    |ContactEmailAddress|連絡先のメール アドレス|  
    |Address Line|Address Line|  
    |City|City|  
    |State|State|  
    |国 ([ **+ (列マッピングの追加)** ] ツールバーをクリックして行を追加します)|Country|  
    |Zip Code|Zip|  
  
     ![ドメインへの Excel 列のマッピング](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-01.jpg "ドメインへの Excel 列のマッピング")  
  
5.  **Address Validation**複合ドメイン内の個々のドメインをすべてマップしているため、複合ドメインは自動的にクレンジングプロセスに参加します。 [**複合ドメインの表示と選択**] ボタンをクリックして、 **Address Validation**複合ドメインが自動的に選択されていることを確認し、[ **OK**] をクリックします。  
  
     ![[複合ドメインの表示と選択] ダイアログ ボックス](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-02.jpg "[複合ドメインの表示と選択] ダイアログ ボックス")  
  
6.  [**次へ**] をクリックして、[**クレンジング**] ページに移動します。  
  
## <a name="next-step"></a>次のステップ  
 [タスク 3: Suppliers ナレッジ ベースに対してデータをクレンジングする](../../2014/tutorials/task-3-cleansing-data-against-the-suppliers-knowledge-base.md)  
  
  
