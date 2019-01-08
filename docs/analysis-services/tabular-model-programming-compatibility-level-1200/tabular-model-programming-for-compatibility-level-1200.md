---
title: Analysis Services 表形式モデルの互換性レベル 1200 のプログラミング |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: eba8822f7fe21e089d9c02b8f6df6cf5ec0e5294
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072109"
---
# <a name="tabular-model-programming-for-compatibility-level-1200-and-higher"></a>テーブル モデルのプログラミング互換性レベル 1200 以降
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
以降の互換性レベル 1200 では、表形式のメタデータは、表形式モデル オブジェクトの記述子として履歴多次元メタデータを置き換える、モデルの構成要素の説明に使用されます。 テーブル、列、およびリレーションシップのメタデータは、テーブル、列、およびリレーションシップではなく (ディメンションおよび属性) と同等の多次元です。  
  
モデルを作成する新しい互換性レベル 1200 以上 Microsoft.AnalysisServices.Tabular Api、SQL Server Data Tools (SSDT) の最新バージョンを使用して、または変更することで、 **CompatibilityLevel**の既存のテーブル(また、SSDT で実行する) にアップグレードするモデル。 これは、サーバー、ツール、およびプログラミング インターフェイスの新しいバージョンに、モデルをバインドします。   
  
既存の表形式ソリューションのアップグレードはお勧めしますが、必要ありません。 既存のスクリプトとアクセスまたは表形式モデルまたはデータベースを管理するカスタム ソリューションとして使用できるは。 以前の互換性レベルは、そのレベルで使用できる機能を使用して SQL Server 2016 で完全にサポートします。 Azure Analysis Services では、互換性レベル 1200 以上がのみサポートします。
  
 新しい表形式モデルでは、別のコードとスクリプトを次に示します必要があります。  
  
## <a name="object-model-definitions-as-tabular-metadata-constructs"></a>表形式のメタデータ コンストラクトとしてオブジェクト モデルの定義  
 1200 以上のモデルの表形式オブジェクト モデルが JSON 経由で公開されている、 [Tabular Model Scripting Language](https://docs.microsoft.com/bi-reference/tmsl/tabular-model-scripting-language-tmsl-reference)では、新しい名前空間を通じて AMO データ定義言語[Microsoft.AnalysisServices.Tabular](http://msdn.microsoft.com/library/microsoft.analysisservices.tabular.aspx)

## <a name="script-for-tabular-models-and-databases"></a>表形式モデル データベース用スクリプト  
 TMSL は、作成、読み取り、更新、削除の操作のサポートの表形式モデルは、JSON スクリプト言語です。 TMSL を使用してデータの更新しのアタッチ、メインボード、バックアップ、復元、データベース操作を呼び出すし、同期できます。  
  
 AMO PowerShell は、TMSL スクリプトを入力として受け取ります。  
  
 参照してください[Tabular Model Scripting Language &#40;TMSL&#41;参照](https://docs.microsoft.com/bi-reference/tmsl/tabular-model-scripting-language-tmsl-reference)と[Analysis Services PowerShell Reference](../../analysis-services/powershell/analysis-services-powershell-reference.md)詳細についてはします。  
  
## <a name="query-languages"></a>クエリ言語  
 DAX と MDX は、すべてのテーブル モデルのサポートされます。  
  
## <a name="expression-language"></a>式言語  
 フィルターとメジャー、Kpi などの計算されるオブジェクトの作成に使用する式は、DAX で確立されます。 参照してください[テーブル モデルにおける DAX の理解](../../analysis-services/tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md)と[Data Analysis Expressions &#40;DAX&#41; Analysis Services で](http://msdn.microsoft.com/library/abb336c9-3346-4cab-b91b-90f93f4575e5)します。  
  
## <a name="managed-code-for-tabular-models-and-databases"></a>表形式モデル データベース用のマネージ コード  
 AMO には、モデルをプログラムで操作するための新しい名前空間、Microsoft.AnalysisServices.Tabular が含まれています。 参照してください[Microsoft.AnalysisServices Namespace](https://msdn.microsoft.com/library/ms146720\(SQL.130\).aspx)詳細についてはします。  
  
> [!NOTE]  
>  Analysis Services 管理オブジェクト (AMO)、ADOMD.NET、および表形式オブジェクト モデル (TOM) のクライアント ライブラリは、.NET 4.0 ランタイムを対象するようになりました。   
  
## <a name="see-also"></a>参照  
 [Analysis Services Developer Documentation (Analysis Services の開発者向けドキュメント)](../../analysis-services/analysis-services-developer-documentation.md)   
 [表形式のモデルのプログラミング互換性レベル 1050 から 1103](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/tabular-model-programming-for-compatibility-levels-1050-through-1103.md)   
 [テクニカル リファレンス](../../analysis-services/powershell/technical-reference-ssas.md) [Analysis Services のアップグレード](../../database-engine/install-windows/upgrade-analysis-services.md)  
 [表形式モデルとデータベースの互換性レベル](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/tabular-model-programming-for-compatibility-levels-1050-through-1103.md)  
  
  
