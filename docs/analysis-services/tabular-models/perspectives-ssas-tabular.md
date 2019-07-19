---
title: Analysis Services 表形式モデルのパースペクティブ |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dc6b574702f71a70de842c3a3b51110e8eed9814
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207620"
---
# <a name="perspectives-in-tabular-models"></a>表形式モデルのパースペクティブ
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  テーブル モデルでパースペクティブを使用すると、ビジネス固有またはアプリケーション固有のビューポイントをモデルに対して的を絞って作成するための、表示可能なサブセットを定義できます。  
  
##  <a name="bkmk_understanding"></a> 利点  
 テーブル モデルは非常に複雑であるために、扱いが困難なことがあります。 テーブル モデルは、1 つだけで多くのテーブル、メジャー、ディメンションを持つ完全なデータ ウェアハウスの内容を表すことができます。 しかしこのような複雑さは、ビジネス インテリジェンス要件やレポート要件を満たすために、モデルのごく一部分しか操作する必要のないユーザーにとっては大きな負担になります。  
  
 パースペクティブでは、テーブル、列、およびメジャー (KPI を含む) がフィールド オブジェクトとして定義されます。 パースペクティブごとに複数の表示可能なフィールドを選択できます。 たとえば、1 つのモデルに商品、売上、財務、従業員、および地域のデータが含まれている場合があります。 販売部門では商品、売上、プロモーション、地域のデータは必要ですが、従業員や財務のデータはおそらく必要ありません。 同様に、人事部門では販売プロモーションや地域のデータは必要ありません。  
  
 パースペクティブが定義されたモデルに (データ ソースとして) 接続する際、ユーザーは使用するパースペクティブを選択できます。 たとえば、Excel のモデル データ ソースに接続する際、人事部門のユーザーはデータ接続ウィザードの [テーブルとビューの選択] ページにある人事パースペクティブを選択できます。 ピボットテーブルのフィールド一覧には、人事パースペクティブに定義されたフィールド (テーブル、列、およびメジャー) のみが表示されます。  
  
 パースペクティブは、セキュリティ メカニズムとして使用するためのものではなく、ユーザーの使用体験をより良いものにするためのツールとして使用するものです。 特定のパースペクティブのセキュリティはすべて、基になるモデルから継承されます。 パースペクティブでは、ユーザーがアクセス権を持っていないモデル オブジェクトにアクセスできません。 パースペクティブでモデルのオブジェクトへのアクセスが提供されるようにするには、そのモデル データベースのセキュリティを解決しておく必要があります。 セキュリティ ロールを使用して、モデルのメタデータとデータをセキュリティ保護することができます。 詳細については、次を参照してください。[ロール](../../analysis-services/tabular-models/roles-ssas-tabular.md)します。  
  
##  <a name="bkmk_testpersp"></a> Testing perspectives  
 モデルの作成時に、モデル デザイナーの Excel で分析機能を使用して、定義したパースペクティブの有効性をテストできます。 モデル デザイナーで **[モデル]** メニューの **[Excel で分析]** をクリックすると、Excel が開く前に **[資格情報とパースペクティブの選択]** ダイアログ ボックスが表示されます。 このダイアログ ボックスでは、データ ソースとしてモデル ワークスペース データベースに接続し、データを表示するために使用する、現在のユーザー名、別のユーザー、ロール、およびパースペクティブを指定できます。  
  
##  <a name="bkmk_related_tasks"></a> 関連タスク  
  
|トピック|説明|  
|-----------|-----------------|  
|[パースペクティブの作成と管理](../../analysis-services/tabular-models/create-and-manage-perspectives-ssas-tabular.md)|モデル デザイナーで [パースペクティブ] ダイアログ ボックスを使用して、パースペクティブを作成し管理する方法を説明します。|  
  
## <a name="see-also"></a>参照  
 [ロール](../../analysis-services/tabular-models/roles-ssas-tabular.md)   
 [階層](../../analysis-services/tabular-models/hierarchies-ssas-tabular.md)  
  
  
