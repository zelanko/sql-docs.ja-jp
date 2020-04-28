---
title: ExecuteOptionEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ExecuteOptionEnum
helpviewer_keywords:
- ExecuteOptionEnum enumeration [ADO]
ms.assetid: 68bfa83a-5df4-4bef-8736-0f88ae8c29ea
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bef70bd72425e749865e31ecf162e719737dd272
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67932844"
---
# <a name="executeoptionenum"></a>ExecuteOptionEnum
プロバイダーがコマンドを実行する方法を指定します。  
  
|Constant|値|説明|  
|--------------|-----------|-----------------|  
|**adAsyncExecute**|0x10|コマンドを非同期的に実行することを示します。<br /><br /> この値は、 [Commandtypeenum](../../../ado/reference/ado-api/commandtypeenum.md)値**Adcmdtabledirect**と組み合わせることはできません。|  
|**adAsyncFetch**|0x20|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)プロパティで指定された初期数量の後の残りの行を非同期に取得することを示します。|  
|**adAsyncFetchNonBlocking**|0x40|メインスレッドが取得中にブロックされないことを示します。 要求された行が取得されていない場合は、現在の行が自動的にファイルの末尾に移動します。<br /><br /> 永続的に格納された**レコードセット**を含む[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)から[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)を開いた場合、 **adasyncfetchnonblocking ブロッキング**は効果を持ちません。操作は同期およびブロックされます。<br /><br /> **adAsynchFetchNonBlocking**は、**レコードセット**を開くために[adcmdtabledirect](../../../ado/reference/ado-api/commandtypeenum.md)オプションを使用した場合には効果がありません。|  
|**adExecuteNoRecords**|0x80|コマンドテキストが、行を返さないコマンドまたはストアドプロシージャ (たとえば、データを挿入するコマンド) であることを示します。 取得された行は破棄され、返されません。<br /><br /> **adExecuteNoRecords**は、**コマンド**または**接続の Execute**メソッドにオプションのパラメーターとしてのみ渡すことができます。|  
|**adExecuteStream**|0x400|コマンドの実行結果をストリームとして返すことを示します。<br /><br /> **adExecuteStream**は、**コマンドの Execute**メソッドにオプションのパラメーターとしてのみ渡すことができます。|  
|**adExecuteRecord**||**CommandText**が、**レコード**オブジェクトとして返される1つの行を返すコマンドまたはストアドプロシージャであることを示します。|  
|**adOptionUnspecified**|-1|コマンドが指定されていないことを示します。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 パッケージ: **com. ms. wfc. データ**  
  
|Constant|  
|--------------|  
|AdoEnums を実行します。|  
|AdoEnums (ASYNCFETCH)|  
|AdoEnums を指定します。|  
|AdoEnums NORECORDS|  
|AdoEnums。指定されていません。|  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Execute メソッド (ADO Command)](../../../ado/reference/ado-api/execute-method-ado-command.md)|[Execute メソッド (ADO Connection)](../../../ado/reference/ado-api/execute-method-ado-connection.md)|  
|[Open メソッド (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|[Requery メソッド](../../../ado/reference/ado-api/requery-method.md)|
