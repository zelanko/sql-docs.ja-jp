---
description: Open メソッド (ADO Connection)
title: Open メソッド (ADO Connection) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::raw_Open
- Connection15::Open
- _Connection::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: 663defab-5545-4973-9036-24d5882c9737
author: rothja
ms.author: jroth
ms.openlocfilehash: 1cfba7ddf3192d8bbc81d051e1c29ac27303ef68
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442984"
---
# <a name="open-method-ado-connection"></a>Open メソッド (ADO Connection)
データソースへの接続を開きます。  
  
## <a name="syntax"></a>構文  
  
```  
  
connection.Open ConnectionString, UserID, Password, Options  
```  
  
#### <a name="parameters"></a>パラメーター  
 *文字列*  
 任意。 接続情報を含む **文字列** 値です。 有効な設定の詳細については、 [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) プロパティを参照してください。  
  
 *UserID*  
 任意。 接続を確立するときに使用するユーザー名を含む **文字列** 値です。  
  
 *パスワード*  
 任意。 接続を確立するときに使用するパスワードを含む **文字列** 値です。  
  
 *[オプション]*  
 任意。 このメソッドが (同期的に) 後に返すか、または (非同期に) 接続を確立するかを決定する [ConnectOptionEnum](../../../ado/reference/ado-api/connectoptionenum.md) 値。  
  
## <a name="remarks"></a>解説  
 [Connection](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトで**Open**メソッドを使用すると、データソースへの物理的な接続が確立されます。 このメソッドが正常に完了すると、接続が有効になり、その接続に対してコマンドを発行して結果を処理できるようになります。  
  
 省略可能な *ConnectionString* 引数を使用して、一連の *引数*を含む接続文字列、セミコロンで区切られた *値* ステートメント、または URL で識別されるファイルまたはディレクトリリソースのいずれかを指定します。 **Connectionstring**プロパティは、 *connectionstring*引数に使用される値を自動的に継承します。 このため、**接続**オブジェクトを開く前に**connectionstring**プロパティを設定するか、 *connectionstring*引数を使用して**Open**メソッド呼び出し中に現在の接続パラメーターを設定またはオーバーライドできます。  
  
 *Connectionstring*引数とオプションの*UserID*および*password*引数の両方でユーザーとパスワードの情報を渡すと、 *userid*と*password*の引数によって*connectionstring*に指定された値が上書きされます。  
  
 開いている **接続**で操作を完了したら、 [Close](../../../ado/reference/ado-api/close-method-ado.md) メソッドを使用して、関連付けられているすべてのシステムリソースを解放します。 オブジェクトを閉じると、メモリから削除されません。プロパティの設定を変更し、 **open** メソッドを使用して後で再び開くことができます。 メモリからオブジェクトを完全に削除するには、オブジェクト変数を *Nothing*に設定します。  
  
> [!NOTE]
>  **リモートデータサービスの使用状況****Open**メソッドをクライアント側の**接続**オブジェクトで使用すると、**接続**オブジェクトで[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)が開かれるまで、サーバーへの接続が実際に確立されることはありません。  
  
> [!NOTE]
>  Http スキームを使用する Url は、 [インターネット公開のために Microsoft OLE DB プロバイダー](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)を自動的に呼び出します。 詳細については、「 [絶対 url と相対 url](../../../ado/guide/data/absolute-and-relative-urls.md)」を参照してください。  
  
## <a name="applies-to"></a>適用対象  
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Open および Close メソッドの例 (VB)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Open および Close メソッドの例 (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Open および Close メソッドの例 (VC + +)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [Open メソッド (ADO Record)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Open メソッド (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Open メソッド (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [OpenSchema メソッド](../../../ado/reference/ado-api/openschema-method.md)
