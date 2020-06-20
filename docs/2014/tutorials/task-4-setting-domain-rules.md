---
title: 'タスク 4: ドメインルールの設定 |Microsoft Docs'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3a7162ba-cf2f-481f-830d-bb6a02823827
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0104fe6b64ff2ecc1a37bb1da9691e34d7913f21
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85061090"
---
# <a name="task-4-setting-domain-rules"></a>タスク 4: ドメイン ルールを設定する
  このタスクでは、**連絡先の電子メール**ドメインのルールを作成して、電子メールアドレスの末尾が** \@ adventure-works.com**であるかどうかを確認します。 ページの詳細については、「[ドメインルールの作成](https://msdn.microsoft.com/library/hh510397.aspx)」を参照してください。  
  
1.  **ドメインリスト**の [**連絡先の電子メール**] をクリックします。  
  
2.  右ペインの [**ドメインルール**] タブに切り替えます。  
  
     ![[新しいドメイン ルールの追加] ツール バー ボタン](../../2014/tutorials/media/et-settingdomainrules-01.jpg "[新しいドメイン ルールの追加] ツール バー ボタン")  
  
3.  右側のウィンドウで、ツールバーの [**新しいドメインルールの追加**] ボタン (画像を参照) をクリックしてルールを追加します。  
  
4.  **規則名**として「**電子メールの検証**」と入力し、 **enter**キーを押します。 [**アクティブ**] チェックボックスは、既定でオンになっている必要があります。 このコントロールを使用すると、ルールを一時的に非アクティブ化できます。  
  
5.  [**ルールの作成**] ペインで、**下矢印**をクリックし、[**値の末尾**] を選択します。  
  
6.  テキストボックスに「 ** \@ adventure-works.com** 」と入力し、 **tab**キーを押します。 [**ルールの作成**] ペインの [**選択した句に新しい条件を追加**] ツールバーボタンをクリックすると、さらに条件を追加できます。  
  
     ![電子メール検証ルール](../../2014/tutorials/media/et-settingdomainrules-02.jpg "電子メール検証ルール")  
  
7.  サンプルデータに対してルールをテストするには、右側のペインのツールバーにある [**テストデータに対して選択したドメインルールを実行**する] ボタンをクリックします。  
  
     ![[テスト データについて選択したドメイン ルールを実行します] ツール バー ボタン](../../2014/tutorials/media/et-settingdomainrules-03.jpg "[テスト データについて選択したドメイン ルールを実行します] ツール バー ボタン")  
  
8.  [**ドメインルールのテスト**] ダイアログボックスで、ツールバーの [**ドメインルールの新しいテスト用語を追加**します] ボタンをクリックします。  
  
     ![[ドメイン ルールのテスト] ダイアログ ボックス](../../2014/tutorials/media/et-settingdomainrules-04.jpg "[ドメイン ルールのテスト] ダイアログ ボックス")  
  
9. [ **Contact Email** ] 列に「 **frank7 \@ adventure-works.com** (有効な値)」と入力します。  
  
10. 前の2つの手順を繰り返して、 **joe2 \@ adventure-work.com**を追加します (の値が無効な場合は、')。  
  
11. ツールバーの最後のボタン ([**すべての用語でドメインルールをテスト**]) をクリックして、ルールに対して入力データをテストします。  
  
     ![[すべての用語でドメイン ルールをテスト] ツール バー ボタン](../../2014/tutorials/media/et-settingdomainrules-05.jpg "[すべての用語でドメイン ルールをテスト] ツール バー ボタン")  
  
12. 最初のエントリが有効な項目として、2 番目のエントリが無効な項目として表示されることに注意してください。  
  
     ![ドメイン ルールのテストの結果](../../2014/tutorials/media/et-settingdomainrules-06.jpg "ドメイン ルールのテストの結果")  
  
13. [**閉じる**] をクリックして [**ドメインルールのテスト**] ダイアログボックスを閉じます。  
  
## <a name="next-step"></a>次の手順  
 [タスク 5: 用語ベースのリレーションを設定する](../../2014/tutorials/task-5-setting-term-based-relationships.md)  
  
  
