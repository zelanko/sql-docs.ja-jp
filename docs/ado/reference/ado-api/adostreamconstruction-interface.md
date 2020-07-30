---
title: ADOStreamConstruction Interface |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADOStreamConstruction
helpviewer_keywords:
- ADOStreamConstruction interface [ADO]
ms.assetid: 92f5a939-3e1a-4b14-a9dd-90e6ce2dec74
author: rothja
ms.author: jroth
ms.openlocfilehash: 75af8d899c4fb0b97f4ee09795888ef773999b60
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242812"
---
# <a name="adostreamconstruction-interface"></a>ADOStreamConstruction インターフェイス
**ADOStreamConstruction**インターフェイスは、C/c + + アプリケーションの OLE DB **ISTREAM**オブジェクトから ADO**ストリーム**オブジェクトを構築するために使用されます。  
  
## <a name="properties"></a>プロパティ  
  
|プロパティ|説明|  
|-|-|  
|[Stream](../../../ado/reference/ado-api/stream-property.md)|読み取り/書き込み。 OLE DB**ストリーム**オブジェクトを取得/設定します。|  
  
## <a name="methods"></a>メソッド  
 [なし] :  
  
## <a name="events"></a>events  
 [なし] :  
  
## <a name="remarks"></a>解説  
 OLE DB **IStream**オブジェクト () を指定した `pStream` 場合、ADO **Stream**オブジェクト () の構造は、 `adoStr` 次の3つの基本的な操作になります。  
  
1.  ADO**ストリーム**オブジェクトを作成します。  
  
    ```  
    Stream20Ptr adoStr;  
    adoStr.CreateInstance(__uuidof(Stream));  
    ```  
  
2.  **ストリーム**オブジェクトの**IADOStreamConstruction**インターフェイスに対してクエリを実行します。  
  
    ```  
    adoStreamConstructionPtr adoStrConstruct=NULL;  
    adoStr->QueryInterface(__uuidof(ADOStreamConstruction),  
                         (void**)&adoStrConstruct);  
    ```  
  
 `IADOStreamConstruction::get_Stream`プロパティメソッドを呼び出して、ADO **Stream**オブジェクトの OLE DB **IStream**オブジェクトを設定します。  
  
```  
IUnknown *pUnk=NULL;  
pRowset->QueryInterface(IID_IUnknown, (void**)&pUnk);  
adoStrConstruct->put_Stream(pUnk);  
```  
  
 結果の `adoStr` オブジェクトは、OLE DB **IStream**オブジェクトから構築された ADO**ストリーム**オブジェクトを表します。  
  
## <a name="requirements"></a>必要条件  
 **バージョン:** ADO 2.0 以降のバージョン  
  
 **ライブラリ:** msado15.dll  
  
 **UUID:** 00000283-0000-0010-8000-00AA006D2EA4  
  
## <a name="see-also"></a>参照  
 [ADO の API リファレンス](../../../ado/reference/ado-api/ado-api-reference.md)
