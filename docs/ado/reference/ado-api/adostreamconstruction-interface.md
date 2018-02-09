---
title: "ADOStreamConstruction インターフェイス |Microsoft ドキュメント"
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
- ADOStreamConstruction
helpviewer_keywords:
- ADOStreamConstruction interface [ADO]
ms.assetid: 92f5a939-3e1a-4b14-a9dd-90e6ce2dec74
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 87d609abefd972ec6fe3c9443f658ffbcc069511
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="adostreamconstruction-interface"></a>ADOStreamConstruction インターフェイス
**ADOStreamConstruction**インターフェイスは、ADO を構築するために使用**ストリーム**オブジェクトを OLE DB から**IStream** C/C++ アプリケーション内のオブジェクト。  
  
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|[Stream プロパティ](../../../ado/reference/ado-api/stream-property.md)|読み取り/書き込みです。 OLE DB を取得/設定**ストリーム**オブジェクト。|  
  
## <a name="methods"></a>メソッド  
 [なし] :  
  
## <a name="events"></a>イベント  
 [なし] :  
  
## <a name="remarks"></a>解説  
 指定された OLE DB **IStream**オブジェクト (`pStream`)、ADO の構築**ストリーム**オブジェクト (`adoStr`) 次の 3 つの基本的な操作を額。  
  
1.  ADO を作成する**ストリーム**オブジェクト。  
  
    ```  
    Stream20Ptr adoStr;  
    adoStr.CreateInstance(__uuidof(Stream));  
    ```  
  
2.  クエリ、 **IADOStreamConstruction**インターフェイスを**ストリーム**オブジェクト。  
  
    ```  
    adoStreamConstructionPtr adoStrConstruct=NULL;  
    adoStr->QueryInterface(__uuidof(ADOStreamConstruction),  
                         (void**)&adoStrConstruct);  
    ```  
  
 呼び出す、`IADOStreamConstruction::get_Stream`プロパティを設定するメソッド、OLE DB **IStream** 、ADO 上のオブジェクト**ストリーム**オブジェクト。  
  
```  
IUnknown *pUnk=NULL;  
pRowset->QueryInterface(IID_IUnknown, (void**)&pUnk);  
adoStrConstruct->put_Stream(pUnk);  
```  
  
 結果として得られる`adoStr`オブジェクトは、ADO を表します**ストリーム**、OLE DB から構築されたオブジェクト**IStream**オブジェクト。  
  
## <a name="requirements"></a>必要条件  
 **バージョン:** ADO 2.0 またはそれ以降のバージョン  
  
 **ライブラリ:** msado15.dll  
  
 **UUID:** 00000283-0000-0010-8000-00AA006D2EA4  
  
## <a name="see-also"></a>参照  
 [ADO の API リファレンス](../../../ado/reference/ado-api/ado-api-reference.md)
