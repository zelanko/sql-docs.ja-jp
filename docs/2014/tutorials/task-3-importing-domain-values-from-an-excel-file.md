---
title: 'タスク 3: Excel ファイルからドメイン値をインポートする |Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 242e8309-1195-495b-9cd5-aa127748c185
ms.author: lle
author: lrtoyou1223
ms.openlocfilehash: d86d71a3d62ca94eed2da5ad91fbdd60ee4989f4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66822970"
---
# <a name="task-3-importing-domain-values-from-an-excel-file"></a>タスク 3:Excel ファイルからドメイン値をインポートする

  ここでは、Excel ファイルのワークシートから **State** ドメインの値をインポートします。  
  
1.  
  **[ドメイン リスト]** から **State**ドメインをクリックします。  
  
2.  右側のペインで、 **[ドメイン値]** タブがアクティブになっていることを確認します。  
  
3.  右側のペインのツール バーで、 **[値をインポートします]** の横にある **下矢印** をクリックし、 **[Excel から有効な値をインポートします]** をクリックします。  
  
     ![[Excel から有効な値をインポートします] メニュー](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-01.jpg "[Excel から有効な値をインポートします] メニュー")  
  
4.  
  **[参照]** をクリックし、 **Suppliers.xls**を選択して、 **[開く]** をクリックします。  
  
5.  
  **[ワークシート]** に **StatesToImport$** を選択します。  
  
     ![[ドメイン値のインポート] ダイアログ ボックス](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-02.jpg "[ドメイン値のインポート] ダイアログ ボックス")  
  
6.  
  **[OK]** をクリックして **[ドメイン値のインポート]** ダイアログ ボックスを閉じます。 インポートしたすべての州の名前が一覧に表示されます。 インポート後は、 **[新規のみ表示]** オプションが自動的に選択されます。 値をインポートするときに、一覧に古い値が表示されない場合は、インポート後にこのオプションが自動的に有効になるためです。 すべての値を表示するには、このチェック ボックスをオフにします。 同じ値のセットをもう一度インポートすると、これらはドメインに既に存在するので、値はインポートされません。  
  
     ![ドメイン値の [新規のみ表示] チェック ボックス](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-03.jpg "ドメイン値の [新規のみ表示] チェック ボックス")  
  
## <a name="next-step"></a>次のステップ  
 [タスク 4: ドメイン ルールを設定する](../../2014/tutorials/task-4-setting-domain-rules.md)  
  
  
