---
title: タスク 4:管理および結果を表示する |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ecc3ba7e-fecf-478f-8825-6e4764b00e99
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: c719b7d4bcd9b792beaa59fdbcf69783d7d3259d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62745633"
---
# <a name="task-4-manaing-and-viewing-results"></a>タスク 4:管理および結果を表示します。
  ここでは、コンピューター支援型のクレンジングの結果を確認し、仕入先データに対してインタラクティブなクレンジングを実行します。 参照してください[インタラクティブなクレンジング ステージ](https://msdn.microsoft.com/library/hh213061.aspx#Interactive)の詳細。  
  
1.  選択**Contact Email**ドメインの一覧からドメイン。  
  
2.  切り替えて、**無効な**右ペインでタブ。 通知の 2 つの電子メール アドレスは文字の不足している ' 最後にします。 これら 2 つの電子メールで終わるすべての電子メール アドレスを要求するドメイン ルールを無効になることは**@adventure-works.com** (での ')。 DQS は、クレンジング中にドメイン ルールを使用して電子メールが有効かどうかを判断します。 このタブには、ナレッジ ベースで無効と見なされたドメイン値か、ドメイン ルールに違反するドメイン値が表示されます。 この場合、これらの値はドメイン ルール (Email Validation) に違反しています。  
  
3.  **に修正**列に適切な電子メール アドレスで終わる型**@adventure-works.com** (での ')。  
  
     ![電子メール検証ルールによる修正](../../2014/tutorials/media/et-managingandviewingresults-01.jpg "電子メール検証ルールによる修正")  
  
4.  クリックして**承認**の両方の変更を承認する、両方のレコード。 承認すると、レコード移動、 **Corrected**タブ。各項目を個別に承認する代わりに使用して、一度にすべての変更を承認することができます、**すべての用語を承認**ツールバー ボタンをクリックします。  
  
5.  切り替えて、**新規**右ペインでタブ。 このタブの値は、DQS で値が正しいかどうかを判断するための十分な情報がナレッジ ベースにない値です。 したがって、ドメイン値を変更したり、変更を提案したりできません。  
  
6.  すべての電子メールで終わることを確認する値を確認**@adventure-works.com**  をクリック**すべての用語を承認**ツールバー。 このタブで承認された値に移動、**修正**タブ。  
  
7.  選択、**国**ドメインの一覧からドメイン。  
  
8.  切り替えて、**修正済み**右側のウィンドウでタブし、ことに注意して**United State**に値が自動的に修正、**米国**での ' 最後にします。 このルールが定義したルール、**国**DQS では、ドメインが**83%** 正しい値があることを確信**米国**します。 **承認**ボタンは自動的にすべての選択、 **Corrected**項目。 この動作をオーバーライドし、変更を拒否できます。  
  
9. 注意して**USA**に修正が**米国**シノニムであるためと**米国**(推奨) の先頭の値です。  
  
     ![修正がシノニムに基づく](../../2014/tutorials/media/et-managingandviewingresults-02.jpg "シノニムに基づいて修正")  
  
10. 注意、**承認**修正された値がこれらのボタンが既に選択されています。 この動作は修正された値に対する既定値です。 変更を却下して、これを行うと、値に移動します。、**無効な**タブ。  
  
11. 選択**Supplier Name**ドメインの一覧から。  
  
12. 切り替えて、 **Corrected**右ペインでタブ。  
  
     ![仕入先名を修正](../../2014/tutorials/media/et-managingandviewingresults-03.jpg "仕入先名を修正しました")  
  
    1.  注意**A. Datum Corp.** に修正が**A. Datum Corporation**と**理由**に設定されている**用語ベースのリレーション。A. datum Corporation** DQS に既知のドメイン値をナレッジ検出プロセス中に検出されたためにです。 そのため、DQS は**100% 確信があります**この修正に関してです。  
  
    2.  注意**Lazy Country Storex**に修正が**Lazy Country Store**、**信頼レベル**に設定されている**100%**、および、 **理由**に設定されている**ドメイン値**します。 設定する、ナレッジ検出プロセス中に**Lazy Country Storex**をエラーとして**Lazy Country Store**として、**修正**ので、DQS は**100%確信**この修正に関してです。  
  
    3.  DQS が一覧で、その他の値に精通していないが、これらの値を使用して修正を検出、**スペル チェッカー**され、適切な修正が提案されます。 DQS は**100%** DQS の修正候補を提示するために、修正を行うためのしきい値のレベルが 80% を超える信頼レベルが、これらの修正に確信が。  
  
13. 注意、**承認**すべての値が自動的に有効にします。 必要に応じて修正値をオーバーライドするか、変更を拒否できます。 既定では、**承認**ですべての値のボタンが選択されている、 **Corrected**タブ。  
  
14. 切り替えて、**新規**タブ。  
  
15. 注意**Corp.** に修正が**Corporation**、 **co.** に修正が**会社**と**Inc.** に修正が**Incorporated**します。 たとえば、 **Consolidate inc.** に修正が**Consolidate Incorporated**と**Consolidated co.** に修正が**Consolidated Company**、および**Frabrikam corp.** に修正が**Fabrikam Corporation**します。  わかります**用語ベースのリレーション**理由と示されています。 これらの変更は、ドメイン管理アクティビティで定義した用語ベースのリレーションに基づいて提案されています。 変更することができます、**に修正**値を手動でここです。  
  
16. スクロール ボックスの一覧に**Hunxgry Coyote Store**に赤い波線。 これを右クリックし、をクリックして**Hungy Coyote Store** (で 'x')。 **に修正**の列を自動的に代入する**Hungry Coyote Store**します。 また、[次に修正] 列の値を手動で入力することもできます。  
  
17. クリックして**すべての用語を承認**ツールバーから。 ドメイン値、**に修正**に指定された値の移動、**修正済み**タブと、新しい値に関連しない**に修正**値に移動、 **正しい**タブ。  
  
18. 選択、 **Address Validation**複合ドメイン ドメインの一覧から。  
  
19. 右側のウィンドウに切り替えると、**修正**タブ。正しいことにあるアドレスを表示する必要があります、 **Melissa Data の Address Check** DQS サービス、 **Azure Marketplace**します。  
  
20. 切り替えて、 **Corrected**タブ。  
  
21. 注意**状態**を持つレコードの**市区町村**として**Los Angeles**に設定されている**CA**ようになりました。 **理由**フィールドは**ルール ' City-State Rule' によって修正**します。  
  
     ![City-State ルールによる修正](../../2014/tutorials/media/et-managingandviewingresults-04.jpg "City-State ルールによる修正")  
  
22. 注意、**承認**オプション ボタンはこの項目の一覧で既に選択されています。 これで項目の既定の動作は、 **Corrected**タブ。  
  
23. 切り替えて、**提案**タブ。によって提案された変更の確認、 **Melissa Data の Address Check**サービス。  
  
24. **承認のすべての用語をクリックします**ツール バー ボタンをクリック**OK**上、**確認**メッセージ ボックス。  
  
     ![すべての用語のツール バー ボタンの承認](../../2014/tutorials/media/et-managingandviewingresults-05.jpg "条項ツール バー ボタンのすべての承認")  
  
25. をクリックして**次**に切り替える、**エクスポート**ページ。  
  
## <a name="next-step"></a>次の手順  
 [タスク 5:クレンジングの結果を Excel ファイルにエクスポートします。](../../2014/tutorials/task-5-exporting-cleansing-results-to-an-excel-file.md)  
  
  
