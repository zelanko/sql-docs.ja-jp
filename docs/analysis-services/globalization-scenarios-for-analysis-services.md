---
title: "Analysis Services のグローバリゼーションのシナリオ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multiple language support [Analysis Services]
- languages [Analysis Services]
- SSAS, international considerations
- international considerations [Analysis Services]
- global considerations [Analysis Services]
- SQL Server Analysis Services, international considerations
- Analysis Services, international considerations
ms.assetid: e8af85ff-ef33-4659-a003-bb34578eb2a2
caps.latest.revision: "40"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 751680ddab38980f539364dc1566fb94c9816352
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="globalization-scenarios-for-analysis-services"></a>Analysis Services のグローバリゼーションのシナリオ
[!INCLUDE[ssas-appliesto-sqlas-aas](../includes/ssas-appliesto-sqlas-aas.md)][!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]多言語データおよび両方のテーブルと多次元データ モデルのメタデータを格納して操作します。 データは Unicode (UTF-16) で格納され、Unicode エンコードの文字セットを使用します。 データ モデルに ANSI データを読み込むと、文字は Unicode の等価なコード ポイントを使用して格納されます。  
  
 Unicode をサポートしているということは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] が、Windows のクライアント/サーバー オペレーティング システムによってサポートされている任意の言語でデータを格納できることを意味します。Windows コンピューターで使用されるどの文字セットでも読み取り、書き込み、並べ替え、およびデータ比較が可能です。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データを使用する BI クライアント アプリケーションは、その言語でモデル内にデータが存在すれば、ユーザーの選択した任意の言語でデータを表現できます。  
  
 言語のサポートは、ユーザーの立場に応じてさまざまな意味を持ちます。 Analysis Services での言語サポートに関連するいくつかの一般的な事項を以下で説明します。  
  
-   既に説明したとおり、データは、Windows クライアント オペレーティング システムにあるどの Unicode エンコードの文字セットでも格納できます。  
  
-   オブジェクト名などのメタデータを翻訳できます。 モデルの種類によってサポートが異なりますが、多次元モデルと表形式モデルは両方とも、モデル内での翻訳文字列の追加をサポートしています。 複数の翻訳を定義し、クライアントに返される翻訳をロケール識別子で決定できます。 詳細については、この後の [機能](#bkmk_features) に関するトピックを参照してください。  
  
-   [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] エンジン (msmdsrv) によって返されるエラー、警告、および情報メッセージは、Office および Office 365 でサポートされる 43 の言語にローカライズされています。 特定の言語でメッセージを取得するために、特別な構成は必要ありません。 クライアント アプリケーションのロケールにより、どの言語で文字列が返されるかが決まります。  
  
-   構成ファイル (msmdsrv.ini) および AMO PowerShell は英語のみです。  
  
-   Analysis Services が実行される Windows サーバーに言語パックをインストールした場合、ログ ファイルには英語とローカライズされたメッセージが混在します。  
  
-   ドキュメントとツール ( [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 、 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]など) は、中国語 (簡体字)、中国語 (繁体字)、フランス語、ドイツ語、イタリア語、日本語、韓国語、ポルトガル語 (ブラジル)、ロシア語、およびスペイン語に翻訳されます。 カルチャはインストール中に指定されます。  
  
 多次元モデルについては、Analysis Services で、言語、照合順序、および翻訳をオブジェクト階層全体で独立して設定できます。  表形式モデルについては、翻訳のみを追加できます。言語と照合順序は、ホスト オペレーティング システムによって継承されます。  
  
 Analysis Services のグローバリゼーション機能を使用すると、次のようなシナリオが可能になります。  
  
-   1 つのデータ モデルで複数の翻訳されたキャプションを提供することにより、ユーザーが選択した言語でフィールド名や値が表示されるようにできます。 カナダ、ベルギー、スイスなどのバイリンガル国で事業を行う企業では、クライアント/サーバー アプリケーション全体で複数の言語をサポートすることが標準的なコーディング要件になっています。 このシナリオは、翻訳と通貨換算によって可能になります。 詳細と参考資料のリンクは、この後の「 [機能](#bkmk_features) 」を参照してください。  
  
-   開発および運用環境を、地理的にさまざまな国に分散して設置できます。 ある国で開発したソリューションを別の国に配置するというシナリオは、ますます一般化しています。 1 つの言語で開発したソリューションを、別の言語パックを使用するサーバーに配置できるように準備するには、言語および照合順序のプロパティを設定する方法についての知識が不可欠です。 これらのプロパティを適切に設定すると、元のホスト システムから取得する継承された既定値を上書きすることができます。 詳細については、この後の [言語および照合順序 &#40;Analysis Services&#41;](../analysis-services/languages-and-collations-analysis-services.md) 」をご覧ください。  
  
##  <a name="bkmk_features"></a> グローバル化された多言語ソリューションを構築するための機能  
 クライアント レベルでは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の多次元データを使用または操作するグローバル化されたアプリケーションで、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]の多言語機能および複数カルチャ機能を使用できます。  
  
 翻訳が自動的に定義された [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトのデータおよびメタデータは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスへの接続時にロケール識別子を指定することによって取得できます。  
  
 多言語データに関連する問題の回避に役立つ設計およびコーディング手法については、「[グローバリゼーションのヒントとベスト プラクティス &#40;Analysis Services&#41;](../analysis-services/globalization-tips-and-best-practices-analysis-services.md)」をご覧ください。  
  
||||  
|-|-|-|  
|**機能**|**テーブル**|**多次元**|  
|[言語および照合順序 &#40;Analysis Services&#41;](../analysis-services/languages-and-collations-analysis-services.md)|オペレーティング システムから継承されます。|モデル階層で主要オブジェクトの言語と照合順序の両方を上書きする機能と共に継承されます。|  
|翻訳サポートのスコープ|キャプションと説明。|オブジェクトの名前、キャプション、識別子、および説明の翻訳を、どの Unicode 言語およびスクリプトでも作成できます。 これは、ツールや環境が別の言語の場合にも当てはまります。 たとえば、スタック全体で英語およびラテン文字の照合順序を使用する開発環境で、名前にキリル文字を使用したオブジェクトをモデルに含めることができます。|  
|翻訳サポートの実装|[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] を使用して作成し、入力する翻訳ファイルを生成して、モデルにインポートし直します。<br /><br /> 詳しくは、「[表形式モデルでの翻訳 &#40;Analysis Services&#41;](../analysis-services/tabular-models/translations-in-tabular-models-analysis-services.md)」をご覧ください。|[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] を使用して作成し、キューブ、メジャー、ディメンション、および属性のキャプション、説明、およびアカウントの種類の翻訳を定義します。<br /><br /> 詳しくは、「[多次元モデルの翻訳 &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/translations-in-multidimensional-models-analysis-services.md)」をご覧ください。 この機能を使用する方法のレッスンは、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] チュートリアルの「[レッスン 9 : パースペクティブと翻訳の定義](../analysis-services/lesson-9-defining-perspectives-and-translations.md)」をご覧ください。|  
|通貨換算|使用できません。|通貨換算は、通貨データを含むメジャーを変換する専用の MDX スクリプトで行います。 [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)] のビジネス インテリジェンス ウィザードを使用すると、属性、メジャー グループのデータおよびメタデータの組み合わせを使用して通貨データを含むメジャーを換算する MDX スクリプトディメンションを生成できます。 「[通貨換算 &#40;Analysis Services&#41;](../analysis-services/currency-conversions-analysis-services.md)」をご覧ください。|  
  
## <a name="see-also"></a>参照  
 [Analysis Services での翻訳のサポート](../analysis-services/translation-support-in-analysis-services.md)   
 [Windows アプリケーションの国際化](http://msdn.microsoft.com/library/windows/desktop/dd318661%28v=vs.85%29.aspx)   
 [グローバル デベロッパー センターを参照してください。](http://msdn.microsoft.com/goglobal/bb871628.aspx)   
 [ロケールに基づくアダプティブ デザインによる書き込みの Windows ストア アプリ](https://blogs.windows.com/buildingapps/2014/03/06/writing-windows-store-apps-with-locale-based-adaptive-design/)   
 [C# と XAML によるユニバーサル Windows アプリの開発](http://www.microsoftvirtualacademy.com/training-courses/developing-universal-windows-apps-with-c-and-xaml)  
  
  
