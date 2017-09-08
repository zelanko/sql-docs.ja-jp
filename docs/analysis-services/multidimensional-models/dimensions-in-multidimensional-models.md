---
title: "多次元モデル内のディメンション |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OLAP [Analysis Services], dimensions
- dimensions [Analysis Services], about dimensions
- OLAP objects [Analysis Services], dimensions
ms.assetid: 2b62b05c-00fd-4e60-b77f-f707ba83a19b
caps.latest.revision: 46
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3e98c77a6b243bd5890aac6612db663377bd1bb3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="dimensions-in-multidimensional-models"></a>多次元モデル内のディメンション
  データベース ディメンションとは、ファクト データに関する情報を 1 つまたは複数のキューブで提供するための、属性と呼ばれる関連オブジェクトが集まったものです。 たとえば、Product ディメンションの一般的な属性としては、製品名、製品カテゴリ、製品ライン、製品サイズ、製品価格などがあります。 これらのオブジェクトは、データ ソース ビューのテーブル内の列にバインドされており、 既定では、これらの属性は、属性階層として表示され、キューブ内のファクト データを理解する際に使用できます。 属性はユーザー定義階層にまとめることができます。これらの階層には、ユーザーがキューブ内のデータを参照する際に使用できるナビゲーション パスが含まれています。  
  
 キューブには、ユーザーがファクト データの分析の基準として使用する、すべてのディメンションが含まれています。 キューブ内のデータベース ディメンションのインスタンスは、キューブ ディメンションと呼ばれ、キューブ内の 1 つ以上のメジャー グループに関連しています。 データベース ディメンションは、キューブで何度も使用できます。 たとえば、ファクト テーブルに時間関連のファクトが複数含まれている場合は、時間関連の各ファクトを分析するために別々のキューブ ディメンションを定義できます。 ただし、時間関連のデータベース ディメンションは 1 つしか必要ありません。つまり、時間に基づく複数のキューブ ディメンションをサポートするために、時間関連のリレーショナル データベースも 1 つしか必要となりません。  
  
> [!NOTE]  
>  ディメンション デザインに関連するパフォーマンスの問題については、「 [SQL Server 2008 R2 Analysis Services パフォーマンス ガイド](http://go.microsoft.com/fwlink/?LinkId=306717)」を参照してください。  
  
## <a name="defining-dimensions-attributes-and-hierarchies"></a>ディメンション、属性、および階層の定義  
 データベースとキューブのディメンション、属性、および階層を定義するための最も簡単な方法は、キューブ ウィザードを使用して、キューブの定義と同時にディメンションを作成することです。 キューブ ウィザードでは、データ ソース ビューのディメンション テーブルに基づいてディメンションを作成します。このディメンション テーブルは、キューブで使用するために、ウィザードで指定されたり、ユーザーが指定したりします。 その後、データベース ディメンションを作成して新しいキューブに追加すると、キューブ ディメンションが作成されます。  
  
 キューブを作成するときは、データベースに既に存在するディメンションを新しいキューブに追加することもできます。 これらのディメンションは、別のキューブやディメンション ウィザードで以前に定義されている場合があります。 データベース ディメンションは、定義した後に、ディメンション デザイナーで変更および構成できます。 またキューブ ディメンションは、キューブ デザイナーで、限られた範囲内でカスタマイズできます。  
  
> [!NOTE]  
>  XMLA または分析管理オブジェクト (AMO) のいずれかを使用すると、ディメンション、属性、および階層をプログラムによってデザインおよび構成することもできます。 詳細については、「[Analysis Services スクリプト言語 (XMLA 用 ASSL)](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)」および「[分析管理オブジェクト (AMO) による開発](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 このトピックでは、次の内容について紹介します。  
  
 [データベース ディメンションの定義](../../analysis-services/multidimensional-models/define-database-dimensions.md)  
 ディメンション デザイナーを使用して、データベース ディメンションを変更および構成する方法について説明します。  
  
 [ディメンションの属性のプロパティの参照](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
 ディメンション デザイナーを使用して、データベース ディメンションの属性を定義、変更、および構成する方法について説明します。  
  
 [属性リレーションシップの定義](../../analysis-services/multidimensional-models/attribute-relationships-define.md)  
 ディメンション デザイナーを使用して、属性リレーションシップを定義、変更、および構成する方法について説明します。  
  
 [ユーザー定義階層の作成](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)  
 ディメンション デザイナーを使用してユーザー定義階層のディメンション属性を定義、変更、および構成する方法について説明します。  
  
 [ビジネス インテリジェンス ウィザードを使用したディメンションの拡張](http://msdn.microsoft.com/library/12d995d1-75ca-4890-bf4b-a2656910b8d0)  
 ビジネス インテリジェンス ウィザードを使用して、データベース ディメンションを拡張する方法について説明します。  
  
## <a name="see-also"></a>参照  
 [多次元モデルのキューブ](../../analysis-services/multidimensional-models/cubes-in-multidimensional-models.md)  
  
  
