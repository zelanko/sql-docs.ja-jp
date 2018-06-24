---
title: 'タスク 16: マスター データ マネージャーを確認しています |Microsoft ドキュメント'
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
ms.assetid: 57ad9d3e-8f95-4df6-af01-c291ccf49164
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 36220f21f3e2e28d75ff546857fd87b1e71436f1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075162"
---
# <a name="task-16-verifying-with-master-data-manager"></a>タスク 16: マスター データ マネージャーを確認する
  ここでは、マスター データ マネージャーを使用して、SSIS パッケージによって送信されたバッチ ジョブの状態をチェックし、データが MDS サーバーにアップロードされたことを確認します。  
  
1.  起動**マスター データ マネージャー** ([http://localhost/MDS](http://localhost/MDS))。 既に開いている場合はクリックして**Microsoft SQL Server マスター データ サービス**に切り替えるには、上部にある、**ホーム ページ**です。  
  
2.  をクリックして**統合管理**です。  
  
3.  バッチがあることに注意してくださいという**EIMBatch**一覧に、送信することです。 をクリックして**データのインポート**次の画面が表示されない場合は、メニュー バーでします。  
  
     ![EIM バッチ](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "EIM バッチ")  
  
4.  クリックして、ホーム ページに切り替える**SQL Server 2012 マスター データ サービス**上部にあります。  
  
5.  確認して**Suppliers**のモデルが選択されている**モデル**と**VERSION_1**が選択されて**バージョン**、 をクリック**エクスプ ローラー**です。  
  
6.  MDS にインポートされたデータの SSIS パッケージが表示されます。 データはクレンジングされており、重複があるない**コード**値 (注: **SupplierID** Excel の列に対応**コード**MDS の Supplier エンティティの属性)。  
  
## <a name="next-step"></a>次の手順  
 [タスク 17: SSIS パッケージによって作成された DQS クレンジング プロジェクトを確認する](../../2014/tutorials/task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package.md)  
  
  