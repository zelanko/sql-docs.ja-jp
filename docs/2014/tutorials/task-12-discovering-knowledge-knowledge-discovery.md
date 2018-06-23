---
title: 'タスク 12: 検出の知識 (ナレッジ検出) |Microsoft ドキュメント'
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
ms.assetid: dd80a8e6-1e41-4c49-9898-02b1d2505a10
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b608a384e5281134ae951fdfeca0e89234c4a32a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084897"
---
# <a name="task-12-discovering-knowledge-knowledge-discovery"></a>タスク 12: ナレッジを検出する (ナレッジ検出)
  このタスクでは、実行、**ナレッジ検出**上のアクティビティ**Supplier ID**と**Supplier Name**ドメイン。 このシナリオでは、ナレッジ検出プロセスにより主にこれら 2 つのドメインの値をインポートします。  
  
 このチュートリアルでは、ナレッジ ベースを最初から作成しました。 さらに、ナレッジ検出アクティビティを実行してナレッジ ベースを作成することができます。 クリックすると、**ナレッジ ベースを作成**メイン ページで、DQS クライアントに進み、含まれているページ**ドメイン管理**活動の選択したアクティビティ。 変更することができます、**アクティビティ**に**ナレッジ検出**し、次のページでドメインを作成できます、ナレッジ検出プロセスの一部としてとします。 参照してください[Perform Knowledge Discovery](http://msdn.microsoft.com/library/hh510398.aspx)詳細についてはします。  
  
1.  DQS クライアントのメイン ページでの**最近使用したナレッジ ベース**セクションで、**[右矢印]** の横に、 **Suppliers**ナレッジ ベースをクリック**ナレッジ探索**です。 またはをクリックして**ナレッジ ベースを開く** **Suppliers**から、**ナレッジ ベースの一覧****ナレッジ検出**として**アクティビティ** をクリック**次**です。  
  
     ![ナレッジ検出 メニューのメイン ページ](../../2014/tutorials/media/et-discoveringknowledge-01.jpg "メイン ナレッジ検出 メニュー ページ")  
  
2.  選択**Excel ファイル**の**データソース**です。  
  
3.  をクリックして**参照**移動し、選択、 **Suppliers.xls**、 をクリック**開く**です。  
  
4.  選択**Suppliers for Discovery**の**ワークシート**です。  
  
5.  **マッピング**セクションで、マップ**SupplierID**列から、 **Excel**ファイルの名前を**Supplier ID**ドメインと**Supplier Name**列を**Supplier Name**を使用してドメイン**ドロップ ダウン リスト**です。 Excel ファイルにサンプル データを**Supplier ID**と**Supplier Name**ドメイン。 検出プロセスでは、値を検出するドメインを選択できます。 このページでドメインを作成し、これらのドメインにソース列をマップできます。 ドメイン管理アクティビティ中にドメインを作成する代わりに、ナレッジ検出アクティビティ中にドメインを作成することは一般的でありません。  
  
     ![検出プロセスのページをマップ](../../2014/tutorials/media/et-discoveringknowledge-02.jpg "検出プロセスのページにマップ")  
  
6.  をクリックして**次**に切り替えるには、 **Discover**ページ。  
  
7.  **Discover**  ページで、をクリックして**開始**検出プロセスを開始します。 列に対して検出が実行**SupplierID**と**Supplier Name**で、 **Suppliers.xls**ファイル。 **Supplier ID**と**Supplier Name**検出によって取得されたナレッジ ドメインを設定する必要があります。  
  
     ![検出プロセスのページを検出](../../2014/tutorials/media/et-discoveringknowledge-03.jpg "検出プロセスのページを検出")  
  
8.  分析が完了すると、確認、**のソース統計情報**で、 **[プロファイラー] タブ**ページの下部にあります。 10 の新しいレコードとが 20 個の値を合計ことに注意してください (**SupplierID**と**Supplier Name**値から、 **Excel ワークシート**) 検出されました。 さらに、これらの値のうちいくつが、新しい値、一意の値、新しい一意の値、および有効な値であるかがわかります。 右側のリスト ボックスには、検出プロセスに使用された各ドメインの詳細が表示されます。 [完全] 列のステータス バーにマウス ポインターを合わせると、ソースの列に不足値があるかどうかを表示できます。  
  
     ![ナレッジ検出結果](../../2014/tutorials/media/et-discoveringknowledge-04.jpg "ナレッジ検出の結果")  
  
9. をクリックして**次**に切り替えるには、**ドメイン値の管理**ページ。  
  
10. **ドメイン値の管理**] ページで [ **Supplier Name**ドメインの一覧からドメイン。  
  
11. 右側のペインで右クリック**Lazy Country Storex** (末尾には通知 'x') を選択して**Lazy Country Store**です。 DQS により、ドメインに対するスペル チェッカーの実行後、この変更内容が提案されます。 既定では、作成するドメインに対するスペル チェックが有効になっています。  
  
     ![仕入先名 - Lazy Country Store を修正](../../2014/tutorials/media/et-discoveringknowledge-05.jpg "仕入先名 - Lazy Country Store を修正")  
  
12. ドメイン値の一覧でいることを確認、値**Lazy Country Storex**エラーとして設定されている (赤い**X**マーク) に**Lazy Country Store**と修正も、 **Lazy Country Store**有効な値としても追加されます。  
  
     ![ドメイン値の値を修正して](../../2014/tutorials/media/et-discoveringknowledge-06.jpg "ドメイン値し、値を修正")  
  
13. **[完了]** をクリックします。  
  
14. **SQL Server Data Quality Services**ダイアログ ボックスで、をクリックして**発行**です。  
  
15. をクリックして**OK** [成功] メッセージ ボックスです。  
  
     これで、チュートリアルの最初のレッスンを完了しました。  
  
## <a name="next-step"></a>次の手順  
 [レッスン 2: Suppliers ナレッジ ベースを使用して仕入先データをクレンジングする](../../2014/tutorials/lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base.md)  
  
  