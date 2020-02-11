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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67931144"
---
# <a name="saveoptionsenum"></a>SaveOptionsEnum
[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクトから保存するときにファイルを作成するか上書きするかを指定します。 値には、 **adSaveCreateNotExist**または**adSaveCreateOverWrite**を指定できます。  
  
|常時|値|[説明]|  
|--------------|-----------|-----------------|  
|**adSaveCreateNotExist**|1 で保護されたプロセスとして起動されました|既定。 *FileName*パラメーターで指定したファイルがまだ存在しない場合は、新しいファイルを作成します。|  
|**adSaveCreateOverWrite**|2|*Filename*パラメーターで指定されたファイルが既に存在する場合、ファイルを現在開いている**ストリーム**オブジェクトのデータで上書きします。 *Filename*パラメーターで指定されたファイルが存在しない場合は、新しいファイルが作成されます。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 これらの定数には、対応する ADO/WFC がありません。  
  
## <a name="applies-to"></a>適用対象  
 [SaveToFile メソッド](../../../ado/reference/ado-api/savetofile-method.md)
