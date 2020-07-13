---
title: CommandType プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::CommandType
helpviewer_keywords:
- CommandType property [ADO]
ms.assetid: ca44809c-8647-48b6-a7fb-0be70a02f53e
author: rothja
ms.author: jroth
ms.openlocfilehash: bbc90dc2d818ca880a9f712d551fd6a98fb9ecf3
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760428"
---
# <a name="commandtype-property-ado"></a>CommandType プロパティ (ADO)
[Command](../../../ado/reference/ado-api/command-object-ado.md)オブジェクトの種類を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 1つ以上の[Commandtypeenum](../../../ado/reference/ado-api/commandtypeenum.md)値を設定または返します。  
  
> [!NOTE]
>  **Adcmdfile**の**commandtypeenum**値、または**CommandType**と共に**adcmdtabledirect**を使用しないでください。 これらの値は、[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)の[Open](../../../ado/reference/ado-api/open-method-ado-recordset.md)メソッドおよび[Requery](../../../ado/reference/ado-api/requery-method.md)メソッドでオプションとしてのみ使用できます。  
  
## <a name="remarks"></a>Remarks  
 **CommandType**プロパティを使用して、 [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)プロパティの評価を最適化します。  
  
 **CommandType**プロパティ値が既定値の**adcmdunknown**に設定されている場合、 **ado.net プロパティが**SQL ステートメント、ストアドプロシージャ、またはテーブル名であるかどうかを確認するために ADO がプロバイダーの呼び出しを行う必要があるため、パフォーマンスが低下する可能性があります。 使用しているコマンドの種類がわかっている場合は、 **CommandType**プロパティを設定することによって、関連するコードに直接アクセスするように ADO に指示します。 **CommandType**プロパティが**CommandText**プロパティ内のコマンドの型と一致しない場合、 [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md)メソッドを呼び出すとエラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [Command オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [ActiveConnection、CommandText、CommandTimeout、CommandType、Size、Direction プロパティの例 (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection、CommandText、CommandTimeout、CommandType、Size、Direction プロパティの例 (VC + +)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection、CommandText、CommandTimeout、CommandType、Size、Direction プロパティの例 (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
