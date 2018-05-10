---
title: 最大容量仕様 (Analysis Services) |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 42cd2e4809ab91fbd672a20b8213dc9fb6d9727c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="maximum-capacity-specifications-analysis-services"></a>最大容量仕様 (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  次の各表に、さまざまなサーバー配置モードの [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] コンポーネントで定義される各種オブジェクトの最大サイズと最大数を示します。  
  
 このトピックには、次のセクションが含まれます。  
  
 [多次元およびデータ マイニング (DeploymentMode = 0)](#bkmk_OLAP)  
  
 [SharePoint (DeploymentMode = 1)](#bkmk_sharepoint)  
  
 [テーブル (DeploymentMode = 2)](#bkmk_vertipaq)  
  
##  <a name="bkmk_OLAP"></a> 多次元およびデータ マイニング (DeploymentMode = 0)  
 データとメタデータの両方を格納する MOLAP ストレージ モードは、ファイル サイズに物理的な制限があります。 文字列ストア ファイルの既定の最大サイズは 4 GB です。 文字列を格納するためにより大きなファイルが必要な場合は、別の文字列ストレージ アーキテクチャを指定できます。 詳細については、次を参照してください。[ディメンションおよびパーティションの文字列ストレージを構成する](../../../analysis-services/multidimensional-models/configure-string-storage-for-dimensions-and-partitions.md)です。  
  
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
  
 オブジェクトの名前付けガイドラインの詳細については、次を参照してください。 [ASSL オブジェクトとオブジェクトの特性](../../../analysis-services/multidimensional-models/scripting-language-assl/assl-objects-and-object-characteristics.md)です。  
  
 オンライン分析処理 (OLAP) およびデータ マイニングのデータ ソース制限の詳細については、次を参照してください[データ ソースのサポートされている&#40;SSAS - 多次元&#41;](../../../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md)、 [&#40;SSAS - 多次元&#41;](../../../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md)、および[ASSL オブジェクトとオブジェクトの特性](../../../analysis-services/multidimensional-models/scripting-language-assl/assl-objects-and-object-characteristics.md)です。  
  
##  <a name="bkmk_sharepoint"></a> SharePoint (DeploymentMode = 1)  
  
|オブジェクト|最大サイズと最大数|  
|------------|----------------------------|  
|インスタンス内のデータベース|2^31-1 = 2,147,483,647|  
|データベース内のテーブル|2^31-1 = 2,147,483,647|  
|テーブル内の列|2^31-1 = 2,147,483,647<br /><br /> **警告:** テーブル内の列の合計数がメジャーの合計数に依存していて、同じテーブルに関連付けられている計算列です。<br /><br /> テーブルの '列 + メジャー + 計算される列' の最大数は、2^31-1 = 2,147,483,647 です。|  
|テーブル内の行|無制限<br /><br /> **警告:** 制限の 1 つの列は含めないこと 1,999,999,997 複数の個別の値。|  
|テーブル内の階層|2^31-1 = 2,147,483,647|  
|階層内のレベル|2^31-1 = 2,147,483,647|  
|リレーションシップ|2^31-1 = 2,147,483,647|  
|テーブル内のキー列|2^31-1 = 2,147,483,647|  
|テーブル内のメジャー|2^31-1 = 2,147,483,647<br /><br /> **警告:** テーブル内のメジャーの合計数は、列の合計数によって異なります。 および、同じテーブルに関連付けられている計算列です。<br /><br /> テーブルの '列 + メジャー + 計算される列' の最大数は、2^31-1 = 2,147,483,647 です。|  
|テーブル内の計算される列|2^31-1 = 2,147,483,647<br /><br /> **警告:** テーブルで計算される列の合計数は、列の合計数によって異なります。 および、同じテーブルにメジャーが関連付けられています。<br /><br /> テーブルの '列 + メジャー + 計算される列' の最大数は、2^31-1 = 2,147,483,647 です。|  
|クエリによって返されるセル|2^31-1 = 2,147,483,647|  
|ソース クエリのレコード サイズ|64 K|  
|オブジェクト名の長さ|100 文字|  
  
##  <a name="bkmk_vertipaq"></a> テーブル (DeploymentMode = 2)  
理論上の制限を次に示します。 小さい番号のパフォーマンスは低下します。   

|オブジェクト|最大サイズと最大数|  
|------------|----------------------------|  
|インスタンス内のデータベース|16,000|  
|データベースのテーブルと列の合計数|16,000|  
|テーブル内の行|無制限<br /><br /> **警告:** 制限のあるテーブルの列を 1 つ持つことができるありません 1,999,999,997 複数の個別の値。|  
|テーブル内の階層|15,999|  
|階層内のレベル|15,999|  
|リレーションシップ|8,000|  
|すべてのテーブル内のキー列|15,999|  
|テーブル内のメジャー|2^31-1 = 2,147,483,647|  
|クエリによって返されるセル|2^31-1 = 2,147,483,647|  
|ソース クエリのレコード サイズ|64 K|  
|オブジェクト名の長さ|512 文字|  
  
## <a name="see-also"></a>参照  
 [Analysis Services インスタンスのサーバー モードの決定](../../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [全般プロパティ](../../../analysis-services/server-properties/general-properties.md)  
  
  
