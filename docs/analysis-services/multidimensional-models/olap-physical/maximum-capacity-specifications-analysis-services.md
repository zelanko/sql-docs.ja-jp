---
title: 最大容量仕様 (Analysis Services) |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 187a3a76f63853c63b9fe92dbd7ccfd4a0cfcdb5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68165489"
---
# <a name="maximum-capacity-specifications-analysis-services"></a>最大容量仕様 (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  次の各表に、さまざまなサーバー配置モードの [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] コンポーネントで定義される各種オブジェクトの最大サイズと最大数を示します。  
  
 このトピックには、次のセクションが含まれます。  
  
 [多次元およびデータ マイニング (DeploymentMode = 0)](#bkmk_OLAP)  
  
 [SharePoint (DeploymentMode = 1)](#bkmk_sharepoint)  
  
 [テーブル (DeploymentMode = 2)](#bkmk_vertipaq)  
  
##  <a name="bkmk_OLAP"></a> 多次元およびデータ マイニング (DeploymentMode = 0)  
 データとメタデータの両方を格納する MOLAP ストレージ モードは、ファイル サイズに物理的な制限があります。 文字列ストア ファイルの既定の最大サイズは 4 GB です。 文字列を格納するためにより大きなファイルが必要な場合は、別の文字列ストレージ アーキテクチャを指定できます。 詳細については、次を参照してください。[ディメンションおよびパーティションの文字列ストレージを構成する](../../../analysis-services/multidimensional-models/configure-string-storage-for-dimensions-and-partitions.md)します。  
  
|オブジェクト|最大サイズと最大数|  
|------------|----------------------------|  
|インスタンス内のデータベース|2^31-1 = 2,147,483,647|  
|データベースのディメンション|2^31-1 = 2,147,483,647|  
|ディメンションの属性|2^31-1 = 2,147,483,647|  
|ディメンション属性のメンバー|2^31-1 = 2,147,483,647|  
|ディメンション内のユーザー定義階層|2^31-1 = 2,147,483,647|  
|ユーザー定義階層内のレベル|2^31-1 = 2,147,483,647|  
|データベース内のキューブ|2^31-1 = 2,147,483,647|  
|キューブ内のメジャー グループ|2^31-1 = 2,147,483,647|  
|メジャー グループ内のメジャー|2^31-1 = 2,147,483,647|  
|キューブ内の計算|2^31-1 = 2,147,483,647|  
|キューブ内の KPI|2^31-1 = 2,147,483,647|  
|キューブ内のアクション|2^31-1 = 2,147,483,647|  
|キューブ内のパーティション|2^31-1 = 2,147,483,647|  
|キューブ内の翻訳|2^31-1 = 2,147,483,647|  
|パーティション内の集計|2^31-1 = 2,147,483,647|  
|クエリによって返されるセル|2^31-1 = 2,147,483,647|  
|ソース クエリのレコード サイズ|64 K|  
|オブジェクト名の長さ|100 文字|  
|データ マイニング モデル属性列の個別状態の最大数|2^31-1 = 2,147,483,647|  
|使用される属性の最大数 (機能選択)|2^31-1 = 2,147,483,647|  
  
 オブジェクトの名前付けのガイドラインの詳細については、次を参照してください。 [ASSL オブジェクトとオブジェクトの特性](../../../analysis-services/multidimensional-models/scripting-language-assl/assl-objects-and-object-characteristics.md)します。  
  
 オンライン分析処理 (OLAP) およびデータ マイニングのデータ ソース制限の詳細については、次を参照してください[サポートされるデータ ソース&#40;SSAS - 多次元&#41;](../../../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md)、 [&#40;SSAS - 多次元&#41;](../../../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md)、および[ASSL オブジェクトとオブジェクトの特性](../../../analysis-services/multidimensional-models/scripting-language-assl/assl-objects-and-object-characteristics.md)します。  
  
##  <a name="bkmk_sharepoint"></a> SharePoint (DeploymentMode = 1)  
  
|オブジェクト|最大サイズと最大数|  
|------------|----------------------------|  
|インスタンス内のデータベース|2^31-1 = 2,147,483,647|  
|データベース内のテーブル|2^31-1 = 2,147,483,647|  
|テーブル内の列|2^31-1 = 2,147,483,647<br /><br /> **警告:** 同じテーブルに関連付けられている計算列とテーブル内の列の合計数は、メジャーの合計数によって異なります。<br /><br /> テーブルの '列 + メジャー + 計算される列' の最大数は、2^31-1 = 2,147,483,647 です。|  
|テーブル内の行|無制限<br /><br /> **警告:** 1 つの列が含まれていないこと 1,999,999,997 複数の個別の値には制限。|  
|テーブル内の階層|2^31-1 = 2,147,483,647|  
|階層のレベル|2^31-1 = 2,147,483,647|  
|リレーションシップ|2^31-1 = 2,147,483,647|  
|テーブル内のキー列|2^31-1 = 2,147,483,647|  
|テーブル内のメジャー|2^31-1 = 2,147,483,647<br /><br /> **警告:** 同じテーブルに関連付けられている計算列とテーブルのメジャーの合計数は、列の合計数によって異なります。<br /><br /> テーブルの '列 + メジャー + 計算される列' の最大数は、2^31-1 = 2,147,483,647 です。|  
|テーブル内の計算される列|2^31-1 = 2,147,483,647<br /><br /> **警告:** テーブルの計算列の合計数は、列と同じテーブルに関連付けられているメジャーの合計数によって異なります。<br /><br /> テーブルの '列 + メジャー + 計算される列' の最大数は、2^31-1 = 2,147,483,647 です。|  
|クエリによって返されるセル|2^31-1 = 2,147,483,647|  
|ソース クエリのレコード サイズ|64 K|  
|オブジェクト名の長さ|100 文字|  
  
##  <a name="bkmk_vertipaq"></a> テーブル (DeploymentMode = 2)  
理論的制限を次に示します。 小さい番号のパフォーマンスは低下します。   

|オブジェクト|最大サイズと最大数|  
|------------|----------------------------|  
|インスタンス内のデータベース|16,000|  
|データベースのテーブルと列の合計数|16,000|  
|テーブル内の行|無制限<br /><br /> **警告:** 制限は、テーブル内 1 つの列を持たない 1,999,999,997 複数の個別の値。|  
|テーブル内の階層|15,999|  
|階層のレベル|15,999|  
|リレーションシップ|8,000|  
|すべてのテーブルのキー列|15,999|  
|テーブル内のメジャー|2^31-1 = 2,147,483,647|  
|クエリによって返されるセル|2^31-1 = 2,147,483,647|  
|ソース クエリのレコード サイズ|64 K|  
|オブジェクト名の長さ|512 文字|  
  
## <a name="see-also"></a>関連項目  
 [Analysis Services インスタンスのサーバー モードの決定](../../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [全般プロパティ](../../../analysis-services/server-properties/general-properties.md)  
  
  
