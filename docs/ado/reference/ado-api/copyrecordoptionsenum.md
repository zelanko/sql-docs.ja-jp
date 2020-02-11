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
ms.openlocfilehash: 6692125b7323bedc7a416e51555c373ef850ce0a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67919379"
---
# <a name="copyrecordoptionsenum"></a>CopyRecordOptionsEnum
[Copyrecord](../../../ado/reference/ado-api/copyrecord-method-ado.md)メソッドの動作を指定します。  
  
|常時|値|[説明]|  
|--------------|-----------|-----------------|  
|**adCopyAllowEmulation**|4|*ターゲット*が別のサーバー上にあるか、*ソース*とは異なるプロバイダーによって処理されることが原因でこのメソッドが失敗した場合*に、ダウンロード*およびアップロード操作を使用してコピーをシミュレートしようとすることを示します。 プロバイダーの機能が異なると、パフォーマンスが低下したり、データが失われることがあります。|  
|**adCopyNonRecursive**|2|現在のディレクトリをコピー先にコピーします。ただし、そのサブディレクトリはコピーしません。 コピー操作は再帰的ではありません。|  
|**adCopyOverWrite**|1 で保護されたプロセスとして起動されました|*コピー先*が既存のファイルまたはディレクトリを指している場合、ファイルまたはディレクトリを上書きします。|  
|**adCopyUnspecified**|-1|既定。 既定のコピー操作を実行します。コピー先のファイルまたはディレクトリが既に存在し、操作が再帰的にコピーされる場合、操作は失敗します。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 これらの定数には、対応する ADO/WFC がありません。  
  
## <a name="applies-to"></a>適用対象  
 [CopyRecord メソッド (ADO)](../../../ado/reference/ado-api/copyrecord-method-ado.md)
