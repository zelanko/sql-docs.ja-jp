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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 5fde8adfb1b3f78e8dd0d047f8b100ddada4608c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66698685"
---
# <a name="commandtype-property-ado"></a>CommandType プロパティ (ADO)
型を示す、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクト。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 1 つまたは複数を取得または設定[CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)値。  
  
> [!NOTE]
>  使用しないでください、 **CommandTypeEnum**値**adCmdFile**または**adCmdTableDirect**で**CommandType**します。 これらの値は、オプションとしてのみ使用できます、[オープン](../../../ado/reference/ado-api/open-method-ado-recordset.md)と[Requery](../../../ado/reference/ado-api/requery-method.md)のメソッド、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)します。  
  
## <a name="remarks"></a>コメント  
 使用して、 **CommandType**プロパティの評価を最適化するために、 [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)プロパティ。  
  
 場合、 **CommandType**プロパティの値は、既定値に設定されて**adCmdUnknown**、ADO プロバイダーの呼び出しかを判断する必要があるために、パフォーマンスの低下が発生する可能性があります、 **CommandText**プロパティが、SQL ステートメント、ストアド プロシージャ、またはテーブル名。 コマンドの種類を使用している場合は、設定、 **CommandType**プロパティに関連するコードに直接移動する ADO がよう指示します。 場合、 **CommandType**プロパティは、コマンドの種類と一致しません、 **CommandText**プロパティを呼び出すときにエラーが発生した、 [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md)メソッド。  
  
## <a name="applies-to"></a>適用対象  
 [Command オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの例 (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの例 (vc++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの例 (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
