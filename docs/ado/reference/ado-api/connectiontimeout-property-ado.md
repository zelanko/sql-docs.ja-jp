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
ms.openlocfilehash: 03d3de2c4aabaf4ad8cbc45d9900b33883ff9a48
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67933465"
---
# <a name="connectiontimeout-property-ado"></a>ConnectionTimeout プロパティ (ADO)
接続の確立中に、試行を終了してエラーを生成するまでの待機時間を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 接続を開くまでの待機時間を秒単位で示す**Long 型**の値を設定または返します。 既定値は 15 です。  
  
## <a name="remarks"></a>Remarks  
 ネットワークトラフィックまたはサーバーが過負荷になっている場合[は、接続オブジェクトの](../../../ado/reference/ado-api/connection-object-ado.md) **ConnectionTimeout**プロパティを使用して、接続試行を破棄する必要があります。 接続を開始する前に**ConnectionTimeout**プロパティの設定から経過した時間が経過すると、エラーが発生し、ADO は試行をキャンセルします。 このプロパティを0に設定した場合、ADO は接続が開かれるまで無制限に待機します。 コードを記述しているプロバイダーで、 **ConnectionTimeout**機能がサポートされていることを確認します。  
  
 **ConnectionTimeout**プロパティは、接続が閉じられている場合は読み取り/書き込みが、開いている場合は読み取り専用になります。  
  
## <a name="applies-to"></a>適用対象  
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [ConnectionString、ConnectionTimeout、State プロパティの例 (VB)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [ConnectionString、ConnectionTimeout、State プロパティの例 (VC + +)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
 [CommandTimeout プロパティ (ADO)](../../../ado/reference/ado-api/commandtimeout-property-ado.md)
