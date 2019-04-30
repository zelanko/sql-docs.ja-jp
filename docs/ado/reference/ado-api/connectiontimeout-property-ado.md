---
title: ConnectionTimeout プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::ConnectionTimeout
helpviewer_keywords:
- ConnectionTimeout property [ADO]
ms.assetid: 8904a403-1383-4b4b-b53d-5c01d6f5deac
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b5cb3e6e1cc4266551bfeabf09bde1a65fea032f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63140258"
---
# <a name="connectiontimeout-property-ado"></a>ConnectionTimeout プロパティ (ADO)
試行を終了し、エラーが発生する前に、接続を確立中に待機する時間を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 設定または取得を**長い**を示す値を秒単位でどのくらいの期間、接続が開くまで待ちます。 既定値は 15 です。  
  
## <a name="remarks"></a>コメント  
 使用して、 **ConnectionTimeout**プロパティを[接続](../../../ado/reference/ado-api/connection-object-ado.md)かどうかネットワーク トラフィックや負荷の高いサーバーの使用による遅延が、接続試行を破棄するために必要なオブジェクトします。 場合、時刻から、 **ConnectionTimeout**プロパティの設定エラーが発生した接続を開く前に経過して、試行が取り消されます。 プロパティを 0 に設定すると、ADO は、接続が開かれるまで無期限に待機します。 コードを記述するプロバイダーがサポートしているかどうかを確認、 **ConnectionTimeout**機能します。  
  
 **ConnectionTimeout**プロパティは、開いているときに、接続が閉じており、読み取り専用と読み取り/書き込みです。  
  
## <a name="applies-to"></a>適用対象  
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [ConnectionString、ConnectionTimeout、および状態のプロパティの例 (VB)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [ConnectionString、ConnectionTimeout、および状態のプロパティの例 (vc++)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
 [CommandTimeout プロパティ (ADO)](../../../ado/reference/ado-api/commandtimeout-property-ado.md)
