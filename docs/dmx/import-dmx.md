---
title: インポート (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2141a4f8ccc6e34ec3010ad3ce8e8e3789d09132
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68892754"
---
# <a name="import-dmx"></a>IMPORT (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Analysis Services バックアップファイル (abf) ファイルからサーバーにマイニングモデルまたはマイニング構造を読み込みます。  
  
## <a name="syntax"></a>構文  
  
```  
  
IMPORT FROM <filename>  
```  
  
## <a name="arguments"></a>引数  
 */db*  
 インポートするファイルの名前と場所を表す文字列。  
  
## <a name="remarks"></a>Remarks  
 オブジェクトが指定されていない場合は、.dmb ファイルの内容全体が読み込まれます。 .dmb ファイルに、サーバー上に存在しないデータベースが含まれている場合、そのデータベースが作成されます。  
  
 オブジェクトをエクスポートまたはインポートするには、データベースまたはサーバーの管理者である必要があります。  
  
## <a name="import-from-file-example"></a>ファイルからインポートする例  
 次の例では、アソシエーションモデルと構造を含むファイルの内容全体を現在のサーバーにインポートします。  
  
```  
IMPORT FROM 'C:\TEMP\Association_NEW.dmb'  
```  
  
## <a name="see-also"></a>参照  
 [DMX&#41; データ定義ステートメント &#40;のデータマイニング拡張機能](../dmx/dmx-statements-data-definition.md)   
 [DMX&#41; データ操作ステートメントを &#40;データマイニング拡張機能](../dmx/dmx-statements-data-manipulation.md)   
 [DMX&#41; ステートメントリファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-statements.md)   
 [DMX&#41;のエクスポート &#40;](../dmx/export-dmx.md)   
 [データ マイニング オブジェクトのエクスポートおよびインポート](https://docs.microsoft.com/analysis-services/data-mining/export-and-import-data-mining-objects)  
  
  
