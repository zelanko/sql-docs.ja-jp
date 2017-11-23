---
title: "OriginalValue プロパティ (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: Field20::OriginalValue
helpviewer_keywords: OriginalValue property [ADO]
ms.assetid: 6e33c6ec-14d9-4b1d-ba9b-cb99862e7bac
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: baa1b522660f2ed7d521a55ad995ed8347c0a2fb
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="originalvalue-property-ado"></a>OriginalValue プロパティ (ADO)
値を示す、[フィールド](../../../ado/reference/ado-api/field-object.md)すべての変更が行われる前に、レコード内に存在します。  
  
## <a name="return-value"></a>戻り値  
 返します、**バリアント**を変更する前にフィールドの値を表す値です。  
  
## <a name="remarks"></a>解説  
 使用して、 **OriginalValue**プロパティを現在のレコードからフィールドの元のフィールド値を返します。  
  
 *即時更新モード*(をプロバイダーに変更を書き込みます、基になるデータ ソースを呼び出した後、[更新](../../../ado/reference/ado-api/update-method.md)メソッド) では、 **OriginalValue**プロパティを返します。変更前に存在するフィールドの値 (つまり、前回**更新**メソッドの呼び出し)。 これは、同じ値を[ただし](../../../ado/reference/ado-api/cancelupdate-method-ado.md)置換するメソッドを使用して、[値](../../../ado/reference/ado-api/value-property-ado.md)プロパティです。  
  
 *バッチ更新モード*(をプロバイダーが複数の変更をキャッシュし、呼び出した場合にのみ、基になるデータ ソースに書き込みます、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)メソッド) では、 **OriginalValue**プロパティを変更する前に存在するフィールドの値を返します (つまり、前回**UpdateBatch**メソッドの呼び出し)。 これは、同じ値を[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)置換するメソッドを使用して、**値**プロパティです。 このプロパティを使用する場合、 [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md)プロパティ、バッチ更新から発生する競合を解決することができます。  
  
## <a name="record"></a>レコード  
 [レコード](../../../ado/reference/ado-api/record-object-ado.md)、オブジェクト、 **OriginalValue**プロパティは前に追加するフィールドを空になります[更新](../../../ado/reference/ado-api/update-method.md)と呼びます。  
  
## <a name="applies-to"></a>適用対象  
 [Field オブジェクト](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>参照  
 [OriginalValue と UnderlyingValue プロパティの例 (VB)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [OriginalValue と UnderlyingValue プロパティの例 (vc++)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [UnderlyingValue プロパティ](../../../ado/reference/ado-api/underlyingvalue-property.md)
