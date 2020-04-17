---
title: 'タスク 2 (オプション): マスター データ マネージャーを使用して MDS サブスクリプション ビューを作成する |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: f3da8219-e0cb-4848-95ca-285a76ec1ba9
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: cc923792adc3fefb5ebaab9e225169648394c71f
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81484712"
---
# <a name="task-2-optional-creating-a-mds-subscription-view-using-master-data-manager"></a>タスク 2 (オプション): マスター データ マネージャーを使用して MDS サブスクリプション ビューを作成する
  このタスクでは、Supplier モデルの**Supplier**エンティティを他のアプリケーション**Suppliers**に公開するサブスクリプション ビューを作成します。 現在のバージョンのチュートリアルでは、このビューを使用しません。  
  
1.  マスター**データ マネージャー** (`http://localhost/MDS`) のメイン ページに切り替えるには、上部にある **[SQL Server 2012 マスター データ サービス**] をクリックします。  
  
2.  [**統合管理**] をクリックします。  
  
3.  メニュー バーの **[ビューの作成**] をクリックします。  
  
     ![[新しいサブスクリプション ビューの追加] ボタン](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-01.jpg "[新しいサブスクリプション ビューの追加] ボタン")  
  
4.  ツールバーの **+(プラス)** アイコンをクリックして、サブスクリプションビューを作成します。  
  
5.  [**サブスクリプション ビューの作成**] ウィンドウで、「 サブスクリプション**ビュー名**の**仕入先 」** と入力します。  
  
6.  [**モデル** **] の [ 仕入先 ]** を選択します。  
  
7.  **[バージョン**] で **[VERSION_1]** を選択します。  
  
8.  [ エンティティ ] の **[ 仕入先 ]** **を**選択します。  
  
9. [フォーマット] で **[リーフ メンバ**] を**選択**します。  
  
     ![[サブスクリプション ビューの保存] ボタン](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-02.jpg "[サブスクリプション ビューの保存] ボタン")  
  
10. ツール バーの [**保存]** をクリックして、サブスクリプション ビューを保存します。 この操作により、 SQL Server 内に **" 仕入先 "** という名前のビューが作成されます。 SQL Server Management Studio (SSMS) を使用してこれを確認できます。  
  
## <a name="next-step"></a>次の手順  
 [タスク 3 &#40;オプション&#41;: サブスクリプション ビューの確認](task-3-optional-reviewing-the-subscription-views.md)  
  
  
