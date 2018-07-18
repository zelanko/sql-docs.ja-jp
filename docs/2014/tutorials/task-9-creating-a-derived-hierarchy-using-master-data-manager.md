---
title: 'タスク 9: マスター データ マネージャーを使用して派生階層を作成する |Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3bd2ec05-933f-4947-b1fe-c9226961eb7d
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 22aba36efffe3b4e15d358e6077bb6b58e7aa328
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37273588"
---
# <a name="task-9-creating-a-derived-hierarchy-using-master-data-manager"></a>タスク 9: マスター データ マネージャーを使用して派生階層を作成する
  ここでは、マスター データ マネージャーを使用して派生階層を作成します。 この派生階層は、ドメイン ベースの属性リレーションシップから派生した、 **Supplier**と**状態**エンティティ。  
  
1.  メイン ページに切り替えます**マスター データ マネージャー**をクリックして**SQL Server 2012 マスター データ サービス**ページの上部にあります。  
  
2.  クリックして**システム管理**で、**管理タスク**セクション。  
  
3.  マウス ポインターを置きます**管理**をクリックし、メニュー バーで**派生階層**します。  
  
     ![[管理] メニュー - 派生階層が選択されている](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-01.jpg "管理 メニュー - 派生階層の選択")  
  
4.  クリックして**派生階層の追加 (+)** ツールバーのボタンをクリックします。  
  
     ![派生階層 ボタンを追加](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-02.jpg "派生階層のボタンの追加")  
  
5.  型**SuppliersInState**の**派生階層名**します。  
  
6.  クリックして**保存**ツールバーのボタンをクリックします。  
  
     ![派生階層 ボタンの保存](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-03.jpg "派生階層 ボタンの保存")  
  
7.  ドラッグ**Supplier**から**使用できるレベル: SuppliersInState**に**現在のレベル: SuppliersInState**します。  
  
     ![使用できるエンティティと階層を現在のレベルに](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-04.jpg "使用できるエンティティと階層を現在のレベル")  
  
8.  ドラッグ**状態**から**使用できるレベル: SuppliersInState**に**現在のレベル: SuppliersInState**します。 画面があります**現在のレベル**次の図に示すようにします。  
  
     ![現在のレベルと派生階層のプレビュー](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-05.jpg "現在のレベルと派生階層のプレビュー")  
  
9. **プレビュー**ウィンドウで、展開**NY New York}** と前の図のように、状態にある 1 つの仕入先を表示する必要があります。  
  
10. メイン ページに切り替えます**マスター データ マネージャー**をクリックして**SQL Server 2012 マスター データ サービス**ページの上部にあります。  
  
11. **[エクスプローラー]** をクリックします。  
  
12. マウス ポインターを置きます**階層**クリック**派生: SuppliersInState**します。  
  
     ![階層 - 派生: SuppliersInState メニュー](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-06.jpg "階層 - 派生: SuppliersInState メニュー")  
  
13. いずれかをクリックして**状態**内のノード、**ツリー ビュー**と右側のウィンドウにその州の仕入先を表示する必要があります。  
  
     ![派生階層エクスプ ローラーで](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-07.jpg "派生階層エクスプ ローラー")  
  
## <a name="next-step"></a>次の手順  
 [レッスン 5: SSIS を使用してクレンジングと照合を自動化する](../../2014/tutorials/lesson-5-automating-the-cleansing-and-matching-using-ssis.md)  
  
  
