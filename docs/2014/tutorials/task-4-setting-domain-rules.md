---
title: タスク 4:ドメイン ルールを設定 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: 3a7162ba-cf2f-481f-830d-bb6a02823827
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6c3b51408258b93f6585b46171793eb885a6d0d3
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/13/2018
ms.locfileid: "53349574"
---
# <a name="task-4-setting-domain-rules"></a>タスク 4:ドメイン ルールを設定する
  このタスクでのルールを作成する、 **Contact Email**かどうかに、電子メール アドレスが終わることを確認するドメイン **@adventure-works.com**します。 参照してください[ドメイン ルールを作成する](https://msdn.microsoft.com/library/hh510397.aspx)ページの詳細についてはトピック。  
  
1.  クリックして**Contact Email**で、**ドメイン リスト**します。  
  
2.  切り替えて、**ドメイン ルール**右ペインでタブ。  
  
     ![新しいドメイン ルールのツール バー ボタンの追加](../../2014/tutorials/media/et-settingdomainrules-01.jpg "新しいドメイン ルールのツール バー ボタンの追加")  
  
3.  右側のウィンドウで次のようにクリックします。**新しいドメイン ルールの追加**ツールバーのボタン (イメージを参照してください) を使用してルールを追加します。  
  
4.  型**電子メール検証**の**ルール名**キーを押します**ENTER**します。 **Active**既定でチェック ボックスをオンにします。 このコントロールを使用すると、ルールを一時的に非アクティブ化できます。  
  
5.  **ルールの作成**ウィンドウで、をクリックして**下向きの矢印**を選択し、**値で終わります**します。  
  
6.  型**@adventure-works.com**キーを押して、テキスト ボックス内**タブ**します。 さらに条件を追加するにはクリックして**選択した句に新しい条件の追加**ツール バー ボタン、**ルールの作成**ウィンドウ。  
  
     ![電子メール検証ルール](../../2014/tutorials/media/et-settingdomainrules-02.jpg "電子メール検証ルール")  
  
7.  クリックして**テスト データについて選択したドメイン ルールを実行**サンプル データに対してルールをテストするには、右側のペインのツールバーのボタンをクリックします。  
  
     ![テスト データのツール バー ボタン上のドメイン ルールの実行](../../2014/tutorials/media/et-settingdomainrules-03.jpg "テスト データのツール バー ボタン上のドメイン ルールの実行")  
  
8.  **ドメイン ルールのテスト**ダイアログ ボックスで、をクリックして**ドメイン ルールの新しいテスト用語を追加します**ツールバーのボタンをクリックします。  
  
     ![ドメイン ルール ダイアログ ボックスのテスト](../../2014/tutorials/media/et-settingdomainrules-04.jpg "ドメイン ルール ダイアログ ボックスのテスト")  
  
9. 型**frank7@adventure-works.com** (有効な値) で、 **Contact Email**列。  
  
10. 追加する 2 つ前の手順を繰り返して**joe2@adventure-work.com** (のない無効な値の ')。  
  
11. 最後のボタンをクリックします (**すべての用語でドメイン ルールをテスト**)、ルールに対して入力データをテストするツールバーです。  
  
     ![すべての用語のツール バー ボタンでドメイン ルールをテスト](../../2014/tutorials/media/et-settingdomainrules-05.jpg "すべての用語のツール バー ボタンでドメイン ルールのテスト")  
  
12. 最初のエントリが有効な項目として、2 番目のエントリが無効な項目として表示されることに注意してください。  
  
     ![ドメイン ルールの結果をテスト](../../2014/tutorials/media/et-settingdomainrules-06.jpg "ドメイン ルールの結果をテストします。")  
  
13. クリックして**閉じます**を閉じる、**ドメイン ルールのテスト** ダイアログ ボックス。  
  
## <a name="next-step"></a>次の手順  
 [タスク 5:ベースのリレーションを設定](../../2014/tutorials/task-5-setting-term-based-relationships.md)  
  
  
