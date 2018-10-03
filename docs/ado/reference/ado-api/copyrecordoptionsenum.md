---
title: CopyRecordOptionsEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CopyRecordOptionsEnum
helpviewer_keywords:
- CopyRecordOptionsEnum enumeration [ADO]
ms.assetid: 2fa4eec5-d50b-4fd3-8ae7-40af441ba12b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fe0b12053b9ac7203253e81fa3300d2e4109a129
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47681568"
---
# <a name="copyrecordoptionsenum"></a>CopyRecordOptionsEnum
動作を指定します、 [CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md)メソッド。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adCopyAllowEmulation**|4|示します、*ソース*プロバイダーによりダウンロードを使用してコピーをシミュレートし、アップロード操作のために、このメソッドが失敗した場合*先*別のサーバー上または異なるによって処理されますプロバイダーよりも*ソース*します。 プロバイダーの機能のさまざまなパフォーマンスが低下したりデータが失われることに注意してください。|  
|**adCopyNonRecursive**|2|現在のディレクトリは、そのサブディレクトリの先にコピーします。 コピー操作は、再帰ではありません。|  
|**adCopyOverWrite**|1|場合、ファイルまたはディレクトリの上書き、*先*既存のファイルまたはディレクトリを指します。|  
|**adCopyUnspecified**|-1|既定値です。 既定のコピー操作を実行します。 コピー先ファイルまたはディレクトリが既に存在する場合、操作は失敗し、操作のコピーは再帰的にします。|  
  
## <a name="adowfc-equivalent"></a>ADO と WFC と同等  
 これらの定数には、ADO と WFC 対応はありません。  
  
## <a name="applies-to"></a>適用対象  
 [CopyRecord メソッド (ADO)](../../../ado/reference/ado-api/copyrecord-method-ado.md)
