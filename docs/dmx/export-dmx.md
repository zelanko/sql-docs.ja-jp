---
title: エクスポート (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2cf3cf85b0efb024d65744f6eea0f5eea47ead83
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68074853"
---
# <a name="export-dmx"></a>エクスポート (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  マイニング モデルまたはマイニング構造オブジェクトをサーバーから Analysis Services Backup File (.abf) に抽出します。  
  
## <a name="syntax"></a>構文  
  
```  
  
EXPORT <object type> <object name>[, <object name>] [<object type> <object name>[, <object name] ] TO <filename> [WITH DEPENDENCIES]  
```  
  
## <a name="arguments"></a>引数  
 *オブジェクトの種類*  
 (マイニング モデルまたはマイニング構造) をエクスポートするオブジェクトの型を省略します。  
  
 *オブジェクト名*  
 任意。 エクスポートするオブジェクトの名前。  
  
 *filename*  
 文字列としてエクスポートするファイルの名前と場所です。  
  
## <a name="remarks"></a>コメント  
 ステートメントがマイニング モデルを指定する場合、結果ファイルは関連するマイニング構造も含みます。 ステートメントが指定されている場合**WITH DEPENDENCIES**、(データ ソースとデータ ソース ビューなど) のオブジェクトを処理するために必要なすべてのオブジェクトが、.abf ファイルに含まれます。  
  
 データベースであるか、エクスポートまたはインポートするサーバーの管理者がオブジェクトから、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]データベース。  
  
## <a name="export-mining-structure-example"></a>マイニング構造の例をエクスポートします。  
 次の例は、Targeted Mailing と Forecasting マイニング構造、および Association マイニング モデルを、指定したファイルの場所にエクスポートします。 Association モデルは Market Basket マイニング構造の一部であるため、例では Market Basket 構造もエクスポートします。 使用してアソシエーション モデルがエクスポートされるため、Market Basket マイニング構造の一部はエクスポートされず可能性のあるその他のすべてのマイニング モデル**マイニング モデル**ではなく、**マイニング構造**します。  
  
```  
EXPORT MINING STRUCTURE [Targeted Mailing], [Forecasting] MINING MODEL Association TO 'C:\TM_NEW.abf'  
```  
  
## <a name="export-mining-model-example"></a>マイニング モデルの例をエクスポートします。  
 次の例では、指定したファイルの場所に、Association マイニング モデルをエクスポートします。 ステートメントが指定されているので**WITH DEPENDENCIES**、データ ソースおよびデータ ソース ビュー オブジェクトも .abf ファイルに含まれます。  
  
```  
EXPORT MINING MODEL [Association] TO 'C:\Association_NEW.abf' WITH DEPENDENCIES  
```  
  
## <a name="see-also"></a>関連項目  
 [データ マイニング拡張機能&#40;DMX&#41;データ定義ステートメント](../dmx/dmx-statements-data-definition.md)   
 [データ マイニング拡張機能&#40;DMX&#41;データ操作ステートメント](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能&#40;DMX&#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [インポート&#40;DMX&#41;](../dmx/import-dmx.md)   
 [データ マイニング オブジェクトのエクスポートおよびインポート](../analysis-services/data-mining/export-and-import-data-mining-objects.md)  
  
  
