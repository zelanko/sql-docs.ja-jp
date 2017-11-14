---
title: "CommandStream プロパティ (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Command::CommandStream
helpviewer_keywords:
- CommandStream property [ADO]
ms.assetid: f78f61b6-87e0-48dc-961e-83d0e20da58e
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 28e4c73b4fdc94be1687ec011ad3a42e5b51bd78
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="commandstream-property-ado"></a>CommandStream プロパティ (ADO)
入力として使用されるストリームを示す、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクト。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 入力として使用されるストリームを取得または設定、**コマンド**オブジェクト。 このストリームの形式は、プロバイダー固有です。詳細については、プロバイダーのマニュアルを参照してください。 このプロパティがに似ていますが、 [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)の入力の文字列を指定するために使用するプロパティ、**コマンド**です。  
  
## <a name="remarks"></a>解説  
 **CommandStream**と**CommandText**は相互に排他的です。 ユーザーが設定した場合、 **CommandStream** 、プロパティ、 **CommandText**プロパティは、空の文字列に設定されます ("") です。 ユーザーを設定する場合、 **CommandText**プロパティ、 **CommandStream**プロパティ設定されます**Nothing**です。  
  
 動作、 **Command.Parameters.Refresh**と**Command.Prepare**メソッドは、プロバイダーによって定義されます。 ストリーム内のパラメーターの値を更新できません。  
  
 入力ストリームが他のソースを返す ADO オブジェクトで使用できる、**コマンド**です。 たとえば場合、[ソース](../../../ado/reference/ado-api/source-property-ado-recordset.md)の[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)に設定されている、**コマンド**の入力としてのストリームを持つオブジェクト**Recordset.Source**返し続けます、 **CommandText**プロパティで、空の文字列が含まれています ("") のストリームの内容ではなく、 **CommandStream**プロパティです。  
  
 コマンド ストリームを使用する場合 (指定に従って**CommandStream**)、唯一の有効な[CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)の値を[CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md)プロパティには**adCmdText**と**adCmdUnknown**です。 その他の値には、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [コマンド オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [CommandText プロパティ (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [Dialect プロパティ](../../../ado/reference/ado-api/dialect-property.md)   
 [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)

