---
title: SaveOptionsEnum |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
ms.openlocfilehash: 739e06a2038a61c821fd9acf779ec70df9621b16
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35281541"
---
# <a name="saveoptionsenum"></a>SaveOptionsEnum
ファイルを作成またはからの保存時に上書きするかどうかを指定します、[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクト。 値を指定できます**adSaveCreateNotExist**または**adSaveCreateOverWrite**.  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adSaveCreateNotExist**|1|既定値です。 ファイルが指定されている場合は、新しいファイルを作成、 *FileName*パラメーターが既に存在しません。|  
|**adSaveCreateOverWrite**|2|現在開かれてからのデータをファイルを上書き**ストリーム**オブジェクトを指定されたファイルの場合、 *Filename*パラメーターは既に存在します。 ファイルが指定されている場合、 *Filename*パラメーターが存在しないか、新しいファイルを作成します。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 これらの定数には、対応する ADO/WFC はありません。  
  
## <a name="applies-to"></a>適用対象  
 [SaveToFile メソッド](../../../ado/reference/ado-api/savetofile-method.md)
