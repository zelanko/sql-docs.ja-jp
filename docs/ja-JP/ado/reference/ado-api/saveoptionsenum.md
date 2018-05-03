---
title: SaveOptionsEnum |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- SaveOptionsEnum
helpviewer_keywords:
- SaveOptionsEnum enumeration [ADO]
ms.assetid: 59339100-6e29-48d1-aea3-6873796d186b
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ebd08388e2b658c6a4b5d85000d48dd4fe77c671
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="saveoptionsenum"></a>SaveOptionsEnum
ファイルを作成またはからの保存時に上書きするかどうかを指定します、[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクト。 値を指定できます**adSaveCreateNotExist**または**adSaveCreateOverWrite**.  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adSaveCreateNotExist**|1|既定値です。 ファイルが指定されている場合は、新しいファイルを作成、 *FileName*パラメーターが既に存在しません。|  
|**adSaveCreateOverWrite**|2|現在開かれてからのデータをファイルを上書き**ストリーム**オブジェクトを指定されたファイルの場合、 *Filename*パラメーターは既に存在します。 ファイルが指定されている場合、 *Filename*パラメーターが存在しないか、新しいファイルを作成します。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 これらの定数には、対応する ADO/WFC はありません。  
  
## <a name="applies-to"></a>適用対象  
 [SaveToFile メソッド](../../../ado/reference/ado-api/savetofile-method.md)
