---
title: 'タスク 16: マスターデータマネージャーによる検証 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 57ad9d3e-8f95-4df6-af01-c291ccf49164
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 35dd2da7f6cf6598918cd9d109b97f3d314556d1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65484688"
---
# <a name="task-16-verifying-with-master-data-manager"></a>タスク 16: マスター データ マネージャーを確認する
  ここでは、マスター データ マネージャーを使用して、SSIS パッケージによって送信されたバッチ ジョブの状態をチェックし、データが MDS サーバーにアップロードされたことを確認します。  
  
1.  **マスターデータマネージャー** ([http://localhost/MDS](http://localhost/MDS)) を起動します。 既に開いている場合は、上部にある [ **Microsoft SQL Server マスターデータサービス**をクリックして、**ホームページ**に移動します。  
  
2.  [**統合管理**] をクリックします。  
  
3.  リストに送信した**Eimbatch**という名前のバッチがあることに注意してください。 次の画面が表示されない場合は、メニューバーの [**データのインポート**] をクリックします。  
  
     ![EIM バッチ](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "EIM バッチ")  
  
4.  上部にある [ **SQL Server 2012 マスターデータサービス**をクリックして、ホームページに戻ります。  
  
5.  [**モデル**] に [**仕入先**モデル] が選択されていることを確認し、[**バージョン**] で [ **VERSION_1** ] が選択されていることを確認し、[**エクスプローラー**  
  
6.  MDS にインポートされたデータの SSIS パッケージが表示されます。 データはクレンジングされ、重複する**コード**値はありません (注: Excel の [**仕入**先] 列は、MDS の Supplier エンティティの**code**属性に対応しています)。  
  
## <a name="next-step"></a>次のステップ  
 [タスク 17: SSIS パッケージによって作成された DQS クレンジング プロジェクトを確認する](../../2014/tutorials/task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package.md)  
  
  
