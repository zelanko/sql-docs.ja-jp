---
title: 'タスク 16: マスター データ マネージャーを確認する |Microsoft Docs'
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
ms.topic: conceptual
ms.assetid: 57ad9d3e-8f95-4df6-af01-c291ccf49164
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7d0c5b2f72a04b1c1f99829e61ca2dca3fedc39a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37304652"
---
# <a name="task-16-verifying-with-master-data-manager"></a>タスク 16: マスター データ マネージャーを確認する
  ここでは、マスター データ マネージャーを使用して、SSIS パッケージによって送信されたバッチ ジョブの状態をチェックし、データが MDS サーバーにアップロードされたことを確認します。  
  
1.  起動**マスター データ マネージャー** ([http://localhost/MDS](http://localhost/MDS))。 既に開いている、クリックして**Microsoft SQL Server マスター データ サービス**に切り替えるの上部にある、**ホーム ページ**。  
  
2.  クリックして**統合管理**します。  
  
3.  という名前のバッチがあることに注意してください**EIMBatch**一覧には、送信します。 クリックして**データのインポート**次の画面が表示されない場合は、メニュー バー。  
  
     ![EIM バッチ](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "EIM バッチ")  
  
4.  をクリックして、ホーム ページに切り替える**SQL Server 2012 マスター データ サービス**上部にあります。  
  
5.  確認します**Suppliers**モデルが選択されている**モデル**と**VERSION_1**が選択されている**バージョン**、 をクリック**エクスプ ローラー**します。  
  
6.  MDS にインポートされたデータの SSIS パッケージが表示されます。 データはクレンジングされており、重複があるない**コード**値 (注: **SupplierID** Excel 列に対応**コード**MDS の Supplier エンティティの属性)。  
  
## <a name="next-step"></a>次の手順  
 [タスク 17: SSIS パッケージによって作成された DQS クレンジング プロジェクトを確認する](../../2014/tutorials/task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package.md)  
  
  
