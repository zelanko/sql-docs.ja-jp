---
title: 'タスク 5: Excel からドメインベースの属性を作成する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 07cbc624-2c6b-4568-96e4-f18663a05d80
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: f7e88065ff66ea953d0a91ed080fc3d7159ab794
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65489107"
---
# <a name="task-5-creating-a-domain-based-attribute-from-excel"></a>タスク 5: Excel からドメイン ベースの属性を作成する
  このタスクでは、 **Supplier**エンティティの**State**属性を**ドメインベースの属性**として変換します。 State 属性をドメインベースの属性に構成し、MDS にパブリッシュすると、列のすべての値を使用して**state**という名前の新しいエンティティが mds サーバーに作成され、 **Supplier**エンティティの**state**属性に**state**エンティティの値が設定されます。 現在、サプライヤー**モデルに**は、 **supplier**と**state**という2つのエンティティがあります **。 Supplier エンティティの** **state**属性は、 **state**エンティティに依存するドメインベースの属性です。  
  
1.  クレンジングされた**仕入先 .xlsx**が開かれている**Excel**ウィンドウに切り替えます。  
  
2.  リボンの [**更新**] ボタンをクリックして、MDS から最新の更新プログラムを取得します。 オプションの**タスク 4**を実行した場合は、さらに2つのレコードが表示されます。  
  
3.  **ヘッダー行**の列名の**状態**(セル**I1**) をクリックします。  
  
     ![Excel - [属性プロパティ] ボタン](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-01.jpg "Excel - [属性プロパティ] ボタン")  
  
4.  リボンの [**属性プロパティ**] をクリックします。  
  
5.  [**属性のプロパティ**] ダイアログボックスで、**属性の種類**として [**制約付き一覧 (ドメインベース)** ] を選択します。  
  
6.  **新しいエンティティ名**として「 **State** 」と入力し、[ **OK]** をクリックします。  
  
     ![Excel - [属性プロパティ] ダイアログ ボックス](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-02.jpg "Excel - [属性プロパティ] ダイアログ ボックス")  
  
7.  Excel では、[**状態**] 列の値をクリックすると**下矢印**が表示されます。 必要に応じてドロップダウン リストを使用して値を変更できます。  
  
     ![Excel - 州のドロップダウン リスト](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-03.jpg "Excel - 州のドロップダウン リスト")  
  
## <a name="next-step"></a>次のステップ  
 [タスク 6: マスター データ マネージャーを使用してドメイン ベースの属性が作成されていることを確認する](../../2014/tutorials/task-6-verify-domain-based-attribute-master-data-manager.md)  
  
  
