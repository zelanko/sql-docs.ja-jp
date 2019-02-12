---
title: ソース コール センター データ (中級者向けデータ マイニング チュートリアル) ビューのデータの追加 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a448e7e4-dbd1-4d31-90bc-4d4a1c23b352
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 5da7978db04b0fdf6e1d4f7740857fc5c0cf90ed
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56035043"
---
# <a name="adding-a-data-source-view-for-call-center-data-intermediate-data-mining-tutorial"></a>コール センター データ用のデータ ソース ビューの追加 (中級者向けデータ マイニング チュートリアル)
  ここでは、コール センター データへのアクセスに使用するデータ ソース ビューを追加します。 最初に調査用のニューラル ネットワーク モデルを構築し、その後、提案作成用のロジスティック回帰モデルを構築します。どちらのモデルにも、同じデータを使用します。  
  
 さらに、データ ソース ビュー デザイナーを使用して曜日の列を追加します。 これは、ソース データによってコール センター データを日付別に追跡していますが、問い合わせ件数とサービス品質にはどちらも、週末か平日かによって定期的なパターンがあることが経験上わかっているためです。  
  
## <a name="procedures"></a>手順  
  
#### <a name="to-add-a-data-source-view"></a>データ ソース ビューを追加するには  
  
1.  **ソリューション エクスプローラー**で **[データ ソース ビュー]** を右クリックし、 **[新しいデータ ソース ビュー]** をクリックします。  
  
     データ ソース ビュー ウィザードが開きます。  
  
2.  **[データ ソース ビュー ウィザードへようこそ]** ページで **[次へ]** をクリックします。  
  
3.  **データ ソースの選択**] ページ [**リレーショナル データ ソース**を選択、[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]データ ソース。 このデータ ソースがないを参照してください。 [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md)します。 **[次へ]** をクリックします。  
  
4.  **テーブルおよびビュー**ページで、次の表を選択し、データ ソース ビューに追加する、右矢印をクリックします。  
  
    -   **FactCallCenter (dbo)**  
  
    -   **DimDate**  
  
5.  **[次へ]** をクリックします。  
  
6.  **ウィザードの完了** ページで、既定では、データ ソース ビューの名前は[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]します。 名を変更して**CallCenter**、 をクリックし、**完了**します。  
  
     表示するデータ ソース ビュー デザイナーが開き、 **CallCenter**データ ソース ビュー。  
  
7.  データ ソース ビュー ウィンドウ内で右クリックして**テーブルの追加/削除**します。 テーブルを選択**DimDate**クリック**OK**。  
  
     間で、リレーションシップを自動的に追加する必要があります、`DateKey`各テーブル内の列。 このリレーションシップを使用して、列を取得するが**EnglishDayNameOfWeek**から、 **DimDate**テーブルが表示され、モデルで使用します。  
  
8.  データ ソース ビュー デザイナーで、テーブルを右クリックして**FactCallCenter**、選択および**新しい名前付き計算**します。  
  
     **名前付き計算の作成** ダイアログ ボックスに、次の値を入力します。  
  
    |||  
    |-|-|  
    |**列名**|DayOfWeek|  
    |**[説明]**|DimDate テーブルから曜日を取得。|  
    |**[式]**|`(SELECT EnglishDayNameOfWeek AS DayOfWeek FROM DimDate where FactCallCenter.DateKey = DimDate.DateKey)`|  
  
     式に、データが作成されることを確認する必要があります、テーブルを右クリックして**FactCallCenter**、し、**データの探索**します。  
  
9. データ マイニングでの使用方法を理解するために、使用可能なデータを少し時間をかけて確認します。  
  
|列名|[値を含む]|  
|-----------------|--------------|  
|FactCallCenterID|データ ウェアハウスにデータがインポートされたときに作成される任意のキー。<br /><br /> この列は一意のレコードを識別する列で、データ マイニング モデルのケース キーとして使用されます。|  
|DateKey|コール センター業務の日付 (整数値)。 データ ウェアハウスでは日付のキーに整数がよく使用されますが、日付の値でグループ化する場合は、日付/時刻の形式で日付を取得することもできます。<br /><br /> ベンダーからは日々、シフトごとに別個のレポートが提供されるため、日付は一意ではありません。|  
|WageType|日付が平日、週末や祝日がかどうかを示します。<br /><br /> ある顧客サービスの品質の違い平日と週末にため、この列の入力として使用することができます。|  
|shift キー|問い合わせが記録されるシフトを示します。 このコール センターでは、4 つのシフトに稼働日が分かれています。AM、PM1、PM2、午前 0 時です。<br /><br /> カスタマー サービスの質がシフトによって異なる可能性があるため、この列を入力として使用します。|  
|LevelOneOperators|勤務時間外のレベル 1 の演算子の数を示します。<br /><br /> コール センターの従業員のレベルはレベル 1 から始まるため、このレベルの従業員は経験が浅い従業員です。|  
|LevelTwoOperators|勤務しているレベル 2 オペレーターの人数を示します。<br /><br /> 従業員は、レベル 2 オペレーターとして限定するためのサービス時間数を記録する必要があります。|  
|TotalOperators|シフト中に勤務しているオペレーターの人数の合計。|  
|Calls|シフト中に受けた問い合わせの件数。|  
|AutomaticResponses|完全に自動呼処理 (対話型音声応答、IVR) によって処理された問い合わせの件数。|  
|Orders|問い合わせの結果として発生した注文の件数。|  
|IssuesRaised|問い合わせによって発生した、フォローアップが必要な案件の件数。|  
|AverageTimePerIssue|問い合わせの電話への応対に要した平均時間。|  
|ServiceGrade|サービスの全体的な質を示すメトリックの単位として、*破棄率*全体をシフトします。 電話放棄呼率が高いほど、顧客の満足度が低下し、注文の機会を失う可能性が高くなります。|  
  
 データが 1 つの日付列に基づく 4 つの異なる列が含まれることに注意してください: `WageType`、 **DayOfWeek**、 `Shift`、および`DateKey`します。 通常、データ マイニングでは、同じデータから派生する列を複数使用することはお勧めしません。それらの値の間の関連が強すぎて、他のパターンがわかりにくくなることがあるからです。  
  
 ただし、私たちは使用しません`DateKey`モデルの一意の値が多すぎますが含まれています。 直接的な関係はありません`Shift`と**DayOfWeek**、および`WageType`と**DayOfWeek**は部分的にのみ関連します。 共線性について気にかかる場合は、使用可能なすべての列を使用して構造を作成し、モデルごとに無視する列を変えて影響をテストしてみてください。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [ニューラル ネットワーク構造およびモデルの作成&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/creating-a-neural-network-structure-and-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [「多次元モデルのデータ ソース ビュー」](../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  
