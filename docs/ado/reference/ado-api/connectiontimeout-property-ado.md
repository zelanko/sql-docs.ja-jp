---
title: "ConnectionTimeout プロパティ (ADO) |Microsoft ドキュメント"
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
f1_keywords: Connection15::ConnectionTimeout
helpviewer_keywords: ConnectionTimeout property [ADO]
ms.assetid: 8904a403-1383-4b4b-b53d-5c01d6f5deac
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 17572bfd4ef1de5fa20246f88c8a0187409bbfd4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="connectiontimeout-property-ado"></a>ConnectionTimeout プロパティ (ADO)
試行を終了し、エラーが発生する前に、接続を確立中に待機する時間を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**長い**を示す値を秒単位でどのくらいの期間を開くには、接続の待機です。 既定値は 15 です。  
  
## <a name="remarks"></a>解説  
 使用して、 **ConnectionTimeout**プロパティを[接続](../../../ado/reference/ado-api/connection-object-ado.md)かどうかネットワーク トラフィックやサーバーの使用による遅延が、接続試行を破棄するために必要なオブジェクトです。 場合、時刻から、 **ConnectionTimeout**プロパティの設定エラーが発生した接続を開く前に経過して、ADO をキャンセルします。 プロパティを 0 に設定すると、ADO は、接続が開かれるまで無期限に待機します。 コードを記述するプロバイダーをサポートしているかどうかを確認、 **ConnectionTimeout**機能します。  
  
 **ConnectionTimeout**プロパティが読み取り/書き込みが開いているとき、接続が閉じていて、読み取り専用です。  
  
## <a name="applies-to"></a>適用対象  
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [ConnectionString、ConnectionTimeout、および (VB) の状態プロパティの例](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [ConnectionString、ConnectionTimeout、および (vc++) の状態プロパティの例](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
 [CommandTimeout プロパティ (ADO)](../../../ado/reference/ado-api/commandtimeout-property-ado.md)
