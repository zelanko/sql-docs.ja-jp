---
title: 'タスク 4: ドメイン ルールを設定する |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a7162ba-cf2f-481f-830d-bb6a02823827
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 89e0027b3bf1748fb68a8b6922c45572a7b41bb7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076755"
---
# <a name="task-4-setting-domain-rules"></a>タスク 4: ドメイン ルールを設定する
  このタスクでのルールを作成する、 **Contact Email**電子メール アドレスで終了することを確認するドメイン **@adventure-works.com**です。 参照してください[ドメイン ルールを作成する](http://msdn.microsoft.com/library/hh510397.aspx)ページの詳細についてはトピックです。  
  
1.  をクリックして**Contact Email**で、**ドメイン リスト**です。  
  
2.  切り替えて、**ドメイン ルール**右ペインでタブです。  
  
     ![新しいドメイン ルールのツール バー ボタンの追加](../../2014/tutorials/media/et-settingdomainrules-01.jpg "新しいドメイン ルールのツール バー ボタンの追加")  
  
3.  右側のウィンドウでをクリックして**新しいドメイン ルールの追加**ツールバーのボタン (イメージを参照してください) を使用規則を追加します。  
  
4.  型**Email Validation**の**ルール名**とキーを押します**ENTER**です。 **Active**  チェック ボックスは既定でチェックする必要があります。 このコントロールを使用すると、ルールを一時的に非アクティブ化できます。  
  
5.  **ルールの作成** ウィンドウで、をクリックして**下向きの矢印**を選択して**値で終わります**です。  
  
6.  型**@adventure-works.com**のテキスト ボックスおよびキーを押して**タブ**です。 クリックして詳細な条件を追加することができます**選択した句に新しい条件の追加**ツール バー ボタン、**ルールの作成**ウィンドウです。  
  
     ![電子メール検証ルール](../../2014/tutorials/media/et-settingdomainrules-02.jpg "電子メールの検証規則")  
  
7.  をクリックして**テスト データについて選択したドメイン ルールを実行**サンプル データに対してルールをテストするには、右側のペインのツールバーのボタンをクリックします。  
  
     ![テスト データのツール バー ボタンのドメイン ルールを実行](../../2014/tutorials/media/et-settingdomainrules-03.jpg "テスト データのツール バー ボタン上のドメイン ルールの実行")  
  
8.  **ドメイン ルールのテスト**ダイアログ ボックスで、をクリックして**ドメイン ルールの新しいテスト用語を追加**ツールバーのボタンをクリックします。  
  
     ![ドメイン ルール ダイアログ ボックスをテスト](../../2014/tutorials/media/et-settingdomainrules-04.jpg "ドメイン ルール ダイアログ ボックスのテスト")  
  
9. 型**frank7@adventure-works.com** (有効な値) で、 **Contact Email**列です。  
  
10. 前の 2 つの手順を繰り返して追加**joe2@adventure-work.com** (のない無効な値の ')。  
  
11. 最後のボタンをクリックして (**すべての用語でドメイン ルールをテスト**)、ルールに対して入力データをテストするツールバーです。  
  
     ![すべての用語のツール バー ボタンでドメイン ルールをテスト](../../2014/tutorials/media/et-settingdomainrules-05.jpg "すべて条項ツール バー ボタンでドメイン ルールのテスト")  
  
12. 最初のエントリが有効な項目として、2 番目のエントリが無効な項目として表示されることに注意してください。  
  
     ![ドメイン ルールの結果をテスト](../../2014/tutorials/media/et-settingdomainrules-06.jpg "ドメイン ルールの結果のテスト")  
  
13. をクリックして**閉じる**を閉じる、**ドメイン ルールのテスト** ダイアログ ボックス。  
  
## <a name="next-step"></a>次の手順  
 [タスク 5: 用語ベースのリレーションを設定する](../../2014/tutorials/task-5-setting-term-based-relationships.md)  
  
  