---
title: "モデリング フラグ (DMX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- REGRESSOR flag
- DMX [Analysis Services], modeling flags
- MODEL_EXISTENCE_ONLY flag
- modeling flags [DMX]
- Data Mining Extensions [Analysis Services], modeling flags
- flags [DMX]
- NOT NULL flag
ms.assetid: 498d25f7-9597-47ae-8717-61ddd1d2fd15
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ce032085f10db22608aee69b886724309e83506b
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="modeling-flags-dmx"></a>モデリング フラグ (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  モデリング フラグを使用する[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]データ マイニング アルゴリズムには、ケース テーブルで定義されているデータに関する追加の情報を提供します。 アルゴリズムは、この情報を使用して、より正確なデータ マイニング モデルを作成することができます。 モデリング フラグは、マイニング構造列およびマイニング モデル列のいずれに対しても定義できます。  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]次のモデリング フラグをサポートしています。  
  
 **NOT NULL します。**  
 この属性列の値は NULL 値を含むことはありません。 モデルの学習プロセス中に、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] がこの属性列に NULL 値を検出した場合、エラーが発生します。 このフラグはマイニング構造列で定義されます。  
  
 **リグレッサー**  
 アルゴリズムが、指定した列を回帰アルゴリズムの回帰式に使用できることを示します。 このフラグは、[!INCLUDE[msCoName](../includes/msconame-md.md)] Linear Regression および [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees アルゴリズムによってサポートされており、マイニング モデル列で定義されます。  
  
 **MODEL_EXISTENCE_ONLY**  
 この属性列の値は、属性の有無ほど重要ではありません。 このフラグはマイニング モデル列で定義されます。  
  
 サード パーティのアルゴリズムによっては、別のモデリング フラグもサポートしている場合があります。 アルゴリズムがどのモデリング フラグを確認するのには、サポートを使用して、 **SUPPORTED_MODELING_FLAGS**スキーマ行セット。 また、サーバーのマイニング サービスに対してクエリを実行し、特定のアルゴリズムでサポートされているモデリング フラグを判別することもできます。 たとえば、次のクエリでは、現在のサーバー上の Microsoft 線形回帰アルゴリズムでサポートされているモデリング フラグが返されます。  
  
```  
SELECT SUPPORTED_MODELING_FLAGS  
FROM $SYSTEM.DMSCHEMA_MINING_SERVICES  
WHERE SERVICE_NAME = 'Microsoft_Linear_Regression'  
```  
  
 期待される結果:  
  
 NOT NULL、REGRESSOR  
  
## <a name="specifying-modeling-flags-on-a-mining-model"></a>マイニング モデルでのモデリング フラグの指定  
 構文の例についてを[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、マイニング構造列でフラグを指定するためのサポートを参照してください[マイニング構造の作成 (&) #40";"DMX"&"#41;](../dmx/create-mining-structure-dmx.md)です。  
  
 マイニング モデル列でモデリング フラグを指定する構文の例は、次を参照してください。 [ALTER MINING STRUCTURE & #40";"DMX"&"#41;](../dmx/alter-mining-structure-dmx.md)です。  
  
 マイニング モデル列の使用の詳細については、次を参照してください。[マイニング モデル列](../analysis-services/data-mining/mining-model-columns.md)です。  
  
## <a name="see-also"></a>参照  
 [データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;参照](../dmx/data-mining-extensions-dmx-reference.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;構文要素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;構文表記規則](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [一般的な予測関数 (&) #40";"DMX"&"#41;](../dmx/general-prediction-functions-dmx.md)   
 [構造と DMX 予測クエリの使用状況](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [DMX の Select ステートメントを理解します](../dmx/understanding-the-dmx-select-statement.md)  
  
  

