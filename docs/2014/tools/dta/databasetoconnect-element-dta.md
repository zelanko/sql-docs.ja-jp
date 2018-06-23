---
title: DatabaseToConnect 要素 (DTA) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- DatabaseToConnect element
ms.assetid: 65153a66-3aee-4429-99b7-0816ac23c285
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: fb0a5e8b6f20a53f8675e1740ffe57b7227437de
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173586"
---
# <a name="databasetoconnect-element-dta"></a>DatabaseToConnect 要素 (DTA)
  データベース エンジン チューニング アドバイザーがワークロードのチューニング時に最初に接続するデータベースを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
    <TuningOptions>  
...code removed here...  
      <DatabaseToConnect>...</DatabaseToConnect>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|`string`、長さは無制限です。|  
|**既定値**|[なし] :|  
|**個数**|任意。 ごとに 1 回使用できます`TuningOptions`要素。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[TuningOptions 要素&#40;DTA&#41;](tuningoptions-element-dta.md)|  
|**子要素**|なし|  
  
## <a name="remarks"></a>コメント  
 使用して`DatabaseToConnect`データベース エンジン チューニング アドバイザーがチューニング セッションの開始時の接続にする最初のデータベースの名前を指定します。 この要素では、データベースを 1 つだけ指定できます。 複数のデータベース名が指定されていると、データベース エンジン チューニング アドバイザーはエラーを返します。  
  
## <a name="example"></a>例  
 使用例については、「[インライン ワークロードを指定した XML 入力ファイルのサンプル &#40;DTA&#41;](xml-input-file-sample-with-inline-workload-dta.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  