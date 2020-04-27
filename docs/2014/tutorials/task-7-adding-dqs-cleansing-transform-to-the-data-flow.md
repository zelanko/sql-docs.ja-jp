---
title: 'タスク 7: DQS クレンジング変換をデータフローに追加する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 0b749c71-dfb6-493a-804f-600290d46eef
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 209659609c2cf19196cc35050fb32e39e079d1c7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "65488943"
---
# <a name="task-7-adding-dqs-cleansing-transform-to-the-data-flow"></a>タスク 7: DQS クレンジング変換をデータ フローに追加する
  ここでは、DQS クレンジング変換をデータ フローに追加して、入力済みの仕入先データを DQS を使用してクレンジングします。 変換の詳細については、「 **[DQS クレンジング変換](https://msdn.microsoft.com/library/ee677619.aspx)**」を参照してください。  
  
1.  [**データフロー** ] タブで [ **DQS クレンジング**] を右クリックし、[**名前の変更**] をクリックします。 「**クレンジング Supplier Data**」と入力し、 **enter**キーを押します。  
  
2.  [ **Excel ファイルから Supplier データを読み取る**] を選択します。blue コネクタをドラッグして、**仕入先データをクレンジング**します。 これでコンポーネントが接続されました。  
  
     ![Supplier データの読み取り-Supplier データのクレンジング >](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-01.jpg "仕入先データの読み取り -> 仕入先データのクレンジング")  
  
3.  [**仕入先データのクレンジング**] をダブルクリックします。  
  
4.  [ **DQS クレンジング変換エディター**] で、[**データ品質接続マネージャー] ボックスの一覧**の横にある [**新規**] をクリックします。  
  
5.  [ **DQS クレンジング接続マネージャー** ] ダイアログボックスで、ローカルサーバーに接続する場合は「 **(local)** 」または「**ピリオド**(.)」と入力します。 このレッスンは、ローカル サーバーに DQS がインストールされていることを前提としています。  
  
6.  [**テスト接続**] をクリックして DQS サーバーへの接続をテストします。  
  
7.  **[OK]** をクリックしてダイアログ ボックスを閉じます。  
  
8.  **データ品質ナレッジベース**の [**仕入先**] を選択します。  
  
     ![DQS クレンジング変換エディター - 仕入先 KB](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-02.jpg "DQS クレンジング変換エディター - 仕入先 KB")  
  
9. 上部の [**マッピング**] タブに切り替えます。  
  
10. [**使用できる入力列**] で、チェックボックスをオンにして [ **Supplier Name**]、[ **ContactEmailAddress**]、[ **Address Line** **]、[****市区町村**]、[ **Country**]、[**郵便**番号] を選択します。  
  
     ![DQS クレンジング変換エディター - マッピング](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-03.jpg "DQS クレンジング変換エディター - マッピング")  
  
11. 下のペインで、[**ドメイン**] 列のドロップダウンリストを使用してこれらの列をマップします。  
  
    |列|ドメイン|  
    |------------|------------|  
    |Supplier Name|Supplier Name|  
    |ContactEmailAddress|連絡先のメール アドレス|  
    |Address Line|Address Line|  
    |City|City|  
    |State|State|  
    |Country|Country|  
    |Zip Code|Zip|  
  
12. [ **OK]** をクリックして [ **DQS クレンジング変換エディター** ] ダイアログボックスを閉じます。  
  
## <a name="next-step"></a>次の手順  
 [タスク 8: 条件分割変換を追加してクレンジング出力を分割する](../../2014/tutorials/task-8-adding-conditional-split-transform-to-split-cleansing-output.md)  
  
  
