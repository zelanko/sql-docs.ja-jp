---
title: 'レッスン 10: 階層を作成する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1e2561d3-4890-4495-a9cd-84eb88508938
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: eb70d7d495d88ee62e98bf27f2b92bf569c98387
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66078190"
---
# <a name="lesson-10-create-hierarchies"></a>レッスン 10: 階層の作成
  このレッスンでは、階層を作成します。 階層は、レベルに分類された列のグループです。たとえば、Geography (地理的な場所) 階層には、Country (国)、State (州)、County (郡)、City (市) などの下位階層があります。 階層は、レポートするクライアント アプリケーションのフィールド リストにある他の列とは別に表示できます。階層を使用すれば、クライアント ユーザーが列をより簡単に探してレポートに含めることができます。 詳細については、[「階層 (SSAS テーブル)」](tabular-models/hierarchies-ssas-tabular.md) を参照してください。  
  
 階層を作成するには、 *ダイアグラム ビュー*のモデル デザイナーを使用します。 階層の作成と管理は、データ ビューのモデル デザイナーではサポートされていません。  
  
 このレッスンの推定所要時間: **20 分**  
  
## <a name="prerequisites"></a>前提条件  
 このトピックは、表形式モデルのチュートリアルの一部であり、順番に従って実行する必要があります。 このレッスンの実習を行う前に、前のレッスン [「レッスン 9: パースペクティブの作成」](lesson-8-create-perspectives.md)を完了している必要があります。  
  
## <a name="create-hierarchies"></a>階層を作成する  
  
#### <a name="to-create-a-category-hierarchy-in-the-product-table"></a>Product テーブル内に Category 階層を作成するには  
  
1.  モデルデザイナーで、 `Model`メニューをクリックし、[**モデルビュー**] をポイントし、[**ダイアグラムビュー**] をクリックします。  
  
    > [!TIP]  
    >  モデル デザイナーの右上にあるミニマップ コントロールを使用すると、ダイアグラム ビューでのオブジェクトの表示方法を変更できます。 ダイアグラム ビューでモデルを移動した場合、プロジェクトを保存する際にそのビューが保持されます。  
  
2.  モデルデザイナーで`Product`テーブルを右クリックし、[**階層の作成**] をクリックします。 テーブル ウィンドウの一番下に、新しい階層が表示されます。  
  
3.  階層名に「」と入力`Category`して階層の名前を変更し、enter キーを押します。  
  
4.  テーブルで、 **Product Category Name**列をクリックし、それを`Category`階層にドラッグして、 `Category`名前の上にリリースします。 `Product`  
  
5.  階層で、 **Product Category Name**列を右クリックし、[名前の**変更**] をクリックし`Category`て「」と入力します。 `Category`  
  
    > [!NOTE]  
    >  階層内で列の名前を変更しても、テーブル内でその列の名前は変更されません。 階層内の列は、テーブル内の列のみを表しています。  
  
6.  テーブルで、 **Product サブカテゴリ名**列を右クリックし、コンテキストメニューで [**階層に追加**] をポイントして、[] `Category`をクリックします。 `Product`  
  
7.  **製品サブカテゴリ名**を`Subcategory`に変更します。  
  
8.  クリックしてドラッグするか、コンテキストメニューの [**階層に追加**] コマンドを使用して、**モデル名**と**製品名**の列を順番に追加し、 **product サブカテゴリ名**列の下に配置します。 これらの列`Model` `Product`の名前をそれぞれ変更します。  
  
#### <a name="to-create-hierarchies-in-the-date-table"></a>Date テーブル内に階層を作成するには  
  
1.  モデル デザイナーで、 **Date** テーブルをクリックし、 **[階層の作成]** をクリックします。  
  
2.  階層の名前を **Calendar**に変更します。  
  
3.  次の列を (順序どおりに) 追加し、名前を次のように変更します。  
  
    |列|変更後の名前|  
    |------------|----------------|  
    |Calendar Year|年|  
    |Calendar Semester|Semester|  
    |Calendar Quarter|Quarter|  
    |Month Calendar|月|  
    |Day Of Month|日|  
  
4.  
  **Date** テーブルで上記の手順を繰り返し、次の列を含んだ **Fiscal** 階層を作成します。  
  
    |列|変更後の名前|  
    |------------|----------------|  
    |Fiscal Year|年|  
    |Fiscal Semester|Semester|  
    |Fiscal Quarter|Quarter|  
    |Month Calendar|月|  
    |Day Of Month|日|  
  
5.  最後に、 **Date** テーブルで上記の手順を繰り返し、次の列を含んだ **Production Calendar** 階層を作成します。  
  
    |列|変更後の名前|  
    |------------|----------------|  
    |Calendar Year|年|  
    |Week Number Of Year|週|  
    |Day Of Week|日|  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルを続行するには、次のレッスン [「レッスン 11: パーティションの作成」](lesson-10-create-partitions.md)に進んでください。  
  
  
