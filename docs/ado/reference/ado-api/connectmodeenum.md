---
title: "ConnectModeEnum |Microsoft ドキュメント"
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
- ConnectModeEnum
helpviewer_keywords:
- ConnectModeEnum enumeration [ADO]
ms.assetid: 3792c294-5161-4538-a908-22a5fc50b85f
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9f524d7d0385de331abed8d857296c55fcdbdc64
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="connectmodeenum"></a>ConnectModeEnum
内のデータを変更するため利用可能なアクセス許可を指定、[接続](../../../ado/reference/ado-api/connection-object-ado.md)、opening、[レコード](../../../ado/reference/ado-api/record-object-ado.md)の値を指定するか、[モード](../../../ado/reference/ado-api/mode-property-ado.md)のプロパティ、 **レコード**と[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクト。  
  
|定数|[値]|Description|  
|--------------|-----------|-----------------|  
|**adModeRead**|1|読み取り専用のアクセス許可を示します。|  
|**adModeReadWrite**|3|読み取り/書き込みアクセス許可を示します。|  
|**adModeRecursive**|0x400000|他のと組み合わせて使用 *\*ShareDeny\** 値 (**adModeShareDenyNone**、 **adModeShareDenyWrite**、または**adModeShareDenyRead**) 共有の制限は、現在のすべてのサブ レコードに反映されるまで**レコード**です。 これは、影響を与えません場合、**レコード**子はありません。 使用されている場合、実行時エラーが生成された**adModeShareDenyNone**のみです。 ただしで使用する**adModeShareDenyNone**他の値と組み合わせた場合です。 たとえば、使用することができます"**adModeRead**または**adModeShareDenyNone**または**adModeRecursive**"です。|  
|**adModeShareDenyNone**|16|他のユーザーが任意のアクセス許可を持つ接続を開くために使用できます。 他のユーザーに対して、読み取りアクセスも書き込みアクセスも拒否できません。|  
|**adModeShareDenyRead**|4|読み取りアクセス許可で接続を開くには、他のユーザーを禁止します。|  
|**adModeShareDenyWrite**|8|書き込みアクセス許可を持つ接続を開くには、他のユーザーを禁止します。|  
|**adModeShareExclusive**|12|接続を開くには、他のユーザーを禁止します。|  
|**adModeUnknown**|0|既定値です。 アクセス許可が設定されていないか特定できないことを示します。|  
|**adModeWrite**|2|書き込み専用のアクセス許可を示します。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.ConnectMode.READ|  
|AdoEnums.ConnectMode.READWRITE|  
|(AdoEnums.ConnectMode.RECURSIVE の該当するショートカットはありません)|  
|AdoEnums.ConnectMode.SHAREDENYNONE|  
|AdoEnums.ConnectMode.SHAREDENYREAD|  
|AdoEnums.ConnectMode.SHAREDENYWRITE|  
|AdoEnums.ConnectMode.SHAREEXCLUSIVE|  
|AdoEnums.ConnectMode.UNKNOWN|  
|AdoEnums.ConnectMode.WRITE|  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Mode プロパティ (ADO)](../../../ado/reference/ado-api/mode-property-ado.md)|[Open メソッド (ADO Record)](../../../ado/reference/ado-api/open-method-ado-record.md)|  
|[Open メソッド (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)|[Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|
