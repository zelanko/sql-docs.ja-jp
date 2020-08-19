---
description: CommandStream プロパティ (ADO)
title: CommandStream プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Command::CommandStream
helpviewer_keywords:
- CommandStream property [ADO]
ms.assetid: f78f61b6-87e0-48dc-961e-83d0e20da58e
author: rothja
ms.author: jroth
ms.openlocfilehash: 07a16b00a4ec4381dc1dfa07fc57c2b599ed5ba1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450844"
---
# <a name="commandstream-property-ado"></a>CommandStream プロパティ (ADO)
[Command](../../../ado/reference/ado-api/command-object-ado.md)オブジェクトの入力として使用されるストリームを示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 **Command**オブジェクトの入力として使用されるストリームを設定または返します。 このストリームの形式はプロバイダー固有です。詳細については、プロバイダーのドキュメントを参照してください。 このプロパティは、**コマンド**の入力の文字列を指定するために使用される[CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)プロパティに似ています。  
  
## <a name="remarks"></a>解説  
 **Commandstream** と **CommandText** は相互に排他的です。 ユーザーが **Commandstream** プロパティを設定すると、 **CommandText** プロパティが空の文字列 ("") に設定されます。 ユーザーが **CommandText** プロパティを設定した場合、 **Commandstream** プロパティは **Nothing**に設定されます。  
  
 コマンドの動作。 **パラメーターの更新** とコマンドの **Prepare** メソッドは、プロバイダーによって定義されます。 ストリーム内のパラメーターの値は更新できません。  
  
 入力ストリームは、 **コマンド**のソースを返す他の ADO オブジェクトでは使用できません。 たとえば、[レコード](../../../ado/reference/ado-api/recordset-object-ado.md)セットの[ソース](../../../ado/reference/ado-api/source-property-ado-recordset.md)が、入力としてストリームを持つ**コマンド**オブジェクトに設定されている場合、 **commandstream**プロパティのストリームコンテンツではなく、空の文字列 ("") を含む**CommandText**プロパティが返されます **。**  
  
 コマンドストリーム ( **commandstream**で指定) を使用する場合、 [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md)プロパティに有効な[Commandtypeenum](../../../ado/reference/ado-api/commandtypeenum.md)値は**adcmdtext**と**adcmdtext**だけです。 それ以外の値を指定すると、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [Command オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [CommandText プロパティ (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [言語プロパティ](../../../ado/reference/ado-api/dialect-property.md)   
 [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)
