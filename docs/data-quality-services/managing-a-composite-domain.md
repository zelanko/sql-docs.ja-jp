---
title: "複合ドメインの管理 | Microsoft Docs"
ms.custom: 
ms.date: 07/31/2012
ms.prod: sql-non-specified
ms.prod_service: data-quality-services
ms.service: 
ms.component: data-quality-services
ms.reviewer: 
ms.suite: sql
ms.technology:
- data-quality-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47821eff-800b-4053-8d36-e42bbc267f54
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 32a0bb0592614c496a3ceff5a3cfa82f73032d9f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="managing-a-composite-domain"></a>複合ドメインの管理
  このトピックでは、 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) での複合ドメインの使用について説明します。 単一ドメインでは 1 つのフィールド内のデータを十分に表せないことがあります。また、単一ドメインをグループ化しないとデータを表すことはできません。 これを行うには、複合ドメインを作成します。 複合ドメインは 2 つ以上の単一ドメインで構成され、解析されないが単一の複合値に含まれる複数の関連用語で構成されるデータ フィールドにマップされます。 値の各用語は、それぞれ異なる単一ドメインで表されます。 単一ドメインを複合ドメインに含めた後に、複合ドメインをデータ フィールドにマップすると、単一ドメインでナレッジを構築して、そのフィールド内のデータに関するナレッジ ベースにナレッジを構築できます。 複合ドメインは、単一ドメインと同様に、1 つのデータ フィールド内のデータのセマンティック表現です。  
  
 複合ドメイン内の単一のドメインには、ナレッジの共通領域が必要です。 たとえば、番地、市区町村、都道府県、国、および郵便番号データを含む住所フィールドがあります。 このフィールドの各用語はそれぞれデータ型が異なる場合があります。 この場合は、これらの用語を複数の異なる単一ドメインにマップします。 また、名前、ミドル ネーム、および姓のデータを含む氏名フィールドもあります。 複合ドメインを使用するには、フィールド内のデータを複数の異なる単一ドメインに解析し、フィールドの複合ドメインとフィールドの一部に対する単一ドメインを作成できる必要があります。  
  
 複合ドメインには、単一ドメインとは異なる機能があります。 複合ドメインで値は変更できません。値の変更は単一ドメインで行う必要があります。 複合ドメインでは、クロス ドメイン ルールを使用して、複合ドメインの単一ドメインで値をテストできます。 複合ドメイン内にある値の組み合わせを表示することもできます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 複合ドメインを使用して、次の操作を実行できます。  
  
|||  
|-|-|  
|解析されない複数の関連用語で構成されるデータ フィールドのセマンティック表現を作成します。|[複合ドメインを作成する](../data-quality-services/create-a-composite-domain.md)|  
|複合データを複合ドメインにマッピングする場合は、区切り記号での解析に加えて、ナレッジに基づいてデータを解析できます。 DQS では最初に単一ドメインに関するナレッジを使用して、複合文字列の各部分が単一ドメインにどのように属しているか確認します。|[複合ドメインを作成する](../data-quality-services/create-a-composite-domain.md)|  
|住所データを処理するサービスなどの参照データ サービスを複合ドメインにアタッチします。|[参照データにドメインまたは複合ドメインをアタッチする](../data-quality-services/attach-domain-or-composite-domain-to-reference-data.md)|  
|複合ドメイン内の 1 つのドメインの値が別のドメインの値に影響する場合は、クロス ドメイン ルールを作成します。|[クロス ドメイン ルールを作成する](../data-quality-services/create-a-cross-domain-rule.md)|  
|DQS で周波数が報告されるように値の組み合わせを指定します。|[複合ドメインで値のリレーションを使用する](../data-quality-services/use-value-relations-in-a-composite-domain.md)|  
  
## <a name="related-tasks"></a>関連タスク  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|ナレッジ検出を実行し、対話方式でナレッジを管理して、ナレッジ ベースを構築します。|[ナレッジ ベースの作成](../data-quality-services/building-a-knowledge-base.md)|  
|ナレッジをナレッジ ベースにインポートするか、ナレッジ ベースからナレッジをエクスポートします。|[ナレッジのインポートとエクスポート](../data-quality-services/importing-and-exporting-knowledge.md)|  
|単一ドメインを作成し、ナレッジをドメインに追加します。|[ドメインの管理](../data-quality-services/managing-a-domain.md)|  
  
  

