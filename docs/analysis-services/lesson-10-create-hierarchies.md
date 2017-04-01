---
title: "レッスン 10: 階層の作成 | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 1e2561d3-4890-4495-a9cd-84eb88508938
caps.latest.revision: 23
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# レッスン 10: 階層の作成
このレッスンでは、階層を作成します。 階層は、複数のレベルに分類された列のグループです。たとえば、Geography という階層に、Country、State、County、および City というサブレベルを含めることができます。 階層は、あるレポート クライアント アプリケーション フィールドの一覧の他の列とは分けて表示できるため、クライアントのユーザーは簡単に移動し、レポートに含めることができます。 詳細については、[「階層 (SSAS テーブル)」](../analysis-services/tabular-models/hierarchies-ssas-tabular.md) を参照してください。  
  
階層を作成するには、*ダイアグラム ビュー*のモデル デザイナーを使用します。 階層の作成と管理は、データ ビューのモデル デザイナーではサポートされていません。  
  
このレッスンの推定所要時間: **20 分**  
  
## 前提条件  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンの実習を行う前に、前のレッスン [「レッスン 9: パースペクティブの作成」](../Topic/Lesson%209:%20Create%20Perspectives.md) を完了している必要があります。  
  
## 階層を作成する  
  
#### Product テーブル内に Category 階層を作成するには  
  
1.  モデル デザイナーで、**[モデル]** メニューをクリックし、**[モデル ビュー]** をポイントし、**[ダイアグラム ビュー]** をクリックします。  
  
  
  
2.  **Product** テーブルをクリックし、**[階層の作成]** をクリックします。 テーブル ウィンドウの下部に新しい階層が表示されます。  
  
3.  階層名で、「**Category**」と入力して階層名を変更し、Enter キーを押します。  
  
4.  **Product** テーブルで、**Product Category Name** 列をクリックして **Category** 階層にドラッグし、**Category** の上で離します。  
  
5.  **Category** 階層で、**Product Category Name** 列を右クリックし、**[名前の変更]** をクリックして「**Category**」と入力します。  
  
    > [!NOTE]  
    > 階層内の列の名前を変更しても、テーブル内のその列の名前は変更されません。 階層内の列は、テーブル内の列の 1 つの表現形態に過ぎません。  
  
6.  **Product** テーブルで、**Product Subcategory Name** 列をクリックし、**Category** 階層までドラッグします。  
  
7.  **Product Subcategory Name** を **Subcategory** に名前変更します。  
  
8.  **Model Name** 列と **Product Name** 列を (この順序で) クリックしてドラッグして、**Product Subcategory Name** 列の下に配置します。 これらの列の名前を、それぞれ **Model** と **Product** に変更します。  
  
#### Date テーブル内に階層を作成するには  
  
1.  モデル デザイナーで、**Date** テーブルをクリックし、**[階層の作成]** をクリックします。  
  
2.  階層の名前を **Calendar** に変更します。  
  
3.  次の列を (順序どおりに) 追加し、名前を次のように変更します。  
  
    |列|変更後の名前|  
    |----------|--------------|  
    |Calendar Year|年|  
    |Calendar Semester|Semester|  
    |Calendar Quarter|Quarter|  
    |Month Calendar|Month|  
    |Day Of Month|日|  
  
4.  **Date** テーブルで上記の手順を繰り返し、次の列を含んだ **Fiscal** 階層を作成します。  
  
    |列|変更後の名前|  
    |----------|--------------|  
    |Fiscal Year|年|  
    |Fiscal Semester|Semester|  
    |Fiscal Quarter|Quarter|  
    |Month Calendar|Month|  
    |Day Of Month|日|  
  
5.  最後に、**Date** テーブルで上記の手順を繰り返し、次の列を含んだ **Production Calendar** 階層を作成します。  
  
    |列|変更後の名前|  
    |----------|--------------|  
    |Calendar Year|年|  
    |Week Number Of Year|Week|  
    |Day Of Week|日|  
  
## 次の手順  
このチュートリアルを続行するには、次のレッスン [「レッスン 11: パーティションの作成」](../analysis-services/lesson-11-create-partitions.md) に進んでください。  
  
  
  
