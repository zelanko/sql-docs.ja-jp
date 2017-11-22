---
title: "レコードにジャンプ |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- record jumping [ADO]
- jumping to record [ADO]
ms.assetid: 6caf6299-2eea-4d34-9b0e-b75aab07b740
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8612ee07c90c315bf5cc1eceb621082ced03d5a3
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="jumping-to-a-record"></a>レコードにジャンプします。
[移動](../../../ado/reference/ado-api/move-method-ado.md)メソッドでは、前方または後方に移動することができます、**レコード セット**次の構文を使用して、レコード数を指定します。  
  
```  
oRs.Move NumRecords, Start  
```  
  
## <a name="remarks"></a>解説  
 **移動**メソッドがすべてでサポートされている**Recordset**オブジェクト。  
  
 場合、 *NumRecords*引数は、0 より大きい値は、現在のレコードの位置を前方に移動 (の終了に向けて、 **Recordset**)。 場合*NumRecords*が現在のレコードの位置は後方に移動、0 より小さい (の先頭に向かって、 **Recordset**)。  
  
 場合、**移動**呼び出しは先頭レコードの前に、のポイントに現在のレコードの位置を移動すると、現在のレコードの最初のレコードの前に、の位置を設定、 **Recordset** (**BOF**は**True**)。 旧バージョンとされる場合に移動しよう、 **BOF**プロパティが既に**True**でエラーが生成されます。  
  
 場合、**移動**呼び出しは最後のレコードの後のポイントに現在のレコードの位置を移動すると、ADO は、後での最後のレコードの位置に、現在のレコードを設定、 **Recordset** (**EOF**は**True**)。 ときに前方に移動しよう、 **EOF**プロパティが既に**True**でエラーが生成されます。  
  
 呼び出す、**移動**メソッドは空の**Recordset**オブジェクト、エラーが発生します。  
  
 内のブックマークを渡した場合、*開始*引数は、このブックマーク レコードに対して相対的です。 移動と仮定した場合、**レコード セット**オブジェクトは、ブックマークをサポートしています。 使用して、ブックマークを取得、[ブックマーク](../../../ado/reference/ado-api/bookmark-property-ado.md)プロパティです。 指定しない場合、現在のレコード相対移動パスです。  
  
 使用している場合、 **CacheSize**受け渡し、プロバイダーからのレコードをローカルにキャッシュするプロパティ、 *NumRecords*引数キャッシュされているレコードの現在のグループの外側、現在のレコードの位置を移動します。強制的にレコードを送信先レコードからの新しいグループを取得します。 **CacheSize**プロパティは、新たに取得したグループのサイズを決定し、送信先レコードは、最初のレコードを取得します。
