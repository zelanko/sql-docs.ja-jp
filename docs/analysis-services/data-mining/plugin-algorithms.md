---
title: "プラグイン アルゴリズム |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- third-party algorithms [Analysis Services]
- algorithms [data mining], creating
- plugin algorithms [Analysis Services]
ms.assetid: fe364ddc-576e-42fc-9ced-baa399992f92
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 66fad2d8974e832925ab67174f2c635b8f5fbf37
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="plugin-algorithms"></a>プラグイン アルゴリズム
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で提供されているアルゴリズムの他にも、データ マイニングに使用できるアルゴリズムが数多くあります。 したがって、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、サード パーティ製アルゴリズムを "プラグイン" するためのメカニズムが提供されています。 サード パーティのアルゴリズムが特定の規格に従っている限り、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] アルゴリズムを使用する場合と同様に、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 内でそれらのアルゴリズムを使用できます。 プラグイン アルゴリズムには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって提供されるアルゴリズムのすべての機能があります。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] がプラグイン アルゴリズムとの通信に使用するインターフェイスの詳細については、 [CodePlex](http://go.microsoft.com/fwlink/?LinkID=87843) Web サイトで公開されている、カスタム アルゴリズムとカスタム モデル ビューアーを作成するためのサンプルをご覧ください。  
  
## <a name="algorithm-requirements"></a>アルゴリズムの必要条件  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]にアルゴリズムをプラグインするには、次の COM インターフェイスを実装する必要があります。  
  
 **IDMAlgorithm**  
 モデルを生成するアルゴリズムを実装し、結果のモデルの予測操作を実装します。  
  
 **IDMAlgorithmNavigation**  
 ブラウザーがモデルのコンテンツにアクセスできるようにします。  
  
 **IDMPersist**  
 アルゴリズムによってトレーニングされるモデルを [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]で保存して読み込むことができるようにします。  
  
 **IDMAlgorithmMetadata**  
 アルゴリズムの機能および入力パラメーターを記述します。  
  
 **IDMAlgorithmFactory**  
 アルゴリズム インターフェイスを実装するオブジェクトのインスタンスを作成し、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] にアルゴリズム メタデータ インターフェイスへのアクセスを提供します。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、これらの COM インターフェイスを使用してプラグイン アルゴリズムと通信します。 使用するプラグイン アルゴリズムでは [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB for Data Mining 仕様をサポートしている必要はありますが、仕様内のデータ マイニング オプションをすべてサポートする必要はありません。 アルゴリズムの機能を決定するには、 [MINING_SERVICES](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-services-rowset.md) スキーマ行セットを使用できます。 このスキーマ行セットでは、プラグイン アルゴリズム プロバイダーごとにデータ マイニング サポート オプションが一覧表示されます。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]で新しいアルゴリズムを使用する前に、そのアルゴリズムを登録する必要があります。 アルゴリズムを登録するには、アルゴリズムを含める [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの .ini ファイルに次の情報を追加します。  
  
-   アルゴリズム名  
  
-   ProgID (プラグイン アルゴリズムにのみ含まれるオプションです)  
  
-   アルゴリズムが有効か無効かを示すフラグ  
  
 次のコード サンプルは、新しいアルゴリズムの登録方法を示しています。  
  
 `<ConfigurationSettings>`  
  
 `...`  
  
 `<DataMining>`  
  
 `...`  
  
 `<Algorithms>`  
  
 `...`  
  
 `<Sample_Plugin_Algorithm>`  
  
 `<Enabled>1</Enabled>`  
  
 `<ProgID>Microsoft.DataMining.SamplePlugInAlgorithm.Factory</ProgID>`  
  
 `</Sample_PlugIn_Algorithm>`  
  
 `...`  
  
 `</Algorithms>`  
  
 `...`  
  
 `</DataMining>`  
  
 `...`  
  
 `</ConfigurationSettings>`  
  
## <a name="see-also"></a>参照  
 [データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [DMSCHEMA_MINING_SERVICES 行セット](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-services-rowset.md)  
  
  

