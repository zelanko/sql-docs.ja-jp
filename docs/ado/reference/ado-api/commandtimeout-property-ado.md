---
title: "CommandTimeout プロパティ (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
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
- Command15::CommandTimeout
helpviewer_keywords:
- CommandTimeout property [ADO]
ms.assetid: c611f857-d6b0-4dca-8925-f4a02e769eb0
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a7848d7fb51a01c35f8a8699b89ea132da36396b
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="commandtimeout-property-ado"></a>CommandTimeout プロパティ (ADO)
試行を終了し、エラーが発生する前に、コマンドを実行中に待機する時間を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**長い**を示す値を秒単位でどのくらいの期間コマンドの実行を待機します。 既定値は 30 です。  
  
## <a name="remarks"></a>解説  
 使用して、 **CommandTimeout**プロパティを[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトまたは[コマンド](../../../ado/reference/ado-api/command-object-ado.md)の取り消しを許可するオブジェクト、 [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md)メソッド呼び出すと、ネットワーク トラフィックやサーバーの使用による遅延が原因です。 間隔設定されている場合、 **CommandTimeout**プロパティまでのコマンドは、実行が完了した、エラーが発生して、コマンドが取り消されます。 プロパティを 0 に設定すると、ADO は、実行が完了するまで無期限に待機します。 コードのサポートを記述するプロバイダーとデータ ソースを確認してください、 **CommandTimeout**機能します。  
  
 **CommandTimeout**の設定、**接続**オブジェクトも何も起こりません、 **CommandTimeout**の設定、**コマンド**オブジェクト上、同じ**接続**ですつまり、**コマンド**オブジェクトの**CommandTimeout**プロパティがの値を継承していない、**接続。**オブジェクトの**CommandTimeout**値。  
  
 **接続**オブジェクト、 **CommandTimeout**プロパティは読み取り/書き込みの後に、**接続**が開かれています。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Command オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|  
  
## <a name="see-also"></a>参照  
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの例 (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの使用例 (vc++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの例 (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [ConnectionTimeout プロパティ (ADO)](../../../ado/reference/ado-api/connectiontimeout-property-ado.md)
