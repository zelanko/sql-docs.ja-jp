---
title: "手順 8: 容易レッスン 1 のパッケージを理解する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: e3751e53-77c7-47d0-8fe8-73ed1a53413a
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 55bd386054f3a7d066dc8c28c13e22ae82e9f0cb
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="lesson-1-8---making-the-lesson-1-package-easier-to-understand"></a>レッスン 1 ~ 8-レッスン 1 のパッケージを容易に理解します。
ここまでの作業で、レッスン 1 のパッケージの構成が完了しました。次は、パッケージのレイアウトを整理することをお勧めします。 制御フローやデータ フローのレイアウトの図形サイズがまちまちであったり、図形の整列やグループ化が行われていないと、パッケージの機能がわかりにくくなることがあります。  
  
[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools には、パッケージのレイアウトをすばやく簡単に書式設定できるツールが用意されています。 この書式設定機能を使用すると、複数の図形を同じサイズにしたり、整列したり、図形間の上下左右の間隔を操作することができます。  
  
パッケージの機能をわかりやすくするには、パッケージ機能について説明した注釈を追加するという方法もあります。  
  
この実習では、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools の書式設定機能を使用してデータ フローのレイアウトを改善し、さらにデータ フローに注釈を追加します。  
  
### <a name="to-format-the-layout-of-the-data-flow"></a>データ フローのレイアウトを書式設定するには  
  
1.  レッスン 1 のパッケージを開いていない場合は、ソリューション エクスプローラーで Lesson 1.dtsx をダブルクリックします。  
  
2.  **[データ フロー]** タブをクリックします。  
  
3.  Extract Sample Currency 変換の右上隅にカーソルを合わせ、クリックしてすべてのデータ フロー コンポーネントを囲むようにドラッグします。  
  
4.  **[書式]** メニューの **[同じサイズに揃える]**をポイントし、 **[両方]**をクリックします。  
  
5.  データ フロー オブジェクトが選択されている状態で、 **[書式]** メニューの **[整列]**をポイントし、 **[左]**をクリックします。  
  
### <a name="to-add-an-annotation-to-the-data-flow"></a>データ フローに注釈を追加するには  
  
1.  データ フローのデザイン画面の背景で任意の場所を右クリックし、 **[注釈の追加]**をクリックします。  
  
2.  注釈ボックスに、次のテキストを入力するか、コピーして貼り付けます。  
  
    **このデータ フローは、ファイルからデータを抽出し、DimCurrency テーブルの CurrencyKey 列の値と DimDate テーブルの DateKey 列の値を参照して、データを NewFactCurrencyRate テーブルに書き込みます。**  
  
    注釈ボックスのテキストを折り返すには、改行する場所にカーソルを置いて、Enter キーを押します。  
  
    注釈ボックスにテキストを追加しない場合は、注釈ボックスの外側をクリックするとボックスは表示されなくなります。  
  
## <a name="next-steps"></a>次の手順  
[手順 9: レッスン 1 のチュートリアル パッケージのテスト](../integration-services/lesson-1-9-testing-the-lesson-1-tutorial-package.md)  
  
  
  

