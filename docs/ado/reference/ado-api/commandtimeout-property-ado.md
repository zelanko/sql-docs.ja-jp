---
title: CommandTimeout プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::CommandTimeout
helpviewer_keywords:
- CommandTimeout property [ADO]
ms.assetid: c611f857-d6b0-4dca-8925-f4a02e769eb0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7c8c6b10e63e4cacce0124eb11102db796168d9b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67919709"
---
# <a name="commandtimeout-property-ado"></a>CommandTimeout プロパティ (ADO)
コマンドの実行中に、試行を終了してエラーを生成するまでの待機時間を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 コマンドの実行を待機する時間を秒単位で示す**Long 型**の値を設定または返します。 既定値は30です。  
  
## <a name="remarks"></a>解説  
 [接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトまたは[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクトの**CommandTimeout**プロパティを使用して、ネットワークトラフィックまたはサーバーの使用量の遅延が原因で[Execute](../../../ado/reference/ado-api/execute-method-ado-command.md)メソッド呼び出しをキャンセルできるようにします。 コマンドの実行が完了する前に、 **CommandTimeout**プロパティに設定された間隔が経過すると、エラーが発生し、ADO によってコマンドがキャンセルされます。 このプロパティを0に設定すると、ADO は実行が完了するまで無制限に待機します。 コードを記述しているプロバイダーとデータソースで、 **CommandTimeout**機能がサポートされていることを確認します。  
  
 **接続**オブジェクトの**CommandTimeout**設定は、同じ**接続**上の**Command**オブジェクトの**CommandTimeout**設定には影響しません。つまり、 **Command**オブジェクトの**CommandTimeout**プロパティは、 **Connection**オブジェクトの**CommandTimeout**値の値を継承しません。  
  
 **接続オブジェクトで**は、**接続**が開かれると、 **CommandTimeout**プロパティは読み取り/書き込みのままになります。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Command オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|  
  
## <a name="see-also"></a>参照  
 [ActiveConnection、CommandText、CommandTimeout、CommandType、Size、Direction プロパティの例 (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection、CommandText、CommandTimeout、CommandType、Size、Direction プロパティの例 (VC + +)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection、CommandText、CommandTimeout、CommandType、Size、Direction プロパティの例 (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [ConnectionTimeout プロパティ (ADO)](../../../ado/reference/ado-api/connectiontimeout-property-ado.md)
