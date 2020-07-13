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
ms.openlocfilehash: b6b57669eed30abf010b9d2775950bf0cd6c6e67
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84542154"
---
# <a name="lesson-10-create-hierarchies"></a>レッスン 10: 階層を作成する
  このレッスンでは、階層を作成します。 階層は、複数のレベルに分類された列のグループです。たとえば、Geography という階層に、Country、State、County、および City というサブレベルを含めることができます。 階層は、レポートするクライアント アプリケーションのフィールド リストにある他の列とは別に表示できます。階層を使用すれば、クライアント ユーザーが列をより簡単に探してレポートに含めることができます。 詳細については、[「階層 (SSAS テーブル)」](tabular-models/hierarchies-ssas-tabular.md) を参照してください。  
  
 階層を作成するには、 *ダイアグラム ビュー*のモデル デザイナーを使用します。 階層の作成と管理は、データ ビューのモデル デザイナーではサポートされていません。  
  
 このレッスンの推定所要時間: **20 分**  
  
## <a name="prerequisites"></a>前提条件  
 このトピックは、表形式モデルのチュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンの実習を行う前に、前のレッスン [「レッスン 9: パースペクティブの作成」](lesson-8-create-perspectives.md)を完了している必要があります。  
  
## <a name="create-hierarchies"></a>階層を作成する  
  
#### <a name="to-create-a-category-hierarchy-in-the-product-table"></a>Product テーブル内に Category 階層を作成するには  
  
1.  モデルデザイナーで、メニューをクリックし、[ `Model` **モデルビュー**] をポイントし、[**ダイアグラムビュー**] をクリックします。  
  
    > [!TIP]  
    >  モデル デザイナーの右上にあるミニマップ コントロールを使用すると、ダイアグラム ビューでのオブジェクトの表示方法を変更できます。 ダイアグラム ビューでモデルを移動した場合、プロジェクトを保存する際にそのビューが保持されます。  
  
2.  モデルデザイナーでテーブルを右クリックし、 `Product` [**階層の作成**] をクリックします。 テーブル ウィンドウの下部に新しい階層が表示されます。  
  
3.  階層名に「」と入力して階層の名前を変更し、enter `Category` キーを押します。  
  
4.  テーブルで、 `Product` **Product Category Name**列をクリックし、それを階層にドラッグして、 `Category` 名前の上にリリースし `Category` ます。  
  
5.  階層で、 `Category` **Product Category Name**列を右クリックし、[名前の**変更**] をクリックして「」と入力し `Category` ます。  
  
    > [!NOTE]  
    >  階層内の列の名前を変更しても、テーブル内のその列の名前は変更されません。 階層内の列は、テーブル内の列の 1 つの表現形態に過ぎません。  
  
6.  テーブルで、 `Product` **Product サブカテゴリ名**列を右クリックし、コンテキストメニューで [**階層に追加**] をポイントして、[] をクリックし `Category` ます。  
  
7.  **製品サブカテゴリ名**をに変更 `Subcategory` します。  
  
8.  クリックしてドラッグするか、コンテキストメニューの [**階層に追加**] コマンドを使用して、**モデル名**と**製品名**の列を順番に追加し、 **product サブカテゴリ名**列の下に配置します。 これらの列の名前をそれぞれ変更し `Model` `Product` ます。  
  
#### <a name="to-create-hierarchies-in-the-date-table"></a>Date テーブル内に階層を作成するには  
  
1.  モデル デザイナーで、 **Date** テーブルをクリックし、 **[階層の作成]** をクリックします。  
  
2.  階層の名前を **Calendar**に変更します。  
  
3.  次の列を (順序どおりに) 追加し、名前を次のように変更します。  
  
    |Column|変更後の名前|  
    |------------|----------------|  
    |Calendar Year|年|  
    |Calendar Semester|Semester|  
    |Calendar Quarter|Quarter|  
    |Month Calendar|Month|  
    |Day Of Month|日間|  
  
4.  **Date** テーブルで上記の手順を繰り返し、次の列を含んだ **Fiscal** 階層を作成します。  
  
    |Column|変更後の名前|  
    |------------|----------------|  
    |Fiscal Year|年|  
    |Fiscal Semester|Semester|  
    |Fiscal Quarter|Quarter|  
    |Month Calendar|Month|  
    |Day Of Month|日間|  
  
5.  最後に、 **Date** テーブルで上記の手順を繰り返し、次の列を含んだ **Production Calendar** 階層を作成します。  
  
    |Column|変更後の名前|  
    |------------|----------------|  
    |Calendar Year|年|  
    |Week Number Of Year|週|  
    |Day Of Week|日間|  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルを続行するには、次のレッスン [「レッスン 11: パーティションの作成」](lesson-10-create-partitions.md)に進んでください。  
  
  
