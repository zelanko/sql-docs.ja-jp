---
title: OriginalValue プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::OriginalValue
helpviewer_keywords:
- OriginalValue property [ADO]
ms.assetid: 6e33c6ec-14d9-4b1d-ba9b-cb99862e7bac
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0d25c44883c7f04f1543639ecc870c00ad5beb9d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47649000"
---
# <a name="originalvalue-property-ado"></a>OriginalValue プロパティ (ADO)
値を示す、[フィールド](../../../ado/reference/ado-api/field-object.md)変更が行われる前に、レコードに存在します。  
  
## <a name="return-value"></a>戻り値  
 返します、**バリアント**変更前のフィールドの値を表す値です。  
  
## <a name="remarks"></a>コメント  
 使用して、 **OriginalValue**を現在のレコードからフィールドの元のフィールドの値を返すプロパティ。  
  
 *即時更新モード*(を呼び出した後にプロバイダーが基になるデータ ソースへの変更書き込みますが、[更新](../../../ado/reference/ado-api/update-method.md)メソッド)、 **OriginalValue**プロパティを返します。変更する前に存在していたフィールドの値 (つまり、前回**更新**メソッドの呼び出し)。 これは、同じ値を[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)メソッドを使用して、置換、[値](../../../ado/reference/ado-api/value-property-ado.md)プロパティ。  
  
 *バッチ更新モード*(をプロバイダーが複数の変更をキャッシュし、呼び出すときにのみ、基になるデータ ソースに書き込む、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)メソッド)、 **OriginalValue**プロパティが変更する前に存在していたフィールドの値を返します (つまり、前回**UpdateBatch**メソッドの呼び出し)。 これは、同じ値を[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)メソッドを使用して、置換、**値**プロパティ。 このプロパティを使用すると、 [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md)プロパティ、バッチ更新プログラムに起因する競合を解決することができます。  
  
## <a name="record"></a>レコード  
 [レコード](../../../ado/reference/ado-api/record-object-ado.md)、オブジェクト、 **OriginalValue**プロパティは空にする前に追加されたフィールドになります[Update](../../../ado/reference/ado-api/update-method.md)が呼び出されます。  
  
## <a name="applies-to"></a>適用対象  
 [Field オブジェクト](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>参照  
 [OriginalValue および UnderlyingValue プロパティの例 (VB)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [OriginalValue および UnderlyingValue プロパティの例 (vc++)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [UnderlyingValue プロパティ](../../../ado/reference/ado-api/underlyingvalue-property.md)
