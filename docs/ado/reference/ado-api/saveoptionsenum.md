---
title: SaveOptionsEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- SaveOptionsEnum
helpviewer_keywords:
- SaveOptionsEnum enumeration [ADO]
ms.assetid: 59339100-6e29-48d1-aea3-6873796d186b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 807a8d7e5757a2caf76f100a1ae51c4a8a3f4e98
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67931144"
---
# <a name="saveoptionsenum"></a>SaveOptionsEnum
[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクトから保存するときにファイルを作成するか上書きするかを指定します。 値には、 **adSaveCreateNotExist**または**adSaveCreateOverWrite**を指定できます。  
  
|Constant|値|説明|  
|--------------|-----------|-----------------|  
|**adSaveCreateNotExist**|1|既定値。 *FileName*パラメーターで指定したファイルがまだ存在しない場合は、新しいファイルを作成します。|  
|**adSaveCreateOverWrite**|2|*Filename*パラメーターで指定されたファイルが既に存在する場合、ファイルを現在開いている**ストリーム**オブジェクトのデータで上書きします。 *Filename*パラメーターで指定されたファイルが存在しない場合は、新しいファイルが作成されます。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 これらの定数には、対応する ADO/WFC がありません。  
  
## <a name="applies-to"></a>適用対象  
 [SaveToFile メソッド](../../../ado/reference/ado-api/savetofile-method.md)
