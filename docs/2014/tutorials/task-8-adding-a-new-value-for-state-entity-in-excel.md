---
title: 'タスク 8: Excel で State エンティティに新しい値を追加する |Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: a763d76b-06a3-4d51-9614-01fc9fb1c158
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 831d0b504a65d485413772ee3711e689e29ee2a3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65489707"
---
# <a name="task-8-adding-a-new-value-for-state-entity-in-excel"></a>タスク 8: Excel で State エンティティに新しい値を追加する
  ここでは、Excel で State エンティティの値を追加し、MDS サーバーに変更をパブリッシュします。  
  
1.  下部にある [新規] タブをクリックして、Excel で**ワークシート**を追加します。  
  
     ![Excel - [新規ワークシート] タブ](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-01.jpg "Excel - [新規ワークシート] タブ")  
  
2.  **Excel**で、メニューの [**マスターデータ**] タブをクリックし、リボンの [**エクスプローラーの表示**] をクリックします。  
  
3.  **マスターデータエクスプローラー**で、[**モデル**] の [**仕入先**] を選択します。 2つのエンティティ ( **Supplier**と**State** ) がエンティティリストに表示されます。  
  
4.  一覧で [**状態**] をダブルクリックします。 MDS からの**State**エンティティのすべてのメンバーがワークシートに表示されます。  
  
5.  ここで、末尾に行を追加します。ここで、 **Name**の場合は**ノースカロライナ**、**コード**の場合は**NC**を指定します。 コードの色分けで、新しい/更新済みレコードと他のレコードを区別します。  
  
     ![Excel - 州にノース カロライナを追加](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-02.jpg "Excel - 州にノース カロライナを追加")  
  
6.  リボンの [**発行**] をクリックして、変更を MDS に発行します。  
  
     ![Excel - [マスター データ] タブの [パブリッシュ] ボタン](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-03.jpg "Excel - [マスター データ] タブの [パブリッシュ] ボタン")  
  
7.  [**パブリッシュと注釈**設定] ダイアログボックスで、[**すべての変更に同じ注釈を使用**する] が選択されていることを確認します。 すべての変更についての単一の注釈をここに入力できます。  
  
8.  各変更 (この場合は1つのみ) に注釈を設定するには、[**変更をレビューし、注釈を個別に入力**する] を選択します。  
  
     ![Excel - [パブリッシュと注釈設定] ダイアログ ボックス](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-04.jpg "Excel - [パブリッシュと注釈設定] ダイアログ ボックス")  
  
9. [**パブリッシュ**] をクリックして、データを MDS にパブリッシュします。  
  
10. **州**としての**ノースカロライナ州**の行の**色分け**は、現在、他のレコードと同じであることに注意してください。  
  
11. **省略可能:****マスターデータマネージャー**の**エクスプローラ**を使用して、新しいメンバー (NC) が**State**エンティティに追加されていることを確認します。  
  
12. Excel で、下部にある [ **State** ] ワークシートを右クリックし、[**削除**] をクリックしてワークシートを削除します。 ワークシートを削除しても MDS サーバーからデータは削除されません。  
  
## <a name="next-step"></a>次のステップ  
 [タスク 9: マスター データ マネージャーを使用して派生階層を作成する](../../2014/tutorials/task-9-creating-a-derived-hierarchy-using-master-data-manager.md)  
  
  
