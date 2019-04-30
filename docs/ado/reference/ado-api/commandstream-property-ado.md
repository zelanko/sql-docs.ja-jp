---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b1048e8d243bd19d86d60c3c4f92e4e4b9d137a9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63267279"
---
# <a name="commandstream-property-ado"></a>CommandStream プロパティ (ADO)
入力として使用するストリームを示す、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクト。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 入力として使用するストリームを取得または設定、**コマンド**オブジェクト。 このストリームの形式は、プロバイダー固有です。詳細については、プロバイダーのドキュメントを参照してください。 このプロパティは、 [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)の入力の文字列を指定するために使用するプロパティを**コマンド**します。  
  
## <a name="remarks"></a>コメント  
 **CommandStream**と**CommandText**は相互に排他的です。 ユーザーが設定した場合、 **CommandStream**プロパティ、 **CommandText**プロパティは空の文字列に設定されます ("")。 ユーザーが設定されている場合、 **CommandText**プロパティ、 **CommandStream**プロパティに設定する**Nothing**。  
  
 動作、 **Command.Parameters.Refresh**と**Command.Prepare**メソッドは、プロバイダーによって定義されます。 ストリーム内のパラメーターの値を更新しないことができます。  
  
 入力ストリームがその他の ADO オブジェクトを返すのソースで使用できる、**コマンド**します。 たとえば場合、[ソース](../../../ado/reference/ado-api/source-property-ado-recordset.md)の[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)に設定されている、**コマンド**、入力としてのストリームを持つオブジェクト**Recordset.Source**返すには引き続き、 **CommandText**プロパティで、空の文字列が含まれています ("") のストリームのコンテンツではなく、 **CommandStream**プロパティ。  
  
 コマンド ストリームを使用する場合 (で指定された**CommandStream**)、唯一の有効な[CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)の値を[CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md)プロパティは**adCmdText**と**adCmdUnknown**します。 その他の値には、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [Command オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [CommandText プロパティ (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [Dialect プロパティ](../../../ado/reference/ado-api/dialect-property.md)   
 [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)
