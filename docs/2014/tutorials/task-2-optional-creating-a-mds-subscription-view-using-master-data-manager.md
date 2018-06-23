---
title: 'タスク 2 (省略可能): マスター データ マネージャーを使用して MDS サブスクリプション ビューを作成する |Microsoft ドキュメント'
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
ms.assetid: f3da8219-e0cb-4848-95ca-285a76ec1ba9
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 4883d4f5c7bef05de9625c2fcb7bac235c0306e7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178119"
---
# <a name="task-2-optional-creating-a-mds-subscription-view-using-master-data-manager"></a>タスク 2 (オプション): マスター データ マネージャーを使用して MDS サブスクリプション ビューを作成する
  このタスクで公開するサブスクリプション ビューを作成する、**業者**内のエンティティ、 **Suppliers**を他のアプリケーション モデルです。 現在のバージョンのチュートリアルでは、このビューを使用しません。  
  
1.  メイン ページに切り替えます**マスター データ マネージャー** ([http://localhost/MDS](http://localhost/MDS)) をクリックして**SQL Server 2012 マスター データ サービス**上部にあります。  
  
2.  をクリックして**統合管理**です。  
  
3.  をクリックして**ビューの作成**メニュー バーでします。  
  
     ![新しいサブスクリプションの表示 ボタンを追加](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-01.jpg "新しいサブスクリプションの表示 ボタンの追加")  
  
4.  をクリックして **+ (正符号 +)** サブスクリプション ビューを作成するには、ツールバーのアイコン。  
  
5.  **サブスクリプション ビューの作成** ウィンドウで「 **Suppliers**の**サブスクリプション ビュー名**です。  
  
6.  選択**Suppliers**の**モデル**です。  
  
7.  選択**VERSION_1**の**バージョン**します。  
  
8.  選択**業者**の**エンティティ**です。  
  
9. 選択**リーフ メンバー**の**形式**です。  
  
     ![サブスクリプションの表示 ボタンを保存](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-02.jpg "サブスクリプションの表示 ボタンを保存")  
  
10. をクリックして**保存**ツールバーのサブスクリプション ビューを保存します。 この操作では、SQL Server 名前付きのビューを作成**Suppliers**です。 SQL Server Management Studio (SSMS) を使用してこれを確認できます。  
  
## <a name="next-step"></a>次の手順  
 [タスク 3&#40;省略可能な&#41;: サブスクリプション ビューを確認します。](task-3-optional-reviewing-the-subscription-views.md)  
  
  