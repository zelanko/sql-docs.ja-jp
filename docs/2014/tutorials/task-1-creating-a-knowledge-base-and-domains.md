---
title: 'タスク 1: ナレッジベースとドメインを作成する |Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 7d74a60b-8933-4038-bcbb-4e9dcc4f70e9
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 79edd8566f2b3c9b586bc8c8815e1d9bc586fb05
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65481241"
---
# <a name="task-1-creating-a-knowledge-base-and-domains"></a>タスク 1: ナレッジ ベースとドメインを作成する
  このタスクでは、**サプライヤー**ナレッジベースを作成し、データのクレンジングと照合データに使用されるドメインを作成して、重複部分を削除します。  
  
1.  **Data Quality Client**を起動します。 [**スタート**] をクリックし、[**すべてのプログラム**] をポイントし、[ **Microsoft SQL Server 2012**]、[ **Data Quality Services**]、[ **Data Quality Client**] の順にクリックします。  
  
2.  [**サーバーへの接続**] ダイアログボックスで、DQS がインストールされているデータベースサーバーインスタンスを選択し、[**接続**] をクリックします。  
  
     ![[サーバーへの接続] ダイアログボックス](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-01.jpg "[サーバーへの接続] ダイアログ ボックス")  
  
3.  Data Quality Client のホームページの [**ナレッジベース管理**] ウィンドウで、[**新しいナレッジベース**] をクリックします。  
  
     ![ナレッジ ベース管理 - 新しい KB](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-02.jpg "ナレッジ ベース管理 - 新しい KB")  
  
4.  ナレッジベースの**名前**として「**仕入先**」と入力します。  
  
     ![新しいナレッジ ベース - ドメイン管理](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-03.jpg "新しいナレッジ ベース - ドメイン管理")  
  
5.  **サプライヤー**ナレッジベースを最初から作成しているため、[フィールド**からナレッジベースを作成**する] が **[なし**] に設定されていることを確認します。  
  
6.  **アクティビティ**の [**ドメイン管理**] が選択されていることを確認し、[**次へ**] をクリックします。 ドメイン管理アクティビティを使用すると、ナレッジ ベース内のドメインを作成および管理できます。  
  
7.  [**ドメイン管理**] ウィンドウで、[ドメインの**作成**] ツールバーボタンをクリックして、ドメインを作成します。  
  
     ![[ドメインの作成] ツール バー ボタン](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-04.jpg "[ドメインの作成] ツール バー ボタン")  
  
8.  [**ドメインの作成**] ダイアログボックスで、**ドメイン名**として「 **Supplier ID** 」と入力し、[ **OK**] をクリックします。  
  
     ![[ドメインの作成] ダイアログ ボックス](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-05.jpg "[ドメインの作成] ダイアログ ボックス")  
  
9. 前の手順を繰り返して、すべて既定の設定になっている次のドメインを作成します。 このチュートリアルを簡単にするために、すべてのドメインの**データ型**を**文字列**として設定します。 他に使用できるデータ型には、Integer、Decimal、および Date があります。 [**先頭の値を使用**する] オプションが選択されている場合 (既定)、すべてのシノニムが出力のシノニムグループの先頭の値に置き換えられます。 **文字列の正規化**オプションを設定すると (既定)、ドメイン値の特殊文字は削除されます。 [**形式の出力先**] オプションを使用すると、ドメイン内のデータ値が出力されるときに適用される書式設定を選択できます。 ドメインの設定時にすべての文字列値に対してスペルチェックを実行するには、[**スペルチェックを有効**にする (既定)] を選択します。 [**言語**] 設定では、適用する**スペルチェック**の言語バージョンを指定します。 構文エラーの文字列値を確認せずにドメインを設定するには、[**構文エラーアルゴリズムを無効**にする] をオンにします。 詳細については、MSDN ライブラリの「[ドメインの作成](https://msdn.microsoft.com/library/hh510401.aspx)」を参照してください。  
  
    -   Supplier Name  
  
    -   連絡先のメール アドレス  
  
    -   Address Line  
  
    -   City  
  
    -   State  
  
    -   Country  
  
    -   Zip  
  
## <a name="next-step"></a>次のステップ  
 [タスク 2: ドメイン値を手動で追加する](../../2014/tutorials/task-2-adding-domain-values-manually.md)  
  
  
