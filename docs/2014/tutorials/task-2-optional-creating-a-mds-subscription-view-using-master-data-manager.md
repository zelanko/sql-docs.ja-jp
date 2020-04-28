---
title: 'タスク 2 (オプション): マスターデータマネージャー | を使用した MDS サブスクリプションビューの作成Microsoft Docs'
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81484712"
---
# <a name="task-2-optional-creating-a-mds-subscription-view-using-master-data-manager"></a>タスク 2 (オプション): マスター データ マネージャーを使用して MDS サブスクリプション ビューを作成する
  このタスクでは、**仕入先**モデルの**Supplier**エンティティを他のアプリケーションに公開するサブスクリプションビューを作成します。 現在のバージョンのチュートリアルでは、このビューを使用しません。  
  
1.  上部にある**SQL Server 2012 マスターデータサービス**をクリック`http://localhost/MDS`して**マスターデータマネージャー** () のメインページに切り替えます。  
  
2.  [**統合管理**] をクリックします。  
  
3.  メニューバーの [**ビューの作成**] をクリックします。  
  
     ![[新しいサブスクリプション ビューの追加] ボタン](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-01.jpg "[新しいサブスクリプション ビューの追加] ボタン")  
  
4.  サブスクリプションビューを作成するには、ツールバーの [ **+] (プラス)** アイコンをクリックします。  
  
5.  [**サブスクリプションビューの作成**] ペインで、[**サブスクリプションビュー名**] に「**仕入先**」と入力します。  
  
6.  **モデル**の**仕入先**を選択します。  
  
7.  [**バージョン**] で [ **VERSION_1** ] を選択します。  
  
8.  [**エンティティ**の**仕入先**] を選択します。  
  
9. [**形式**] で [**リーフメンバー** ] を選択します。  
  
     ![[サブスクリプション ビューの保存] ボタン](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-02.jpg "[サブスクリプション ビューの保存] ボタン")  
  
10. ツールバーの [**保存**] をクリックして、サブスクリプションビューを保存します。 この操作により、SQL Server の**仕入先**という名前のビューが作成されます。 SQL Server Management Studio (SSMS) を使用してこれを確認できます。  
  
## <a name="next-step"></a>次の手順  
 [タスク 3 &#40;オプションの&#41;: サブスクリプションビューの確認](task-3-optional-reviewing-the-subscription-views.md)  
  
  
