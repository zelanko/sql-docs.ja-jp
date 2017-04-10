---
title: "Analysis Services での翻訳のサポート | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Business Intelligence Development Studio、翻訳 [Analysis Services]"
  - "翻訳 [Analysis Services]、翻訳について"
  - "オブジェクト翻訳 [Analysis Services]"
  - "言語識別子 [Analysis Services]"
  - "属性翻訳 [Analysis Services]"
  - "翻訳 [Analysis Services]"
ms.assetid: 018471e0-3c82-49ec-aa16-467fb58a6d5f
caps.latest.revision: 34
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 34
---
# Analysis Services での翻訳のサポート
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のデータ モデルでは、キャプションや説明に複数の翻訳を埋め込み、LCID に基づいてカルチャ固有の文字列を提供することができます。 多次元モデルの場合、データベース名、キューブ オブジェクト、およびデータベース ディメンション オブジェクトに翻訳を追加できます。 テーブル モデルでは、テーブルと列のキャプションと説明を翻訳できます。  
  
 翻訳を定義するには、メタデータと翻訳されたキャプションをモデル内に作成します。しかし、クライアント アプリケーションでローカライズされた文字列をレンダリングするには、**Language** プロパティをオブジェクトに設定するか、または接続文字列で **Culture** または **Locale Identifier** パラメーターを渡す (たとえば、`LocaleIdentifier=1036` を設定するとフランス語の文字列が返されます) 必要があります。  
  
 同じオブジェクトでさまざまな言語の翻訳を同時にサポートする場合は、 **Locale Identifier** を使用するように計画してください。 **Language** プロパティを設定する方法でも機能しますが、処理やクエリにも影響が出るため、意図しない結果になる恐れがあります。 **Locale Identifier** は翻訳した文字列を返すためにのみ使用されるため、それを設定する方が適切です。  
  
 翻訳は、ロケール識別子 (LCID)、オブジェクトの翻訳されたキャプション (たとえば、ディメンションまたは属性の名前)、およびオプションとして対象言語でのデータ値を提供する列へのバインドで構成されます。 複数の翻訳を保持できますが、特定の接続で使用できる翻訳は 1 つのみです。 モデルに埋め込むことができる翻訳の数に理論上の制限はありませんが、翻訳を 1 つ追加するごとにテストの複雑さが増すことと、すべての翻訳で同じ照合順序を共有する必要があることから、ソリューションを設計する際にはこれらの当然の制約に注意してください。  
  
> [!TIP]  
>  Excel、Management Studio、および SQL Server Profiler などのクライアント アプリケーションを使用して、翻訳した文字列を取得することができます。 詳細については、「[グローバリゼーションのヒントとベスト プラクティス (Analysis Services)](../analysis-services/globalization-tips-and-best-practices-analysis-services.md)」をご覧ください。  
  
## Analysis Services 内のモデルに翻訳済みメタデータを追加する方法  
 手順の詳細については、以下のリンクを参照してください。  
  
-   [テーブル モデルでの翻訳 (Analysis Services)](../analysis-services/tabular-models/translations-in-tabular-models-analysis-services.md)  
  
-   [多次元モデルの翻訳 (Analysis Services)](../analysis-services/multidimensional-models/translations-in-multidimensional-models-analysis-services.md)  
  
## 参照  
 [Analysis Services のグローバリゼーションのシナリオ](../analysis-services/globalization-scenarios-for-analysis-services.md)   
 [言語および照合順序 (Analysis Services)](../analysis-services/languages-and-collations-analysis-services.md)   
 [列の照合順序の設定または変更](../relational-databases/collations/set-or-change-the-column-collation.md)   
 [グローバリゼーションのヒントとベスト プラクティス (Analysis Services)](../analysis-services/globalization-tips-and-best-practices-analysis-services.md)  
  
  