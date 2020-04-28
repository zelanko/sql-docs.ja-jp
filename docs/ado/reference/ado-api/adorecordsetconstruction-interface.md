---
title: ADORecordsetConstruction Interface |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordsetConstruction
helpviewer_keywords:
- ADORecordsetConstruction interface [ADO]
ms.assetid: 08386eba-f1f7-4879-8ffd-8733930ecb2f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1e1d14255acd4cc7f18abea1c494353ef970903c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67920790"
---
# <a name="adorecordsetconstruction-interface"></a>ADORecordsetConstruction インターフェイス
**ADORecordsetConstruction**インターフェイスは、C/c + + アプリケーションの OLE DB**行**セットオブジェクトから ADO**レコードセット**オブジェクトを構築するために使用されます。  
  
 このインターフェイスは、次のプロパティをサポートしています。  
  
## <a name="properties"></a>Properties  
  
|||  
|-|-|  
|[章](../../../ado/reference/ado-api/chapter-property-ado.md)|読み取り/書き込み。<br />この ADO**レコードセット**オブジェクトから OLE DB**チャプター**オブジェクトを取得/設定します。|  
|[RowPosition](../../../ado/reference/ado-api/rowposition-property-ado.md)|読み取り/書き込み。<br />この ADO**レコードセット**オブジェクトの/から OLE DB **rowposition**オブジェクトを取得/設定します。|  
|[[行セット]](../../../ado/reference/ado-api/rowset-property-ado.md)|読み取り/書き込み。<br />この ADO**レコードセット**オブジェクトの/から OLE DB**行**セットオブジェクトを取得/設定します。|  
  
## <a name="methods"></a>メソッド  
 なし。  
  
## <a name="events"></a>イベント  
 なし。  
  
## <a name="remarks"></a>Remarks  
 OLE DB の**行**セットオブジェクト (`pRowset`) がある場合、ADO**レコードセット**オブジェクト (`adoRs`) の構造は、次の3つの基本的な操作になります。  
  
1.  ADO**レコードセット**オブジェクトを作成します。  
  
    ```  
    Recordset20Ptr adoRs;  
    adoRs.CreateInstance(__uuidof(Recordset));  
    ```  
  
2.  **レコードセット**オブジェクトの**IADORecordsetConstruction**インターフェイスに対してクエリを実行します。  
  
    ```  
    adoRecordsetConstructionPtr adoRsConstruct=NULL;  
    adoRs->QueryInterface(__uuidof(ADORecordsetConstruction),  
                         (void**)&adoRsConstruct);  
    ```  
  
3.  プロパティメソッドを呼び出して、ADO `Recordset`オブジェクト`Rowset`の OLE DB オブジェクトを設定します。 `IADORecordsetConstruction::put_Rowset`  
  
    ```  
    IUnknown *pUnk=NULL;  
    pRowset->QueryInterface(IID_IUnknown, (void**)&pUnk);  
    adoRsConstruct->put_Rowset(pUnk);  
    ```  
  
 結果`adoRs`のオブジェクトは、OLE DB**行**セットオブジェクトから構築された ADO**レコードセット**オブジェクトを表します。  
  
 また、OLE DB**チャプター**または**ROWPOSITION**オブジェクトから ADO**レコードセット**オブジェクトを構築することもできます。  
  
## <a name="requirements"></a>要件  
 **バージョン:** ADO 2.0 以降  
  
 **ライブラリ:** msado15.dll  
  
 **UUID:** 00000283-0000-0010-8000-00AA006D2EA4  
  
## <a name="see-also"></a>参照  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Rowset プロパティ (ADO)](../../../ado/reference/ado-api/rowset-property-ado.md)
