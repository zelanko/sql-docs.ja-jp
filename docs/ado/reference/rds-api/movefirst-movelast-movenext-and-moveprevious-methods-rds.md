---
title: MoveFirst、MoveLast、MoveNext、および MovePrevious メソッド (RDS) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- MoveLast method [RDS]
- MovePrevious method [RDS]
- MoveFirst method [RDS]
- MoveNext method [RDS]
ms.assetid: 45c80bb5-136f-4204-9df2-78740fa55574
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7b57fef531fd66e9e649cba77b88d666281b273f
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35288320"
---
# <a name="movefirst-movelast-movenext-and-moveprevious-methods-rds"></a>MoveFirst、MoveLast、MoveNext、および MovePrevious メソッド (RDS)
First、last に移動次、または前のレコードを指定した[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
DataControl.Recordset.{MoveFirst | MoveLast | MoveNext | MovePrevious}  
```  
  
#### <a name="parameters"></a>パラメーター  
 *DataControl*  
 オブジェクト変数を表す、 [.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクト。  
  
## <a name="remarks"></a>コメント  
 使用することができます、**移動**メソッド、 **.rds ですDataControl** Web ページ上のデータ バインド コントロール内のデータ レコード間を移動するオブジェクト。 たとえば、表示する、 **Recordset**にバインドしてグリッドで、 **.rds ですDataControl**オブジェクト。 ユーザーが最初に移動、最後、次へ をクリックして、First、Last、Next と前のボタンを含めることができますし、表示されている前のレコードまたは**レコード セット**です。 呼び出すことによって、これを行う、 **MoveFirst**、 **MoveLast**、 **MoveNext**、および**MovePrevious**のメソッド、 **.rds ですDataControl**それぞれ First、Last、Next と前のボタンの onClick プロシージャ内のオブジェクトします。 [アドレス帳例](../../../ado/guide/remote-data-service/address-book-navigation-buttons.md)これを行う方法を示します。  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [Move メソッド (ADO)](../../../ado/reference/ado-api/move-method-ado.md)   
 [MoveFirst、MoveLast、MoveNext、および MovePrevious メソッド (ADO)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)   
 [MoveRecord メソッド (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)


