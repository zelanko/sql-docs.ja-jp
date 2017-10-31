---
title: "インポート (DMX) |Microsoft ドキュメント"
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
f1_keywords:
- IMPORT
dev_langs:
- DMX
helpviewer_keywords:
- IMPORT statement
- mining structures [DMX], importing
ms.assetid: c053bc88-2daf-4ebb-81d7-5a330250536d
caps.latest.revision: 42
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 5510631430ed75a04dd9685d1197f60c64a85aa8
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="import-dmx"></a>IMPORT (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Analysis Services Backup File (.abf) ファイルからサーバー上にマイニング モデルまたはマイニング構造を読み込みます。  
  
## <a name="syntax"></a>構文  
  
```  
  
IMPORT FROM <filename>  
```  
  
## <a name="arguments"></a>引数  
 *ファイル名*  
 インポートするファイルの名前と場所を表す文字列。  
  
## <a name="remarks"></a>解説  
 オブジェクトが指定されない場合、.dmb ファイルのすべてのコンテンツが読み込まれます。 .dmb ファイルに、サーバー上に存在しないデータベースが含まれている場合、そのデータベースが作成されます。  
  
 オブジェクトをエクスポートまたはインポートするには、データベースまたはサーバーの管理者である必要があります。  
  
## <a name="import-from-file-example"></a>ファイルからインポートする例  
 次の例では、アソシエーションのモデルおよび構造を含んでいるファイルのコンテンツ全体を現在のサーバーにインポートします。  
  
```  
IMPORT FROM 'C:\TEMP\Association_NEW.dmb'  
```  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 &#40;DMX"&"#41;データ定義ステートメント](../dmx/dmx-statements-data-definition.md)   
 [データ マイニング拡張機能 &#40;DMX"&"#41;データ操作ステートメント](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能 &#40;DMX"&"#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [エクスポート &#40;DMX"&"#41;](../dmx/export-dmx.md)   
 [エクスポートし、インポートのデータ マイニング オブジェクト](../analysis-services/data-mining/export-and-import-data-mining-objects.md)  
  
  

