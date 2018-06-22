---
title: 'タスク 10: 参照データ サービスを使用する複合ドメインの構成 |Microsoft ドキュメント'
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
ms.assetid: 752eefde-8b87-4f54-878e-9963ccbadc8e
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 2a5d37578ac8336b67201161ef4de59baf90649c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075403"
---
# <a name="task-10-configuring-composite-domain-to-use-reference-data-service"></a>タスク 10: 参照データ サービスを使用して複合ドメインを構成する
  このタスクで構成する、 **Address Validation**複合ドメインを使用して、 **Melissa Data – Address Check**サービス。 実行時のクレンジング アクティビティでは、クレンジングのために Address Validation ドメインのドメイン値が DQS からこのサービスに渡されます。 参照してください[参照データにドメイン/複合ドメインをマップ](http://msdn.microsoft.com/library/hh213030.aspx)詳細についてはします。  
  
1.  メイン ページで**DQS クライアント**をクリックして**Suppliers (ドメイン管理)** **最近使用したナレッジ ベース**を起動する、**ドメイン管理**ページ。  
  
2.  選択、 **Address Validation**の複合ドメインに、**ドメインの一覧**です。  
  
3.  右側のペインでに切り替えると、**参照データ**タブです。  
  
     ![[データ] タブを参照](../../2014/tutorials/media/et-configuringcdtouserds-01.jpg "データ タブを参照")  
  
4.  をクリックして**参照**ツールバーのボタンをクリックします。  
  
5.  **オンライン参照データ プロバイダーのカタログ**ダイアログ ボックスで、 ** チェック ボックスを** の横に**Melissa Data – Address Check**です。  
  
     ![Melissa Data のアドレス確認を選択して](../../2014/tutorials/media/et-configuringcdtouserds-02.jpg "メリッサ データ - アドレスのチェックを選択")  
  
6.  右側のウィンドウでの**スキーマ**セクションで、マップ**Address Line**ドメインを**Address Line (M)** ドロップダウン リストを使用して、スキーマ項目。  
  
     ![RDS スキーマのアイテムをドメインにマップ](../../2014/tutorials/media/et-configuringcdtouserds-03.jpg "RDS スキーマのアイテムをドメインにマップします。")  
  
7.  をクリックして**スキーマ エントリの追加 (+)** 一覧にエントリを作成するには、ツールバーのボタンをクリックします。  
  
     ![スキーマ エントリのツール バー ボタンの追加](../../2014/tutorials/media/et-configuringcdtouserds-04.jpg "スキーマ エントリのツール バー ボタンの追加")  
  
8.  次の図に示すように、ドロップダウン リストを使用して次の DQS ドメインをマップします。  
  
     ![RDS スキーマ項目をドメインにマッピング](../../2014/tutorials/media/et-configuringcdtouserds-05.jpg "RDS スキーマ項目のドメインをマップします。")  
  
9. **[OK]** をクリックしてダイアログ ボックスを閉じます。  
  
## <a name="next-step"></a>次の手順  
 [タスク 11: ナレッジ ベースをパブリッシュする](../../2014/tutorials/task-11-publishing-the-knowledge-base.md)  
  
  