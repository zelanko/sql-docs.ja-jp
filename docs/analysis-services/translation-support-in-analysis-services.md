---
title: Analysis Services での翻訳のサポート |Microsoft Docs
ms.date: 01/09/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bd727b56649ce9ffc237575b0311db256ec9b2fc
ms.sourcegitcommit: 1c01af5b02fe185fd60718cc289829426dc86eaa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2019
ms.locfileid: "54184928"
---
# <a name="translation-support-in-analysis-services"></a>Analysis Services での翻訳のサポート
[!INCLUDE[ssas-appliesto-sqlas-aas](../includes/ssas-appliesto-sqlas-aas.md)]

  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]データ モデルでは、複数の翻訳キャプションまたは説明のロケール識別子 (LCID) に基づくカルチャに固有の文字列を提供するを埋め込むことができます。 多次元モデルの場合、データベース名、キューブ オブジェクト、およびデータベース ディメンション オブジェクトに翻訳を追加できます。 テーブル モデルでは、テーブルと列のキャプションと説明を翻訳できます。  
  
 翻訳を定義するには、メタデータと翻訳されたキャプションをモデル内に作成します。しかし、クライアント アプリケーションでローカライズされた文字列をレンダリングするには、 **Language** プロパティをオブジェクトに設定するか、または接続文字列で **Culture** または **Locale Identifier** パラメーターを渡す (たとえば、 `LocaleIdentifier=1036` を設定するとフランス語の文字列が返されます) 必要があります。  
  
 同じオブジェクトでさまざまな言語の翻訳を同時にサポートする場合は、 **Locale Identifier** を使用するように計画してください。 **Language** プロパティを設定する方法でも機能しますが、処理やクエリにも影響が出るため、意図しない結果になる恐れがあります。 **Locale Identifier** は翻訳した文字列を返すためにのみ使用されるため、それを設定する方が適切です。  
  
 翻訳は、ロケール識別子 (LCID)、オブジェクトの翻訳されたキャプション (たとえば、ディメンションまたは属性の名前)、およびオプションとして対象言語でのデータ値を提供する列へのバインドで構成されます。 複数の翻訳を保持できますが、特定の接続で使用できる翻訳は 1 つのみです。 モデルに埋め込むことができる翻訳の数に理論上の制限はありませんが、翻訳を 1 つ追加するごとにテストの複雑さが増すことと、すべての翻訳で同じ照合順序を共有する必要があることから、ソリューションを設計する際にはこれらの当然の制約に注意してください。  
  
> [!TIP]  
>  Excel、SQL Server Management Studio、および SQL Server Profiler などのクライアント アプリケーションを使用すると、翻訳された文字列が返されます。 詳細については、「 [グローバリゼーションのヒントとベスト プラクティス (Analysis Services)](../analysis-services/globalization-tips-and-best-practices-analysis-services.md) 」をご覧ください。  
  
## <a name="how-to-add-translated-metadata-to-model-in-analysis-services"></a>Analysis Services 内のモデルに翻訳済みメタデータを追加する方法  
 手順の詳細については、以下のリンクを参照してください。  
  
-   [表形式モデルの翻訳](../analysis-services/tabular-models/translations-in-tabular-models-analysis-services.md)  
  
-   [多次元モデルの翻訳](../analysis-services/multidimensional-models/translations-in-multidimensional-models-analysis-services.md)  
  
## <a name="see-also"></a>関連項目  
 [Analysis Services のグローバリゼーションのシナリオ](../analysis-services/globalization-scenarios-for-analysis-services.md)   
 [言語および照合順序 (Analysis Services)](../analysis-services/languages-and-collations-analysis-services.md)   
 [列の照合順序の設定または変更](../relational-databases/collations/set-or-change-the-column-collation.md)   
 [グローバリゼーションのヒントとベスト プラクティス (Analysis Services)](../analysis-services/globalization-tips-and-best-practices-analysis-services.md)  
  
  
