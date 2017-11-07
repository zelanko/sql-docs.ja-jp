---
title: "ローカル キューブ (Analysis Services - 多次元データ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- cubes [Analysis Services], local
ms.assetid: e52e1515-35a7-4dc3-9bbf-736d176ba0c7
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 849f17d47b443e992bd314d6ce2d2a04ec080cd6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="local-cubes-analysis-services---multidimensional-data"></a>ローカル キューブ (Analysis Services - 多次元データ)
  ローカル キューブを作成、更新、または削除するには、ASSL スクリプトまたは AMO プログラムを作成して実行する必要があります。  
  
 ローカル キューブおよびローカル マイニング モデルは、クライアント ワークステーションがネットワークから切断されている間も分析が可能です。 たとえば、次の図のように、クライアント アプリケーションが OLE DB for OLAP 9.0 Provider (MSOLAP.3) を呼び出すと、このプロバイダーはローカル キューブ エンジンを読み込み、ローカル キューブを作成してクエリを実行します。  
  
 ![ローカル キューブとモデルのクライアント アーキテクチャ](../../../analysis-services/multidimensional-models/olap-physical/media/as-localcubearch9.gif "ローカル キューブとモデルのクライアント アーキテクチャ")  
  
 ADMOD.NET および分析管理オブジェクト (AMO) もまた、ローカル キューブとやり取りするときにローカル キューブ エンジンを読み込みます。 ローカル キューブ エンジンはローカル キューブと接続するときにローカル キューブ ファイルを排他的にロックするため、ローカル キューブ ファイルには同時に 1 つのプロセスしかアクセスできません。 1 つのプロセスにつき、5 つまでの同時接続が可能です。  
  
 .cub ファイルには、2 つ以上のキューブまたはデータ マイニング モデルが含まれる場合があります。 ローカル キューブおよびデータ マイニング モデルに対するクエリは、ローカル キューブ エンジンによって処理されるので、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスへの接続は必要ありません。  
  
> [!NOTE]  
>  [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] および [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] をローカル キューブの管理に使用することはできません。  
  
## <a name="local-cubes"></a>ローカル キューブ  
 ローカル キューブを作成し、いずれかの既存のキューブから取得されます、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンスまたはリレーショナル データ ソース。  
  
|ローカル キューブ用データのソース|作成方法|  
|------------------------------------|---------------------|  
|サーバーベースのキューブ|CREATE GLOBAL CUBE ステートメントを使用することができます、または[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]スクリプト言語 (ASSL) スクリプトを作成し、サーバー ベースのキューブからキューブを入力します。 詳細については、次を参照してください。[グローバル CUBE ステートメントの作成 & #40 です。MDX と #41 です。](../../../mdx/mdx-data-definition-create-global-cube.md)または[Analysis Services スクリプト言語 & #40 です。ASSL を XMLA &#41;](../../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md).|  
|リレーショナル データ ソース|ASSL スクリプトを使用して、OLE DB リレーショナル データベースからキューブを作成して設定します。 ASSL を使用してローカル キューブを作成するには、ローカル キューブ ファイル (*.cub) に接続して、サーバー キューブを作成するときに [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスで ASSL スクリプトを実行するのと同じ要領で ASSL スクリプトを実行するだけです。 詳細については、「[Analysis Services スクリプト言語 (XMLA 用 ASSL)](../../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)」を参照してください。|  
  
 ローカル キューブを再構築してデータを更新するには、REFRESH CUBE ステートメントを使用します。 詳細については、次を参照してください。 [CUBE ステートメントの更新 & #40 です。MDX と #41 です。](../../../mdx/mdx-data-definition-refresh-cube.md).  
  
### <a name="local-cubes-created-from-server-based-cubes"></a>サーバーベースのキューブから作成されたローカル キューブ  
 サーバーベースのキューブからローカル キューブを作成する場合は、次の点に注意してください。  
  
-   個別のカウント メジャーはサポートされていません。  
  
-   メジャーを追加する場合は、追加するメジャーに関連するディメンションも最低 1 つ追加する必要があります。 メジャー グループ ディメンションのリレーションシップの詳細については、次を参照してください。[ディメンション リレーションシップ](../../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)です。  
  
-   親子階層を追加すると、親子階層のレベルやフィルターは無視されて、親子階層全体が追加されます。  
  
-   メンバー プロパティは作成されません。  
  
-   準加法メジャーを含める場合、Account ディメンションおよび Time ディメンションでのスライスは許可されていません。  
  
-   参照ディメンションは常に具体化されます。  
  
-   多対多ディメンションを含める場合は、次の規則が適用されます。  
  
    -   多対多ディメンションをスライスすることはできません。  
  
    -   中間メジャー グループのメジャーを追加する必要があります。  
  
    -   多対多リレーションシップに関係する 2 つのメジャー グループに共通するディメンションはスライスすることができません。  
  
-   ローカル キューブに追加されたメジャーおよびディメンションに依存する計算されるメンバー、名前付きセット、および割り当てだけがローカル キューブに表示されます。 無効な計算されるメンバー、名前付きセット、および割り当ては自動的に除外されます。  
  
### <a name="security"></a>セキュリティ  
 ユーザーがサーバー キューブからローカル キューブを作成するためには、ユーザーに許可する必要があります**ドリルスルーとローカル キューブ**サーバー キューブに対する権限。 詳細については、次を参照してください。[許可キューブまたはモデル権限 & #40 です。Analysis Services &#41;](../../../analysis-services/multidimensional-models/grant-cube-or-model-permissions-analysis-services.md).  
  
 ローカル キューブは、サーバー キューブのようにロールを使用してセキュリティで保護されていません。 ローカル キューブ ファイルへのファイル レベルのアクセス権を持っていれば、ローカル キューブ ファイル内のキューブに対してクエリを実行できます。 使用することができます、**暗号化パスワード**接続ファイルのプロパティをローカル キューブに、ローカル キューブ ファイルにパスワードを設定します。 ローカル キューブ ファイルにパスワードを設定すると、以後クエリを実行するためにローカル キューブ ファイルに接続するときにそのパスワードが必要になります。  
  
## <a name="see-also"></a>参照  
 [GLOBAL CUBE ステートメント &#40; を作成します。MDX と #41 です。](../../../mdx/mdx-data-definition-create-global-cube.md)   
 [Analysis Services スクリプト言語 &#40; を使用した開発ASSL &#41;](../../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [更新の CUBE ステートメント & #40 です。MDX と #41 です。](../../../mdx/mdx-data-definition-refresh-cube.md)  
  
  

