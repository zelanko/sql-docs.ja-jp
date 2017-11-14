---
title: "ExecuteOptionEnum |Microsoft ドキュメント"
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
- ExecuteOptionEnum
helpviewer_keywords:
- ExecuteOptionEnum enumeration [ADO]
ms.assetid: 68bfa83a-5df4-4bef-8736-0f88ae8c29ea
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 74248756628e892ff8a00e0e6e206b5eb7639e05
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="executeoptionenum"></a>ExecuteOptionEnum
プロバイダーでのコマンドの実行方法を指定します。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adAsyncExecute**|0x10|コマンドを非同期的に実行することを示します。<br /><br /> この値と組み合わせることはできません、 [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)値**adCmdTableDirect**です。|  
|**adAsyncFetch**|0x20|残りの行を後で指定した初期量を示す、 [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)プロパティを非同期に取得する必要があります。|  
|**adAsyncFetchNonBlocking**|0x40|取得中にメイン スレッドがブロックされないことを示します。 要求された行が取得されなかった場合、現在の行は自動的にファイルの末尾に移動します。<br /><br /> 開く場合、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)から、[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)永続的に格納されたを含む**Recordset**、 **adAsyncFetchNonBlocking**必要はありません効果。この操作は、同期およびブロックされます。<br /><br /> **adAsynchFetchNonBlocking**持たないされるときに有効、 [adCmdTableDirect](../../../ado/reference/ado-api/commandtypeenum.md)オプションを使用して、開く、**レコード セット**です。|  
|**adExecuteNoRecords**|0x80|コマンド テキストがコマンドまたは行 (データの挿入のみコマンドなど) を返さないストアド プロシージャであることを示します。 すべての行が取得された場合、破棄され、返されません。<br /><br /> **adExecuteNoRecords**に省略可能なパラメーターとして渡されることができますのみ、**コマンド**または**接続実行**メソッドです。|  
|**adExecuteStream**|0x400|コマンドの実行の結果をストリームとして返すことを示します。<br /><br /> **adExecuteStream**に省略可能なパラメーターとして渡されることができますのみ、**コマンド実行**メソッドです。|  
|**adExecuteRecord**||示します、 **CommandText**コマンドまたはとして返される必要がありますが、1 つの行を返すストアド プロシージャ、**レコード**オブジェクト。|  
|**adOptionUnspecified**|-1|コマンドは指定されていないことを示します。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.ExecuteOption.ASYNCEXECUTE|  
|AdoEnums.ExecuteOption.ASYNCFETCH|  
|AdoEnums.ExecuteOption.ASYNCFETCHNONBLOCKING|  
|AdoEnums.ExecuteOption.NORECORDS|  
|AdoEnums.ExecuteOption.UNSPECIFIED|  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Execute メソッド (ADO コマンド)](../../../ado/reference/ado-api/execute-method-ado-command.md)|[Execute メソッド (ADO 接続)](../../../ado/reference/ado-api/execute-method-ado-connection.md)|  
|[Open メソッド (ADO レコード セット)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|[Requery メソッド](../../../ado/reference/ado-api/requery-method.md)|

