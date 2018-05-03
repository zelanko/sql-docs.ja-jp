---
title: ADORecordConstruction インターフェイス |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordConstruction
helpviewer_keywords:
- ADORecordConstruction interface [ADO]
ms.assetid: 52a5429e-5829-455e-be3b-31f05cbecf2d
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 564d06235e5fcb6e0f12cd17dcb98dda76ddc280
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="adorecordconstruction-interface"></a>ADORecordConstruction インターフェイス
**ADORecordConstruction**インターフェイスは、ADO を構築するために使用**レコード**オブジェクトを OLE DB から**行**C/C++ アプリケーション内のオブジェクト。  
  
 このインターフェイスは、次のプロパティをサポートします。  
  
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|[ParentRow](../../../ado/reference/ado-api/parentrow-property-ado.md)|書き込み専用です。<br />OLE DB のコンテナーを設定**行**この ADO 上のオブジェクト**レコード**オブジェクト。|  
|[行](../../../ado/reference/ado-api/row-property-ado.md)|読み取り/書き込みです。<br />OLE DB を取得/設定**行**オブジェクトから/この ADO に**レコード**オブジェクト。|  
  
## <a name="methods"></a>メソッド  
 [なし] :  
  
## <a name="events"></a>イベント  
 [なし] :  
  
## <a name="remarks"></a>解説  
 指定された OLE DB**行**オブジェクト (`pRow`)、ADO の構築**レコード**オブジェクト (`adoR`)、次の 3 つの基本的な操作を額。  
  
1.  ADO を作成する**レコード**オブジェクト。  
  
    ```  
    _RecordPtr adoR;  
    adoRs.CreateInstance(__uuidof(_Record));  
    ```  
  
2.  クエリ、 **IADORecordConstruction**インターフェイスを**レコード**オブジェクト。  
  
    ```  
    adoRecordConstructionPtr adoRConstruct=NULL;  
    adoR->QueryInterface(__uuidof(ADORecordConstruction),  
                        (void**)&adoRConstruct);  
    ```  
  
3.  呼び出す、 **IADORecordConstruction::put_Row**プロパティを設定するメソッド、OLE DB**行**、ADO 上のオブジェクト**レコード**オブジェクト。  
  
    ```  
    IUnknown *pUnk=NULL;  
    pRow->QueryInterface(IID_IUnknown, (void**)&pUnk);  
    adoRConstruct->put_Row(pUnk);  
    ```  
  
 結果として得られる**adoR**オブジェクトは、ADO を表します**レコード**、OLE DB から構築されたオブジェクト**行**オブジェクト。  
  
 ADO**レコード**OLE DB のコンテナーからオブジェクトを作成することができますも**行**オブジェクト。  
  
## <a name="requirements"></a>必要条件  
 **バージョン:** ADO 2.0 以降  
  
 **ライブラリ:** msado15.dll  
  
 **UUID:** 00000567-0000-0010-8000-00AA006D2EA4
