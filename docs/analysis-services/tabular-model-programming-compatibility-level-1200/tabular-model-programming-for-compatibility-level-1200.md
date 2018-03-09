---
title: "互換性レベル 1200 の表形式モデルのプログラミング |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/30/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d343f693-c800-42fe-bb4f-2c38a10919f1
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: c7e1ec3e7ef85cb567d70e96d5c9f3bdd6655f3d
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2018
---
# <a name="tabular-model-programming-for-compatibility-level-1200-and-higher"></a>表形式モデル プログラミングの互換性レベル 1200 以降
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
以降の互換性レベル 1200 では、表形式のメタデータは表形式モデル オブジェクトの記述子と履歴の多次元メタデータを置き換えて、モデルのコンス トラクターの記述に使用されます。 テーブル、列、およびリレーションシップのメタデータは、テーブル、列、およびリレーションシップではなく (ディメンションおよび属性) と同等の多次元です。  
  
モデルを作成する新しい互換性レベル 1200 以上 Microsoft.AnalysisServices.Tabular Api、SQL Server Data Tools (SSDT) の最新バージョンを使用して、または変更することによって、 **CompatibilityLevel**既存の表形式の(また、SSDT で処理する) をアップグレードするモデル。 これにより新しいバージョンのサーバー、ツール、およびプログラミング インターフェイスをモデルをバインドします。   
  
既存の表形式ソリューションをアップグレードすることをお勧めは必要ありません。 既存のスクリプトとアクセスまたは表形式モデルまたはデータベースを管理するカスタム ソリューションとして使用できるはします。 以前の互換性レベルは、そのレベルで使用できる機能を使用して SQL Server 2016 で完全にサポートされます。 Azure Analysis Services では、互換性レベル 1200 以上がのみがサポートされます。
  
 新しい表形式モデルでは、別のコードとスクリプトを次にまとめます必要があります。  
  
## <a name="object-model-definitions-as-tabular-metadata-constructs"></a>表形式のメタデータ構造としてオブジェクト モデルの定義  
 1200 以上のモデルの表形式オブジェクト モデルが JSON 経由で公開されている、[表形式モデル スクリプト言語](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)を介してでは、新しい名前空間、AMO データ定義言語を[Microsoft.AnalysisServices.Tabular](http://msdn.microsoft.com/library/microsoft.analysisservices.tabular.aspx)

## <a name="script-for-tabular-models-and-databases"></a>表形式モデルとデータベース用スクリプト  
 TMSL は、作成、読み取り、更新、削除操作のサポート表形式モデルの場合は、JSON スクリプト言語です。 TMSL を使用してデータを更新し、アタッチ、メインボード、バックアップ、復元、データベース操作の呼び出しし、を同期します。  
  
 AMO PowerShell は、TMSL スクリプトを入力として受け取ります。  
  
 参照してください[表形式モデルの言語 &#40; のスクリプトTMSL &#41;参照](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)と[Analysis Services PowerShell Reference](../../analysis-services/powershell/analysis-services-powershell-reference.md)詳細についてはします。  
  
## <a name="query-languages"></a>クエリ言語  
 DAX と MDX については、すべてのテーブル モデルのサポートします。  
  
## <a name="expression-language"></a>式の言語  
 DAX では、フィルターとメジャー、Kpi などの計算されるオブジェクトを作成するために使用する式が策定されました。 参照してください[表形式モデルでの DAX を理解する](../../analysis-services/tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md)と[Data Analysis Expressions &#40;DAX"&"#41 です。 Analysis Services で](http://msdn.microsoft.com/library/abb336c9-3346-4cab-b91b-90f93f4575e5)です。  
  
## <a name="managed-code-for-tabular-models-and-databases"></a>表形式モデルとデータベースのマネージ コード  
 AMO には、モデルをプログラムで使用するための新しい名前空間、Microsoft.AnalysisServices.Tabular が含まれています。 参照してください[Microsoft.AnalysisServices Namespace](https://msdn.microsoft.com/library/ms146720\(SQL.130\).aspx)詳細についてはします。  
  
> [!NOTE]  
>  Analysis Services 管理オブジェクト (AMO)、ADOMD.NET、および表形式オブジェクト モデル (TOM) のクライアント ライブラリのターゲットを .NET 4.0 ランタイム。   
  
## <a name="see-also"></a>参照  
 [Analysis Services Developer Documentation (Analysis Services の開発者向けドキュメント)](../../analysis-services/analysis-services-developer-documentation.md)   
 [互換性のためのテーブル モデルのプログラミング レベルを 1050 から 1103](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/tabular-model-programming-for-compatibility-levels-1050-through-1103.md)   
 [テクニカル リファレンス](../../analysis-services/powershell/technical-reference-ssas.md) [Analysis Services のアップグレード](../../database-engine/install-windows/upgrade-analysis-services.md)  
 [表形式モデルとデータベースの互換性レベル](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/tabular-model-programming-for-compatibility-levels-1050-through-1103.md)  
  
  
