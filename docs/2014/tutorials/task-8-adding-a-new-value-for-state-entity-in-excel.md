---
title: 'タスク 8: Excel で State エンティティの新しい値を追加する |Microsoft ドキュメント'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a763d76b-06a3-4d51-9614-01fc9fb1c158
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: db2eaccd4d9b344cbc1b7c25b6fec940ff9c77a9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36175058"
---
# <a name="task-8-adding-a-new-value-for-state-entity-in-excel"></a>タスク 8: Excel で State エンティティに新しい値を追加する
  ここでは、Excel で State エンティティの値を追加し、MDS サーバーに変更をパブリッシュします。  
  
1.  追加、**作業シート**下部にある新しいタブをクリックして Excel でします。  
  
     ![Excel - 新しいワークシートのタブ](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-01.jpg "Excel - [新規ワークシート] タブ")  
  
2.  **Excel**、] をクリックして、**マスター データ**タブ、メニューをクリックして **[エクスプ ローラーの**リボン上。  
  
3.  **マスター データ エクスプ ローラー** **Suppliers**の**モデル**です。 2 つのエンティティを参照してください:**業者**と**状態**がエンティティ リストにします。  
  
4.  ダブルクリックして**状態**一覧にします。 すべてのメンバー、**状態**がワークシートに MDS からエンティティを表示する必要があります。  
  
5.  ここで、次の値で、末尾に行を追加:**ノース カロライナ**の**名前**と**NC**の**コード**です。 コードの色分けで、新しい/更新済みレコードと他のレコードを区別します。  
  
     ![Excel - 状態にノース カロライナを追加](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-02.jpg "Excel の状態にノース カロライナを追加")  
  
6.  をクリックして**発行**MDS に変更をパブリッシュするには、リボン上。  
  
     ![Excel - [マスター データ] タブのボタンを発行](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-03.jpg "Excel - [マスター データ] タブのボタンの発行")  
  
7.  **パブリッシュと注釈設定** ダイアログ ボックスで、ことに注意して、**同じ注釈を使用して、すべての変更の**が選択されています。 すべての変更についての単一の注釈をここに入力できます。  
  
8.  選択**変更を確認し、注釈を個別に提供**各変更の注釈 (ここでは、1 つのみ) を提供するオプションです。  
  
     ![Excel - [パブリッシュし、注釈設定] ダイアログ ボックス](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-04.jpg "Excel - [パブリッシュし、注釈設定] ダイアログ ボックス")  
  
9. をクリックして**発行**を MDS にデータを発行します。  
  
10. 注意して**カラー コーディング**を持つ行の**ノース カロライナ**として、**状態**は他のレコードと同じようになりました。  
  
11. **省略可能:** に新しいメンバー (NC) が追加されたことを確認して、**状態**エンティティを使用して、**エクスプ ローラー**で**マスター データ マネージャー**です。  
  
12. Excel を右クリックし、**状態**下とクリックにワークシート**削除**ワークシートを削除します。 ワークシートを削除しても MDS サーバーからデータは削除されません。  
  
## <a name="next-step"></a>次の手順  
 [タスク 9: マスター データ マネージャーを使用して派生階層を作成する](../../2014/tutorials/task-9-creating-a-derived-hierarchy-using-master-data-manager.md)  
  
  