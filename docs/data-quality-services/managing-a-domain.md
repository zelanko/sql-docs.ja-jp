---
title: "ドメインの管理 | Microsoft Docs"
ms.custom: ""
ms.date: "07/31/2012"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c5ab71a3-0dac-45b1-be8e-93bf7e0e03ce
caps.latest.revision: 13
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 13
---
# ドメインの管理
  このトピックでは、[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) でのドメインの使用について説明します。 ドメインは、分析対象のデータ ソースの特定のフィールドに含まれているデータのセマンティック表現です。 ドメインは、データ ソースに対して作成するナレッジ ベースの一部で、サンプル データ ソースを分析するか、データをインポートして構築するナレッジは、ナレッジ ベースで定義されたドメインに追加されます。 これらのドメインのナレッジは、データ品質プロジェクトでクレンジングおよび照合を実行するために後で使用されます。 ドメインは、Data Quality Services のすべてのアクティビティの中核になります。  
  
 ドメインは、データ ソース フィールドにマップされ、ナレッジ検出、ドメイン管理、および照合の各アクティビティで作成されます。 データ ソースからデータを読み込む方法とレポートにデータを出力する方法は、ドメインのプロパティで定義します。 参照データ プロバイダーを使用してデータをクレンジングする場合は、参照データ サービスを単一または複合ドメインにアタッチします。 ドメインのデータに適用されるルールを作成すると、ドメインに対する用語ベースのリレーションを作成できます。 ドメインのデータを表示および修正できます。  
  
 共通データに関するナレッジを含む 2 つ以上の個別のドメインで構成される複合ドメインを作成することもできます。 詳細については、次を参照してください。 [複合ドメインの管理](../data-quality-services/managing-a-composite-domain.md)します。  
  
## ドメインのプロパティ  
 ドメインを作成する際には、ソース データからドメインを作成する方法とドメイン値を出力する方法に関する次のオプションがあります。 詳細については、次を参照してください。 [ドメイン プロパティの設定](../data-quality-services/set-domain-properties.md)します。  
  
-   ドメインの作成に使用するデータの型を選択します。 各ドメインのデータ型のサポートされるデータ型については、次を参照してください。 [サポートされている SQL Server と SSIS の DQS ドメインのデータ型](../data-quality-services/supported-sql-server-and-ssis-data-types-for-dqs-domains.md)します。  
  
-   シノニムではなく先頭の値のみがドメインから出力されるように指定します。  
  
-   ドメイン値がデータ型に応じて特定の形式で出力されるように指定します。  
  
-   データ型が文字列の場合は、文字列がデータ ソースからドメインに読み込まれるときに特殊文字を削除することによって文字列を正規化します。  
  
-   データ型が文字列の場合は、構文、スペル チェック、および、文字列の文の構造をチェックする DQS スペル チェックを実行しで潜在的なエラーを示す、 **ドメイン値** のページ **ドメイン管理**します。 これには、スペル チェックを実行する言語の指定が含まれます。  
  
-   データ型が文字列で、構文エラーが文字列で発生しないことがわかっている場合は、DQS が構文エラーを識別しないように指定できます。  
  
## このセクションの内容  
 ドメインを使用すると、次の操作を実行できます。  
  
|||  
|-|-|  
|特定のデータ型を持つデータ フィールドのセマンティック表現を作成し、ドメインの作成方法を指定して、ドメインの出力形式を設定する|[ドメインの作成](../data-quality-services/create-a-domain.md)|  
|ドメインを別のドメインにリンクして、ドメインが同じ設定と値を共有できるようにする|[リンク ドメインの作成](../data-quality-services/create-a-linked-domain.md)|  
|参照データ サービスを単一または複合ドメインにアタッチする|[参照データへのドメインまたは複合ドメインのアタッチ](../data-quality-services/attach-domain-or-composite-domain-to-reference-data.md)|  
|ナレッジ ベース内の値を変更または拡張する|[ドメイン値の変更](../data-quality-services/change-domain-values.md)|  
|検証と標準化の規則を使用する|[Create a Domain Rule](../data-quality-services/create-a-domain-rule.md)|  
|リレーションを使用してドメインの値の一部である用語を修正する|[Create Term-Based Relations](../data-quality-services/create-term-based-relations.md)|  
|ドメイン管理アクティビティを完了、終了、またはキャンセルする|[ドメイン管理アクティビティの終了](../Topic/End%20the%20Domain%20Management%20Activity.md)|  
  
## 関連タスク  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|ナレッジ検出を実行し、対話方式でナレッジを管理して、ナレッジ ベースを構築します。|[ナレッジ ベースの作成](../data-quality-services/building-a-knowledge-base.md)|  
|ナレッジをナレッジ ベースにインポートするか、ナレッジ ベースからナレッジをエクスポートします。|[ナレッジのインポートとエクスポート](../data-quality-services/importing-and-exporting-knowledge.md)|  
|複合ドメインを作成し、ナレッジをドメインに追加します。|[複合ドメインの管理](../data-quality-services/managing-a-composite-domain.md)|  
  
  