---
title: 'タスク 5: Excel からドメイン ベースの属性を作成する |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 07cbc624-2c6b-4568-96e4-f18663a05d80
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 5e7a8dda16d8f513b2c4b07b9f41712be806b8a9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163981"
---
# <a name="task-5-creating-a-domain-based-attribute-from-excel"></a>タスク 5: Excel からドメイン ベースの属性を作成する
  このタスクで変換する、**状態**の属性、**業者**エンティティとして、**ドメイン ベース属性**です。 ドメイン ベースのどちらを指定して、MDS、という名前の新しいエンティティに発行する State 属性を構成した後**状態**列内のすべての値と共に MDS サーバーに作成されます、**状態**の属性、**業者**から値を持つエンティティが設定されます、**状態**エンティティです。 ここで、 **Suppliers**モデルは 2 つのエンティティである必要があります:**業者**と**状態**場所、**状態**の属性、 **供給業者**エンティティに依存するドメイン ベースの属性は、**状態**エンティティです。  
  
1.  切り替える**Excel**のあるウィンドウ**Cleansed and Matched Suppliers.xlsx**を開きます。  
  
2.  をクリックして**更新**MDS から最新の更新プログラムを取得するには、リボンのボタンをクリックします。 省略可能な実行している場合、2 つのレコードが表示されます**タスク 4**です。  
  
3.  列名をクリックして**状態**(セル**I1**) で、**ヘッダー行**です。  
  
     ![Excel - [属性プロパティ] ボタン](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-01.jpg "Excel - [属性プロパティ] ボタン")  
  
4.  をクリックして**属性プロパティ**リボン上。  
  
5.  **属性プロパティ**ダイアログ ボックスで、**制約付き一覧 (ドメイン ベース)** の**属性の種類**です。  
  
6.  型**状態**の**新しいエンティティ名** をクリック**OK**です。  
  
     ![Excel - [属性プロパティ] ダイアログ ボックス](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-02.jpg "Excel - [属性プロパティ] ダイアログ ボックス")  
  
7.  ここで、Excel で表示されます**下向きの矢印**の任意の値をクリックすると、**状態**列です。 必要に応じてドロップダウン リストを使用して値を変更できます。  
  
     ![Excel - ドロップダウン リストでの状態を持つ](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-03.jpg "Excel - ドロップダウン リストでの状態を持つ")  
  
## <a name="next-step"></a>次の手順  
 [タスク 6: マスター データ マネージャーを使用してドメイン ベースの属性が作成されていることを確認する](../../2014/tutorials/task-6-verify-domain-based-attribute-master-data-manager.md)  
  
  