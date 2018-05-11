---
title: メジャーとメジャー グループ |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c546b8a23ca165c800f1216d5efd666dd1c6e76c
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="measures-and-measure-groups"></a>メジャーおよびメジャー グループ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  キューブには、 *メジャー グループ* 内の *メジャー*、ビジネス ロジック、およびディメンションのコレクション (メジャーが提供する数値のデータを評価するためのコンテキストを指定する) が含まれます。 メジャーおよびメジャー グループはどちらも、キューブに不可欠なコンポーネントです。 キューブは、それぞれが少なくとも 1 つないと存在できません。  
  
 このトピックでは、 [メジャー](#bkmk_measure) と [メジャー グループ](#bkmk_mg)について説明します。 また、メジャーおよびメジャー グループの作成と構成の手順にリンクされている次の表も含まれています。  
  
|**リンク**|**Description**|  
|--------------|---------------------|  
|[多次元モデル内のメジャーおよびメジャー グループを作成します。](../../analysis-services/multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md)|メジャーとメジャー グループを作成するためのいくつかのアプローチのいずれかを選択します。|  
|[メジャーのプロパティを構成します。](../../analysis-services/multidimensional-models/configure-measure-properties.md)|キューブを開始するためにキューブ ウィザードを使用した場合、集計方法を変更し、データ形式を適用し、クライアント アプリケーションでのメジャーの表示/非表示を設定し、場合によっては値の集計前にデータを操作するためのメジャー式を追加する必要があります。|  
|[メジャー グループのプロパティを構成します。](../../analysis-services/multidimensional-models/configure-measure-group-properties.md)|多次元モデルでは、メジャー グループはソースのデータ ウェアハウス内のファクト テーブルに相当します。 メジャー グループでのプロパティにより、キャッシュの動作、記憶域、メジャー グループ レベルでまとめて動作する処理ディレクティブを指定することができます。 パーティション構成の一部は、メジャー グループ オブジェクトに設定するプロパティによって決まります。|  
|[集計関数を使用します。](../../analysis-services/multidimensional-models/use-aggregate-functions.md)|メジャーに割り当てることのできる集計メソッドを理解してください。|  
|[準加法の動作を定義します。](../../analysis-services/multidimensional-models/define-semiadditive-behavior.md)|準加法の動作は、一部のディメンションだけに有効な集計を表します。 一般的な例としては、銀行口座の残高があります。 時間は除外し、顧客と地域によって残高を集計したい場合があります。 たとえば、連続した日々にわたって、同じ口座から残高を加算することはしません。 準加法の動作を定義するには、ビジネス インテリジェンスの追加ウィザードを使用します。|  
|[リンク メジャー グループ](../../analysis-services/multidimensional-models/linked-measure-groups.md)|同じデータベース内、または別の Analysis Services データベース内の他のキューブで、既存のメジャー グループの用途を変更します。|  
  
##  <a name="bkmk_measure"></a> Measures  
 メジャーは、集計できる定量化可能なデータ (通常は数値データ) を含んでいる列を表します。 メジャーは組織のアクティビティの何らかの側面を表すもので、通貨の用語 (売上、利益率、コストなど) で表現されるか、カウント (在庫レベル、従業員、顧客、または注文の数) として表現されるか、またはビジネス ロジックを組み込んだ、より複雑な計算として表現されます。  
  
 すべてのキューブが少なくとも 1 つのメジャーを持っている必要があるものの、多くの場合、メジャーの数は数百に達します。 構造的には、メジャーは多くの場合、メジャーの読み込みに使用される値を提供する列と共に、ファクト テーブル内のソース列にマップされます。 代わりに、MDX を使用してメジャーを定義することもできます。  
  
 メジャーはコンテキスト依存であり、いずれかのディメンション メンバーがクエリに含まれることによって決定されるコンテキストで、数値データに対して動作します。 たとえば、 **再販業者の売上** を計算するメジャーは **Sum** 演算子の支援を受け、クエリに含まれるディメンション メンバーごとに売り上げ高を加算します。 クエリで個々の製品を指定するかどうか、カテゴリにロールアップするかどうか、また時間や場所によってスライスされるかに応じて、メジャーはクエリに含まれるディメンションに対して有効な操作を生成します。  
  
 この例では、 **Sales Territory** 階層に沿ったさまざまなレベルに **再販業者の売上** を集計します。  
  
 ![ピボット テーブルにメジャーとディメンションが呼び出された](../../analysis-services/multidimensional-models/media/ssas-keyconcepts-pivot1-measures-dimensions.png "にメジャーとディメンションが呼び出されたピボット テーブル")  
  
 メジャーは、数値のソース データを含むファクト テーブルに、クエリで使用されているディメンション テーブルへのポインターも含まれているときに、有効な結果を生成します。 Reseller Sales の例で説明すると、売り上げ高を格納する行ごとに製品テーブル、日付テーブル、または販売区域のテーブルへのポインターも格納されている場合には、それらのディメンションからのメンバーが含まれるクエリが正しく解決されます。  
  
 メジャーがクエリで使用されるディメンションに関連付けられていないと、どうなるでしょうか。 通常、Analysis Services は、既定のメジャーを表示し、値はすべてのメンバーで同じになります。 この例では、オンライン カタログを使用して顧客によって行われる直販を測定する **Internet Sales**は、販売組織に関連付けられていません。  
  
 ![繰り返し表示するピボット テーブルで値が測定](../../analysis-services/multidimensional-models/media/ssas-unrelatedmeasure.PNG "繰り返し表示するピボット テーブルのメジャーの値")  
  
 クライアント アプリケーションでこれらの動作が発生する可能性を最小限に抑えるには、複数のキューブまたはパースペクティブを同じデータベース内で構築し、各キューブまたはパースペクティブに、関連するオブジェクトのみが含まれるようにします。 確認する必要がある関係は、(ファクト テーブルにマップする) メジャー グループと、ディメンションの間の関係です。  
  
##  <a name="bkmk_mg"></a> Measure Groups  
 キューブでは、メジャーは基になるファクト テーブルによってメジャー グループにグループ化されます。 メジャー グループは、ディメンションをメジャーに関連付けるために使用されます。 メジャー グループは、集計動作として個別のカウントを持っているメジャーにも使用されます。 各個別のカウント メジャーをそれぞれ独自のメジャー グループに配置すると、集計処理が最適化されます。  
  
 単純な <xref:Microsoft.AnalysisServices.MeasureGroup> オブジェクトは、グループ名、ストレージ モード、および処理モードなどの基本情報で構成されます。 その構成要素として、メジャー、ディメンション、およびメジャー グループの構成を形成するパーティションも、それに含まれます。  
  
## <a name="see-also"></a>参照  
 [多次元モデル内のキューブ](../../analysis-services/multidimensional-models/cubes-in-multidimensional-models.md)   
 [多次元モデル内のメジャーおよびメジャー グループを作成します。](../../analysis-services/multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md)  
  
  
