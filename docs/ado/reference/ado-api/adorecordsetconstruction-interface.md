---
title: "ADORecordsetConstruction インターフェイス |Microsoft ドキュメント"
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
- ADORecordsetConstruction
helpviewer_keywords:
- ADORecordsetConstruction interface [ADO]
ms.assetid: 08386eba-f1f7-4879-8ffd-8733930ecb2f
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3da6260d5e0d4e503dae54e6ffc13f6d35f1890d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="adorecordsetconstruction-interface"></a>ADORecordsetConstruction インターフェイス
**ADORecordsetConstruction**インターフェイスは、ADO を構築するために使用**Recordset**オブジェクトを OLE DB から**行セット**C/C++ アプリケーション内のオブジェクト。  
  
 このインターフェイスは、次のプロパティをサポートします。  
  
## <a name="properties"></a>[プロパティ]  
  
|||  
|-|-|  
|[章](../../../ado/reference/ado-api/chapter-property-ado.md)|読み取り/書き込みです。<br />OLE DB を取得/設定**章**オブジェクトから/この ADO に**Recordset**オブジェクト。|  
|[RowPosition](../../../ado/reference/ado-api/rowposition-property-ado.md)|読み取り/書き込みです。<br />OLE DB を取得/設定**RowPosition**オブジェクトから/この ADO に**Recordset**オブジェクト。|  
|[行セット](../../../ado/reference/ado-api/rowset-property-ado.md)|読み取り/書き込みです。<br />OLE DB を取得/設定**行セット**オブジェクトから/この ADO に**Recordset**オブジェクト。|  
  
## <a name="methods"></a>メソッド  
 [なし] :  
  
## <a name="events"></a>イベント  
 [なし] :  
  
## <a name="remarks"></a>解説  
 指定された OLE DB**行セット**オブジェクト (`pRowset`)、ADO の構築**レコード セット**オブジェクト (`adoRs`) 次の 3 つの基本的な操作を額。  
  
1.  ADO を作成する**Recordset**オブジェクト。  
  
    ```  
    Recordset20Ptr adoRs;  
    adoRs.CreateInstance(__uuidof(Recordset));  
    ```  
  
2.  クエリ、 **IADORecordsetConstruction**インターフェイスを**Recordset**オブジェクト。  
  
    ```  
    adoRecordsetConstructionPtr adoRsConstruct=NULL;  
    adoRs->QueryInterface(__uuidof(ADORecordsetConstruction),  
                         (void**)&adoRsConstruct);  
    ```  
  
3.  呼び出す、`IADORecordsetConstruction::put_Rowset`プロパティを設定するメソッド、OLE DB `Rowset` 、ADO 上のオブジェクト`Recordset`オブジェクト。  
  
    ```  
    IUnknown *pUnk=NULL;  
    pRowset->QueryInterface(IID_IUnknown, (void**)&pUnk);  
    adoRsConstruct->put_Rowset(pUnk);  
    ```  
  
 結果`adoRs`オブジェクトは、ADO を表します**Recordset** 、OLE DB から構築されたオブジェクト**行セット**オブジェクト。  
  
 ADO を構築することもできます。 **Recordset**オブジェクトを OLE DB から**章**または**RowPosition**オブジェクト。  
  
## <a name="requirements"></a>必要条件  
 **バージョン:** ADO 2.0 以降  
  
 **ライブラリ:** msado15.dll  
  
 **UUID:** 00000283-0000-0010-8000-00AA006D2EA4  
  
## <a name="see-also"></a>参照  
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [行セット プロパティ (ADO)](../../../ado/reference/ado-api/rowset-property-ado.md)

