---
title: 'タスク 9: マスターデータマネージャー | を使用して派生階層を作成するMicrosoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3bd2ec05-933f-4947-b1fe-c9226961eb7d
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 7cb2f12115e3fe743c49c2f7e69f765da4501ba2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65489547"
---
# <a name="task-9-creating-a-derived-hierarchy-using-master-data-manager"></a>タスク 9: マスター データ マネージャーを使用して派生階層を作成する
  ここでは、マスター データ マネージャーを使用して派生階層を作成します。 この派生階層は、 **Supplier**エンティティと**State**エンティティ間のドメインベースの属性リレーションシップから派生します。  
  
1.  ページの上部にある**SQL Server 2012 マスターデータサービス**をクリックして**マスターデータマネージャー**のメインページに切り替えます。  
  
2.  [**管理タスク**] セクションで [**システム管理**] をクリックします。  
  
3.  メニューバーの [**管理**] の上にマウスポインターを移動し、[**派生階層**] をクリックします。  
  
     ![[管理] メニュー - 派生階層が選択された状態](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-01.jpg "[管理] メニュー - 派生階層が選択された状態")  
  
4.  ツールバーの [**派生階層の追加] (+)** ボタンをクリックします。  
  
     ![[派生階層の追加] ボタン](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-02.jpg "[派生階層の追加] ボタン")  
  
5.  **派生階層名**として「 **SuppliersInState** 」と入力します。  
  
6.  ツールバーの [**保存**] ボタンをクリックします。  
  
     ![[派生階層の保存] ボタン](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-03.jpg "[派生階層の保存] ボタン")  
  
7.  [**使用可能なレベル: SuppliersInState**から**現在のレベル: SuppliersInState**に**仕入先**をドラッグします。  
  
     ![使用できるエンティティと階層から現在のレベルへ](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-04.jpg "使用できるエンティティと階層から現在のレベルへ")  
  
8.  [**使用可能なレベル: SuppliersInState**から**現在のレベル: SuppliersInState**に**状態**をドラッグします。 画面には、次の図に示すように、**現在のレベル**が表示されます。  
  
     ![現在のレベルと、派生階層のプレビュー](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-05.jpg "現在のレベルと、派生階層のプレビュー")  
  
9. **プレビュー**ウィンドウで、[ **NY {New ニューヨーク}** ] を展開すると、前の図に示すように、その状態に1つの仕入先が表示されます。  
  
10. ページの上部にある**SQL Server 2012 マスターデータサービス**をクリックして**マスターデータマネージャー**のメインページに切り替えます。  
  
11. 
  **[エクスプローラー]** をクリックします。  
  
12. **階層**上にマウスポインターを置き、[ **Derived: SuppliersInState**] をクリックします。  
  
     ![階層 - 派生: SuppliersInState メニュー](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-06.jpg "階層 - 派生: SuppliersInState メニュー")  
  
13. **ツリービュー**の任意の**状態**ノードをクリックすると、その状態にある仕入先が右ペインに表示されます。  
  
     ![エクスプローラーでの派生階層](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-07.jpg "エクスプローラーでの派生階層")  
  
## <a name="next-step"></a>次のステップ  
 [レッスン 5: SSIS を使用してクレンジングと照合を自動化する](../../2014/tutorials/lesson-5-automating-the-cleansing-and-matching-using-ssis.md)  
  
  
