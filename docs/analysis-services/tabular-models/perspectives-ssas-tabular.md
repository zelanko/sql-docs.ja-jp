---
title: "パースペクティブ (SSAS テーブル) |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f78c3a1-ce2c-4e7f-a277-71a657692bea
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a9c1ad93e5c4af1736721436f4ce5116ac279934
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="perspectives"></a>パースペクティブ
  テーブル モデルでパースペクティブを使用すると、ビジネス固有またはアプリケーション固有のビューポイントをモデルに対して的を絞って作成するための、表示可能なサブセットを定義できます。  
  
##  <a name="bkmk_understanding"></a> 利点  
 テーブル モデルは非常に複雑であるために、扱いが困難なことがあります。 テーブル モデルは、1 つだけで多くのテーブル、メジャー、ディメンションを持つ完全なデータ ウェアハウスの内容を表すことができます。 しかしこのような複雑さは、ビジネス インテリジェンス要件やレポート要件を満たすために、モデルのごく一部分しか操作する必要のないユーザーにとっては大きな負担になります。  
  
 パースペクティブでは、テーブル、列、およびメジャー (KPI を含む) がフィールド オブジェクトとして定義されます。 パースペクティブごとに複数の表示可能なフィールドを選択できます。 たとえば、1 つのモデルに商品、売上、財務、従業員、および地域のデータが含まれている場合があります。 販売部門では商品、売上、プロモーション、地域のデータは必要ですが、従業員や財務のデータはおそらく必要ありません。 同様に、人事部門では販売プロモーションや地域のデータは必要ありません。  
  
 パースペクティブが定義されたモデルに (データ ソースとして) 接続する際、ユーザーは使用するパースペクティブを選択できます。 たとえば、Excel のモデル データ ソースに接続する際、人事部門のユーザーはデータ接続ウィザードの [テーブルとビューの選択] ページにある人事パースペクティブを選択できます。 ピボットテーブルのフィールド一覧には、人事パースペクティブに定義されたフィールド (テーブル、列、およびメジャー) のみが表示されます。  
  
 パースペクティブは、セキュリティ メカニズムとして使用するためのものではなく、ユーザーの使用体験をより良いものにするためのツールとして使用するものです。 特定のパースペクティブのセキュリティはすべて、基になるモデルから継承されます。 パースペクティブでは、ユーザーがアクセス権を持っていないモデル オブジェクトにアクセスできません。 パースペクティブでモデルのオブジェクトへのアクセスが提供されるようにするには、そのモデル データベースのセキュリティを解決しておく必要があります。 セキュリティ ロールを使用して、モデルのメタデータとデータをセキュリティ保護することができます。 詳細については、次を参照してください。[ロール](../../analysis-services/tabular-models/roles-ssas-tabular.md)です。  
  
##  <a name="bkmk_testpersp"></a> Testing perspectives  
 モデルの作成時に、モデル デザイナーの Excel で分析機能を使用して、定義したパースペクティブの有効性をテストできます。 モデル デザイナーで **[モデル]** メニューの **[Excel で分析]**をクリックすると、Excel が開く前に **[資格情報とパースペクティブの選択]** ダイアログ ボックスが表示されます。 このダイアログ ボックスでは、データ ソースとしてモデル ワークスペース データベースに接続し、データを表示するために使用する、現在のユーザー名、別のユーザー、ロール、およびパースペクティブを指定できます。  
  
##  <a name="bkmk_related_tasks"></a> Related tasks  
  
|トピック|Description|  
|-----------|-----------------|  
|[作成し、パースペクティブの管理](../../analysis-services/tabular-models/create-and-manage-perspectives-ssas-tabular.md)|モデル デザイナーで [パースペクティブ] ダイアログ ボックスを使用して、パースペクティブを作成し管理する方法を説明します。|  
  
## <a name="see-also"></a>参照  
 [ロール](../../analysis-services/tabular-models/roles-ssas-tabular.md)   
 [階層](../../analysis-services/tabular-models/hierarchies-ssas-tabular.md)  
  
  

