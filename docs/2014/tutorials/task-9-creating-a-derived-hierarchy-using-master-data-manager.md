---
title: 'タスク 9: マスター データ マネージャーを使用して派生階層を作成する |Microsoft ドキュメント'
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
ms.topic: article
ms.assetid: 3bd2ec05-933f-4947-b1fe-c9226961eb7d
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 35584d33afac7a2a8f74abd013288a974cade512
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36179005"
---
# <a name="task-9-creating-a-derived-hierarchy-using-master-data-manager"></a>タスク 9: マスター データ マネージャーを使用して派生階層を作成する
  ここでは、マスター データ マネージャーを使用して派生階層を作成します。 この派生階層は、ドメイン ベースの属性リレーションシップから派生した、**業者**と**状態**エンティティです。  
  
1.  メイン ページに切り替えます**マスター データ マネージャー**  をクリックして**SQL Server 2012 マスター データ サービス**ページの上部にあります。  
  
2.  をクリックして**システム管理**で、**管理タスク**セクションです。  
  
3.  マウス ポインターを合わせる**管理**クリックしてメニュー バーで**派生階層**です。  
  
     ![[管理] メニューで選択されている派生階層](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-01.jpg "メニュー - 選択した派生階層の管理")  
  
4.  をクリックして**派生階層の追加 (+)** ツールバーのボタンをクリックします。  
  
     ![派生階層 ボタンを追加](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-02.jpg "派生階層 ボタンの追加")  
  
5.  型**SuppliersInState**の**派生階層名**です。  
  
6.  をクリックして**保存**ツールバーのボタンをクリックします。  
  
     ![保存派生階層ボタン](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-03.jpg "保存派生階層 ボタン")  
  
7.  ドラッグ**業者**から**使用できるレベル: SuppliersInState**に**現在のレベル: SuppliersInState**です。  
  
     ![使用できるエンティティと階層を現在のレベル](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-04.jpg "使用できるエンティティと階層を現在のレベル")  
  
8.  ドラッグ**状態**から**使用できるレベル: SuppliersInState**に**現在のレベル: SuppliersInState**です。 画面が必要**現在のレベル**次の図に示すようにします。  
  
     ![現在のレベルと派生階層のプレビュー](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-05.jpg "現在のレベルと派生階層のプレビュー")  
  
9. **プレビュー**ウィンドウで、展開**NY New York}** と前の図のように、状態にある 1 つの仕入先を表示する必要があります。  
  
10. メイン ページに切り替えます**マスター データ マネージャー**  をクリックして**SQL Server 2012 マスター データ サービス**ページの上部にあります。  
  
11. **[エクスプローラー]** をクリックします。  
  
12. マウス ポインターを合わせる**階層** をクリック**Derived:suppliersinstate**です。  
  
     ![階層 - 派生: SuppliersInState メニュー](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-06.jpg "階層 - 派生: SuppliersInState メニュー")  
  
13. いずれかをクリックして**状態**内のノード、**ツリー ビュー**と右側のペインにその州の仕入先が表示されます。  
  
     ![派生階層エクスプ ローラーで](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-07.jpg "派生階層エクスプ ローラー")  
  
## <a name="next-step"></a>次の手順  
 [レッスン 5: SSIS を使用してクレンジングと照合を自動化する](../../2014/tutorials/lesson-5-automating-the-cleansing-and-matching-using-ssis.md)  
  
  