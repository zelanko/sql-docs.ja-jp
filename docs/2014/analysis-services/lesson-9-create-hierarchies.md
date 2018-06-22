---
title: 'レッスン 10: 階層の作成 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1e2561d3-4890-4495-a9cd-84eb88508938
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.openlocfilehash: ea741676f07020291c2aa94d130c2f595a50f323
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36071065"
---
# <a name="lesson-10-create-hierarchies"></a>レッスン 10: 階層の作成
  このレッスンでは、階層を作成します。 階層は、複数のレベルに分類された列のグループです。たとえば、Geography という階層に、Country、State、County、および City というサブレベルを含めることができます。 階層は、あるレポート クライアント アプリケーション フィールドの一覧の他の列とは分けて表示できるため、クライアントのユーザーは簡単に移動し、レポートに含めることができます。 詳細については、[「階層 (SSAS テーブル)」](tabular-models/hierarchies-ssas-tabular.md) を参照してください。  
  
 階層を作成するには、*ダイアグラム ビュー*のモデル デザイナーを使用します。 階層の作成と管理は、データ ビューのモデル デザイナーではサポートされていません。  
  
 このレッスンの推定所要時間: **20 分**  
  
## <a name="prerequisites"></a>前提条件  
 このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンの実習を行う前に、前のレッスン [「レッスン 9: パースペクティブの作成」](lesson-8-create-perspectives.md) を完了している必要があります。  
  
## <a name="create-hierarchies"></a>階層を作成する  
  
#### <a name="to-create-a-category-hierarchy-in-the-product-table"></a>Product テーブル内に Category 階層を作成するには  
  
1.  モデル デザイナーでは、をクリックして、`Model`メニューから、をポイント**モデル ビュー**、クリックして**ダイアグラム ビュー**です。  
  
    > [!TIP]  
    >  モデル デザイナーの右上にあるミニマップ コントロールを使用すると、ダイアグラム ビューでのオブジェクトの表示方法を変更できます。 ダイアグラム ビューでモデルを移動した場合、プロジェクトを保存する際にそのビューが保持されます。  
  
2.  モデル デザイナー内を右クリックし、`Product`テーブル、およびクリックして**階層の作成**です。 テーブル ウィンドウの下部に新しい階層が表示されます。  
  
3.  」と入力して、階層の名前を変更、階層名に`Category`、ENTER キーを押します。  
  
4.  `Product`テーブルで、をクリックして、 **Product Category Name**列で、ドラッグ、`Category`階層、およびの上に、リリース、`Category`名。  
  
5.  `Category`階層を右クリックし、 **Product Category Name**列で、をクリックして**の名前を変更**、し、入力`Category`です。  
  
    > [!NOTE]  
    >  階層内の列の名前を変更しても、テーブル内のその列の名前は変更されません。 階層内の列は、テーブル内の列の 1 つの表現形態に過ぎません。  
  
6.  `Product`テーブルを右クリックして、 **Product Subcategory Name**列で、コンテキスト メニューのをポイント**階層を追加する**、順にクリック`Category`です。  
  
7.  名前を変更**Product Subcategory Name**に`Subcategory`です。  
  
8.  クリック アンド ドラッグを使用するかを使用して、**階層を追加する**コンテキスト メニューにコマンドを追加、**モデル名**と**製品名**(順序) で列の下に配置し、**Product Subcategory Name**列です。 これらの列の名前を変更`Model`と`Product`、それぞれします。  
  
#### <a name="to-create-hierarchies-in-the-date-table"></a>Date テーブル内に階層を作成するには  
  
1.  モデル デザイナーで、 **Date** テーブルをクリックし、 **[階層の作成]** をクリックします。  
  
2.  階層の名前を **Calendar**に変更します。  
  
3.  次の列を (順序どおりに) 追加し、名前を次のように変更します。  
  
    |[列]|変更後の名前|  
    |------------|----------------|  
    |Calendar Year|年|  
    |Calendar Semester|Semester|  
    |Calendar Quarter|Quarter|  
    |Month Calendar|Month|  
    |Day Of Month|日|  
  
4.  **Date** テーブルで上記の手順を繰り返し、次の列を含んだ **Fiscal** 階層を作成します。  
  
    |[列]|変更後の名前|  
    |------------|----------------|  
    |Fiscal Year|年|  
    |Fiscal Semester|Semester|  
    |Fiscal Quarter|Quarter|  
    |Month Calendar|Month|  
    |Day Of Month|日|  
  
5.  最後に、 **Date** テーブルで上記の手順を繰り返し、次の列を含んだ **Production Calendar** 階層を作成します。  
  
    |[列]|変更後の名前|  
    |------------|----------------|  
    |Calendar Year|年|  
    |Week Number Of Year|Week|  
    |Day Of Week|日|  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルを続行するには、次のレッスン [「レッスン 11: パーティションの作成」](lesson-10-create-partitions.md) に進んでください。  
  
  