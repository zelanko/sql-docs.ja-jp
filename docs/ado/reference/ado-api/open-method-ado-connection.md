---
title: "Open メソッド (ADO 接続) |Microsoft ドキュメント"
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
- Connection15::raw_Open
- Connection15::Open
- _Connection::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: 663defab-5545-4973-9036-24d5882c9737
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c61284bb59c01e22ef4f2cb46664fe7d7f7bbd2f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="open-method-ado-connection"></a>Open メソッド (ADO 接続)
データ ソースへの接続を開きます。  
  
## <a name="syntax"></a>構文  
  
```  
  
connection.Open ConnectionString, UserID, Password, Options  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ConnectionString*  
 省略可。 A**文字列**接続情報を含む値です。 参照してください、 [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)有効な設定の詳細プロパティです。  
  
 *ユーザー Id*  
 省略可。 A**文字列**接続を確立するときに使用するユーザー名を含む値です。  
  
 *Password*  
 省略可。 A**文字列**接続を確立するときに使用するパスワードを含む値です。  
  
 *および*  
 省略可。 A [ConnectOptionEnum](../../../ado/reference/ado-api/connectoptionenum.md)後に、このメソッドを返すかどうかを決定する値 (同期的に)、または (非同期)、接続が確立される前にします。  
  
## <a name="remarks"></a>解説  
 使用して、**開く**メソッドを[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトは、データ ソースへの物理接続を確立します。 このメソッドが正常に完了すると後の接続はライブおよびに対してコマンドを発行し、結果を処理することができます。  
  
 省略可能なを使用して*ConnectionString*の系列を含む接続文字列を指定する引数*引数**値 =*セミコロンで区切られたステートメントまたはURL で識別されるリソース ファイルまたはディレクトリ。 **ConnectionString**プロパティで使用される値を自動的に継承する、 *ConnectionString*引数。 そのため、設定するか、 **ConnectionString**のプロパティ、**接続**、開く前にオブジェクト、またはを使用して、 *ConnectionString*設定またはオーバーライドへの引数中に現在の接続パラメーター、**開く**メソッドの呼び出しです。  
  
 ユーザー名とパスワード両方の情報を渡す場合、 *ConnectionString*引数と省略可能な*UserID*と*パスワード*、引数、 *UserID*と*パスワード*引数で指定された値が上書きされます*ConnectionString*です。  
  
 開いている操作が完了すると**接続**を使用して、[閉じる](../../../ado/reference/ado-api/close-method-ado.md)を解放するメソッドには、システム リソースが関連付けられています。 オブジェクトを閉じてから削除されませんがメモリです。プロパティの設定を変更して、使用することができます、**開く**を後でもう一度開くメソッドです。 メモリからオブジェクトを完全になくすためには、オブジェクト変数を設定*Nothing*です。  
  
> [!NOTE]
>  **リモートのデータ サービスの使用法**クライアント側で使用すると**接続**オブジェクト、**開く**メソッドは、するまで、サーバーへの接続を確立されません実際には、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)で開かれる、**接続**オブジェクト。  
  
> [!NOTE]
>  Http スキームを使用する Url が自動的に起動、 [Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)です。 詳細については、次を参照してください。[絶対と相対 Url](../../../ado/guide/data/absolute-and-relative-urls.md)です。  
  
## <a name="applies-to"></a>適用対象  
 [接続オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Open および Close メソッドの例 (VB)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Open および Close メソッドの例 (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Open および Close メソッドの例 (vc++)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [Open メソッド (ADO レコード)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Open メソッド (ADO レコード セット)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Open メソッド (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [OpenSchema メソッド](../../../ado/reference/ado-api/openschema-method.md)

