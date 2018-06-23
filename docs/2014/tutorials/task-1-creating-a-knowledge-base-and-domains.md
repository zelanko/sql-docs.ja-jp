---
title: '作業 1: ナレッジ ベースとドメインの作成 |Microsoft ドキュメント'
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
ms.assetid: 7d74a60b-8933-4038-bcbb-4e9dcc4f70e9
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: beec636f9137802c6651f0c08889acf73000b063
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173582"
---
# <a name="task-1-creating-a-knowledge-base-and-domains"></a>タスク 1: ナレッジ ベースとドメインを作成する
  このタスクで作成、 **Suppliers**サポート技術情報データのクレンジングおよび照合のデータの重複の削除に使用されるドメインを作成するとします。  
  
1.  起動**Data Quality Client**です。 をクリックして**開始**、 をポイント**すべてのプログラム**、 をクリックして**Microsoft SQL Server 2012**、 をクリックして**Data Quality Services**をクリックして**Data Quality Client**です。  
  
2.  **サーバーへの接続** ダイアログ ボックスで、データベース サーバー インスタンスを DQS がインストールされ、をクリックして選択**接続**です。  
  
     ![サーバーに接続 ダイアログ ボックス](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-01.jpg "サーバーに接続 ダイアログ ボックス")  
  
3.  ホーム ページの Data Quality Client で、**ナレッジ ベース管理** ウィンドウで、をクリックして**新しいナレッジ ベース**です。  
  
     ![ナレッジ ベース管理 - 新しい KB](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-02.jpg "ナレッジ ベース管理 - 新しい KB")  
  
4.  入力**Suppliers**の**名前**サポート技術情報のです。  
  
     ![新しいナレッジ ベース - ドメイン管理](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-03.jpg "新しいナレッジ ベース - ドメイン管理")  
  
5.  いることを確認**からナレッジ ベースを作成する**にフィールドが設定されている**None**作成しているため、 **Suppliers**ナレッジ ベースを最初からです。  
  
6.  いることを確認**ドメイン管理**が選択されて、**アクティビティ** をクリック**次**です。 ドメイン管理アクティビティを使用すると、ナレッジ ベース内のドメインを作成および管理できます。  
  
7.  **ドメイン管理**ウィンドウで、をクリックして**ドメインを作成**ツールバーの ドメインを作成します。  
  
     ![ドメインの作成ツール バー ボタン](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-04.jpg "ドメインの作成ツール バー ボタン")  
  
8.  **ドメインの作成** ダイアログ ボックスで、「 **Supplier ID**の、**ドメイン名** をクリック**OK**です。  
  
     ![ドメイン ダイアログ ボックスを作成する](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-05.jpg "ドメイン ダイアログ ボックスを作成します。")  
  
9. 前の手順を繰り返して、すべて既定の設定になっている次のドメインを作成します。 このチュートリアルを簡潔にするを設定する、**データ型**としてすべてのドメインの**文字列**です。 他に使用できるデータ型には、Integer、Decimal、および Date があります。 ときに、**先頭の値を使用して**オプションがオン (既定)、すべてのシノニムは出力に、シノニムのグループの先頭の値に置き換えられます。 設定**文字列を正規化**オプション (既定) が、ドメインの値に特殊文字を削除します。 **形式の出力先**オプションを使用して、ドメイン内のデータ値が出力時に適用される書式設定を選択できます。 選択**スペル チェックを有効にする**ドメインを作成するときに、すべての文字列値でスペル チェックを実行するには、(既定)。 **言語**設定の言語バージョンを指定する、**スペル チェック**を適用します。 選択**構文エラーのアルゴリズムを無効にする**に構文エラーの文字列値をチェックせずにドメインを設定します。 参照してください[ドメインを作成する](http://msdn.microsoft.com/library/hh510401.aspx)詳細については、MSDN ライブラリの「します。  
  
    -   Supplier Name  
  
    -   Contact Email  
  
    -   Address Line  
  
    -   City  
  
    -   状態  
  
    -   Country  
  
    -   Zip  
  
## <a name="next-step"></a>次の手順  
 [タスク 2: ドメイン値を手動で追加する](../../2014/tutorials/task-2-adding-domain-values-manually.md)  
  
  