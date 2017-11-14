---
title: "Mode プロパティ (ADO) |Microsoft ドキュメント"
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
- Connection15::Mode
- _Stream::Mode
- _Record::Mode
helpviewer_keywords:
- Mode property [ADO]
ms.assetid: 808661eb-0d7c-4e6d-8e40-9dc3bef3d77a
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9ee4463749e231b6ecd48a1fa24af1a72b3766ef
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="mode-property-ado"></a>Mode プロパティ (ADO)
データの変更の利用可能なアクセス許可を示す、[接続](../../../ado/reference/ado-api/connection-object-ado.md)、[レコード](../../../ado/reference/ado-api/record-object-ado.md)、または[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクト。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、 [ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md)値。 既定値、**接続**は**adModeUnknown**です。 既定値、**レコード**オブジェクトが**adModeRead**です。 既定値、**ストリーム**基になるソースに関連付けられている (または既定値として、ソースとして URL を使用して開いた**ストリーム**の**レコード**) は**adModeRead**です。 既定値、**ストリーム**、基になると関連付けられていません (メモリ内インスタンス化された) ソースは**adModeUnknown**です。  
  
## <a name="remarks"></a>解説  
 使用して、**モード**プロパティを設定または現在の接続で使用中で、プロバイダーによってアクセス許可を取得します。 設定することができます、**モード**プロパティされる場合にのみ、**接続**オブジェクトが閉じられています。  
  
 **ストリーム**オブジェクトを開くために使用するソースから継承されている、アクセス モードが指定されていない場合、**ストリーム**オブジェクト。 たとえば場合、**ストリーム**から開かれた、**レコード**として同じモードで開かれている既定のオブジェクト、**レコード**です。  
  
 このプロパティは読み取り/書き込み、オブジェクトが開いているときに、オブジェクトは閉じていて、読み取り専用です。  
  
> [!NOTE]
>  **リモートのデータ サービスの使用法**クライアント側で使用すると**接続**オブジェクト、**モード**プロパティのみ設定できます**adModeUnknown**です。  
  
## <a name="applies-to"></a>適用対象  
  
||||  
|-|-|-|  
|[接続オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Record オブジェクト (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[ストリーム オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|  
  
## <a name="see-also"></a>参照  
 [IsolationLevel とモードのプロパティの例 (VB)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vb.md)   
 [IsolationLevel とモードのプロパティの例 (vc++)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vc.md)   

