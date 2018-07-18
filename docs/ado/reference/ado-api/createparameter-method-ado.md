---
title: CreateParameter メソッド (ADO) |Microsoft ドキュメント
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
- Command15::raw_CreateParameter
- Command15::CreateParameter
helpviewer_keywords:
- CreateParameter method [RDS]
ms.assetid: 9666fdcc-0544-4ed7-a97b-c415f2a56d7e
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 865b2b0b8009b03e33e24f72ab4f336910a17ace
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277251"
---
# <a name="createparameter-method-ado"></a>CreateParameter メソッド (ADO)
新たに作成[パラメーター](../../../ado/reference/ado-api/parameter-object.md)指定したプロパティを持つオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
Set parameter = command.CreateParameter (Name, Type, Direction, Size, Value)  
```  
  
## <a name="return-value"></a>戻り値  
 返します、**パラメーター**オブジェクト。  
  
#### <a name="parameters"></a>パラメーター  
 *Name*  
 任意。 A**文字列**値の名前を含む、**パラメーター**オブジェクト。  
  
 *Type*  
 任意。 A[格納](../../../ado/reference/ado-api/datatypeenum.md)のデータ型を指定する値、**パラメーター**オブジェクト。  
  
 *[方向]*  
 任意。 A[値](../../../ado/reference/ado-api/parameterdirectionenum.md)の種類を指定する値**パラメーター**オブジェクト。  
  
 *[サイズ]*  
 任意。 A**長い**文字またはバイトで、パラメーターの値の最大長を指定する値。  
  
 *Value*  
 任意。 A**バリアント**の値を指定する、**パラメーター**オブジェクト。  
  
## <a name="remarks"></a>コメント  
 使用して、 **CreateParameter**メソッドを作成、新しい**パラメーター**指定された名前、型、方向、サイズ、および値を持つオブジェクト。 対応する引数を渡す任意の値が書き込まれます**パラメーター**プロパティです。  
  
 このメソッドは自動的に追加しません、**パラメーター**オブジェクトを**パラメーター**のコレクション、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクト。 これにより、追加のプロパティを追加するときに値が ADO は検証を設定する、**パラメーター**オブジェクトをコレクション。  
  
 内の可変長データ型を指定するかどうか、*型*引数を渡す必要がありますか、*サイズ*引数またはセット、[サイズ](../../../ado/reference/ado-api/size-property-ado-parameter.md)のプロパティ、**パラメーター**オブジェクトに追加する前に、**パラメーター**コレクションです。 それ以外の場合、エラーが発生します。  
  
 数値データ型を指定する場合 (**adNumeric**または**adDecimal**) で、*型*後の引数を設定する必要がありますも、 [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md)と[精度](../../../ado/reference/ado-api/precision-property-ado.md)プロパティです。  
  
## <a name="applies-to"></a>適用対象  
 [Command オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [追加と CreateParameter メソッドの例 (VB)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vb.md)   
 [追加する方法の例を CreateParameter (vc++)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vc.md)   
 [Append メソッド (ADO)](../../../ado/reference/ado-api/append-method-ado.md)   
 [パラメーター オブジェクト](../../../ado/reference/ado-api/parameter-object.md)   
 [Parameters コレクション (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)
