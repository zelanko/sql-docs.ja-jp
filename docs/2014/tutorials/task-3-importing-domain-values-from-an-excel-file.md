---
title: 'タスク 3: Excel ファイルからドメイン値のインポート |Microsoft ドキュメント'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 242e8309-1195-495b-9cd5-aa127748c185
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: fd5f73f95dce1d40689062a368e1cc222023541c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070851"
---
# <a name="task-3-importing-domain-values-from-an-excel-file"></a>タスク 3:Excel ファイルからドメイン値をインポートする
  ここでは、Excel ファイルのワークシートから **State** ドメインの値をインポートします。  
  
1.  **[ドメイン リスト]** から **State**ドメインをクリックします。  
  
2.  右側のペインで、 **[ドメイン値]** タブがアクティブになっていることを確認します。  
  
3.  右側のペインのツール バーで、 **[値をインポートします]** の横にある **下矢印** をクリックし、 **[Excel から有効な値をインポートします]** をクリックします。  
  
     ![Excel のメニューから有効な値をインポート](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-01.jpg "Excel メニューからの有効な値のインポート")  
  
4.  **[参照]** をクリックし、 **Suppliers.xls**を選択して、 **[開く]** をクリックします。  
  
5.  **[ワークシート]** に **StatesToImport$** を選択します。  
  
     ![ドメインのインポート ダイアログ ボックスの値](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-02.jpg "ドメインのインポート ダイアログ ボックスの値")  
  
6.  **[OK]** をクリックして **[ドメイン値のインポート]** ダイアログ ボックスを閉じます。 インポートしたすべての州の名前が一覧に表示されます。 インポート後は、 **[新規のみ表示]** オプションが自動的に選択されます。 値をインポートする際に、一覧に古い値が表示されないのは、このオプションがインポート後に自動的に有効になるためです。 すべての値を表示するには、このチェック ボックスをオフにします。 同じ値のセットをもう一度インポートすると、これらはドメインに既に存在するので、値はインポートされません。  
  
     ![ドメインの値にのみ新しいチェック ボックスを表示する](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-03.jpg "ドメインの値にのみ新しいチェック ボックスを表示します。")  
  
## <a name="next-step"></a>次の手順  
 [タスク 4: ドメイン ルールを設定する](../../2014/tutorials/task-4-setting-domain-rules.md)  
  
  