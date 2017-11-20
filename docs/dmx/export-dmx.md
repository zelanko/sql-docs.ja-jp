---
title: "エクスポート (DMX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- EXPORT
dev_langs:
- DMX
helpviewer_keywords:
- exporting mining models
- exporting mining structures
- mining structures [DMX], exporting
- EXPORT statement
ms.assetid: 97617071-e560-4080-81af-a80276fc0823
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: bfc3e8344d1c6967185979c0970be6d49b572500
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="export-dmx"></a>EXPORT (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  マイニング モデルまたはマイニング構造オブジェクトをサーバーから Analysis Services Backup File (.abf) へ展開します。  
  
## <a name="syntax"></a>構文  
  
```  
  
EXPORT <object type> <object name>[, <object name>] [<object type> <object name>[, <object name] ] TO <filename> [WITH DEPENDENCIES]  
```  
  
## <a name="arguments"></a>引数  
 *オブジェクトの種類*  
 (マイニング モデルまたはマイニング構造) にエクスポートするオブジェクトの型を省略可能です。  
  
 *オブジェクト名*  
 省略可。 エクスポートするオブジェクトの名前です。  
  
 *ファイル名*  
 文字列としてエクスポートするファイルの名前と場所です。  
  
## <a name="remarks"></a>解説  
 ステートメントがマイニング モデルを指定する場合、結果ファイルは関連するマイニング構造も含みます。 ステートメントを指定する場合**WITH DEPENDENCIES**、.abf ファイルに (たとえば、データ ソースおよびデータ ソース ビュー) のオブジェクトを処理するために必要なすべてのオブジェクトが含まれます。  
  
 データベースであるかからオブジェクトをエクスポートまたはインポートするサーバーの管理者、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]データベース。  
  
## <a name="export-mining-structure-example"></a>マイニング構造のエクスポート例  
 次の例は、Targeted Mailing と Forecasting マイニング構造、および Association マイニング モデルを、指定したファイルの場所にエクスポートします。 Association モデルは Market Basket マイニング構造の一部であるため、例では Market Basket 構造もエクスポートします。 アソシエーション モデルを使用してエクスポートされたために、Market Basket マイニング構造の一部はエクスポートされず存在するその他のすべてのマイニング モデル**マイニング モデル**ではなく、**マイニング構造**です。  
  
```  
EXPORT MINING STRUCTURE [Targeted Mailing], [Forecasting] MINING MODEL Association TO 'C:\TM_NEW.abf'  
```  
  
## <a name="export-mining-model-example"></a>マイニング モデルのエクスポート例  
 次の例は、Association マイニング モデルを、指定したファイルの場所にエクスポートします。 ステートメントが指定されているので**WITH DEPENDENCIES**、データ ソースおよびデータ ソース ビュー オブジェクトも .abf ファイルに含まれます。  
  
```  
EXPORT MINING MODEL [Association] TO 'C:\Association_NEW.abf' WITH DEPENDENCIES  
```  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 &#40;DMX&#41;データ定義ステートメント](../dmx/dmx-statements-data-definition.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;データ操作ステートメント](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [インポート &#40;DMX&#41;](../dmx/import-dmx.md)   
 [エクスポートし、インポートのデータ マイニング オブジェクト](../analysis-services/data-mining/export-and-import-data-mining-objects.md)  
  
  

