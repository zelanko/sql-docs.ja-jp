---
title: プラグインアルゴリズム |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- third-party algorithms [Analysis Services]
- algorithms [data mining], creating
- plugin algorithms [Analysis Services]
ms.assetid: fe364ddc-576e-42fc-9ced-baa399992f92
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ac6494a438f8ecd9c1fb48cc7c2a588cfab9bd9a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66083169"
---
# <a name="plugin-algorithms"></a>プラグイン アルゴリズム
  に用意されている[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]アルゴリズムに加えて、データマイニングに使用できるアルゴリズムは他にも多数あります。 したがって、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、サード パーティ製アルゴリズムを "プラグイン" するためのメカニズムが提供されています。 サード パーティのアルゴリズムが特定の規格に従っている限り、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] アルゴリズムを使用する場合と同様に、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 内でそれらのアルゴリズムを使用できます。 プラグインアルゴリズムには、に用意され[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]ているアルゴリズムのすべての機能が備わっています。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] がプラグイン アルゴリズムとの通信に使用するインターフェイスの詳細については、 [CodePlex](https://go.microsoft.com/fwlink/?LinkID=87843) Web サイトで公開されている、カスタム アルゴリズムとカスタム モデル ビューアーを作成するためのサンプルをご覧ください。  
  
## <a name="algorithm-requirements"></a>アルゴリズムの必要条件  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]にアルゴリズムをプラグインするには、次の COM インターフェイスを実装する必要があります。  
  
 `IDMAlgorithm`  
 モデルを生成するアルゴリズムを実装し、結果のモデルの予測操作を実装します。  
  
 `IDMAlgorithmNavigation`  
 ブラウザーがモデルのコンテンツにアクセスできるようにします。  
  
 `IDMPersist`  
 アルゴリズムによってトレーニングされるモデルを [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]で保存して読み込むことができるようにします。  
  
 `IDMAlgorithmMetadata`  
 アルゴリズムの機能および入力パラメーターを記述します。  
  
 `IDMAlgorithmFactory`  
 アルゴリズム インターフェイスを実装するオブジェクトのインスタンスを作成し、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] にアルゴリズム メタデータ インターフェイスへのアクセスを提供します。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、これらの COM インターフェイスを使用してプラグイン アルゴリズムと通信します。 使用するプラグイン アルゴリズムでは [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB for Data Mining 仕様をサポートしている必要はありますが、仕様内のデータ マイニング オプションをすべてサポートする必要はありません。 アルゴリズムの機能を決定するには、 [MINING_SERVICES](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset) スキーマ行セットを使用できます。 このスキーマ行セットでは、プラグイン アルゴリズム プロバイダーごとにデータ マイニング サポート オプションが一覧表示されます。  
  
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
 [データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining-algorithms-analysis-services-data-mining.md)   
 [DMSCHEMA_MINING_SERVICES 行セット](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset)  
  
  
