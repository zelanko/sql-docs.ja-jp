---
title: "ActiveConnection プロパティ (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Command15::ActiveConnection
- Recordset15::get_ActiveConnection
- _Record::ActiveConnection
helpviewer_keywords:
- ActiveConnection property [ADO]
ms.assetid: 52d0a96c-14fb-4ad9-b004-4d821bc0a6db
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 431438fa61750ca2f8eaee3362f94188e5985523
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="activeconnection-property-ado"></a>ActiveConnection プロパティ (ADO)
示す[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトの指定した[コマンド](../../../ado/reference/ado-api/command-object-ado.md)、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)、または[レコード](../../../ado/reference/ado-api/record-object-ado.md)オブジェクトが現在属しています。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**文字列**接続が閉じられたか、接続の定義を含む値**バリアント**現在を含む**接続**オブジェクトの場合、接続は開いています。 既定値は、null オブジェクト参照です。 参照してください、 [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)プロパティです。  
  
## <a name="remarks"></a>解説  
 使用して、 **ActiveConnection**を決定するプロパティ、**接続**オブジェクトを指定した**コマンド**オブジェクトは実行または指定した**レコード セット**は開かれます。  
  
## <a name="command"></a>Command  
 **コマンド**、オブジェクト、 **ActiveConnection**読み取り/書き込みプロパティです。  
  
 呼び出すしようとすると、 [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md)メソッドを**コマンド**、開いているにこのプロパティを設定する前にオブジェクト**接続**オブジェクトか、有効な接続文字列、エラーが発生します。  
  
 場合、**接続**にオブジェクトが割り当てられた、 **ActiveConnection**プロパティ、オブジェクトを開く必要があります。 閉じた接続オブジェクトを割り当てると、エラーが発生します。  
  
### <a name="note"></a>注意  
 **Microsoft Visual Basic**設定、 **ActiveConnection**プロパティを*Nothing*の関連付けを解除、**コマンド**オブジェクトを現在の**接続**を発生させて、プロバイダーにデータ ソースに関連付けられているリソースを解放します。 関連付けることができますし、**コマンド**同一または別のオブジェクト**接続**オブジェクト。 一部のプロバイダーでは、いずれかから、プロパティの設定を変更できます。**接続**を最初にプロパティを設定することなく別*Nothing*です。  
  
 場合、[パラメーター](../../../ado/reference/ado-api/parameters-collection-ado.md)のコレクション、**コマンド**オブジェクトには、プロバイダーによって指定されたパラメーターが含まれています、設定した場合、コレクションの消去、 **ActiveConnection**プロパティを*Nothing*または別**接続**オブジェクト。 手動で作成する場合[パラメーター](../../../ado/reference/ado-api/parameter-object.md)オブジェクトし、それらを使用して埋める、**パラメーター**のコレクション、**コマンド**オブジェクト、設定、 **ActiveConnection**プロパティを*Nothing*または別**接続**オブジェクトのリーフ、**パラメーター**コレクションをそのまま保持します。  
  
 閉じる、**接続**オブジェクトを**コマンド**オブジェクトが関連付けられている設定、 **ActiveConnection**プロパティを*Nothing*です。 このプロパティを closed に設定**接続**オブジェクト、エラーが発生します。  
  
## <a name="recordset"></a>レコードセット  
 開く**レコード セット**オブジェクトまたは**Recordset**オブジェクト[ソース](../../../ado/reference/ado-api/source-property-ado-recordset.md)プロパティが有効な**コマンド**オブジェクト、 **ActiveConnection**プロパティは読み取り専用です。 それ以外の場合、読み取り/書き込みを勧めします。  
  
 このプロパティを設定するには有効な**接続**オブジェクトまたは有効な接続文字列にします。 この場合、プロバイダーは、作成、新しい**接続**オブジェクトのこの定義を使用し、接続を開きます。 さらに、プロバイダーは、このプロパティを設定を新しい**接続**にアクセスする手段を提供するオブジェクト、**接続**オブジェクトの拡張エラー情報またはその他のコマンドを実行します。  
  
 使用する場合、 *ActiveConnection*の引数、[開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)を開くメソッドを**レコード セット**オブジェクト、 **ActiveConnection**がプロパティ引数の値を継承します。  
  
 設定した場合、**ソース**のプロパティ、 **Recordset**有効なオブジェクト**コマンド**オブジェクト変数を**ActiveConnection**のプロパティ**Recordset**はの設定が継承、**コマンド**オブジェクトの**ActiveConnection**プロパティです。  
  
> [!NOTE]
>  **リモートのデータ サービスの使用法**クライアント側で使用すると**Recordset**オブジェクト、または (Microsoft Visual Basic または Visual Basic Scripting Edition) で接続文字列にのみ、このプロパティを設定できますを*何も行われません*.  
  
## <a name="record"></a>レコード  
 このプロパティは読み取り/書き込み時に、**レコード**オブジェクトが閉じられ、接続文字列または開いているへの参照を含めることがあります**接続**オブジェクト。 このプロパティは読み取り専用ときに、**レコード**オブジェクトが開いていると、開いているへの参照が含まれています**接続**オブジェクト。  
  
 A**接続**オブジェクトが暗黙的に作成されるときに、**レコード**URL からオブジェクトをオープンします。 開く、**レコード**既存を開く**接続**オブジェクトを割り当てることによって、**接続**または、このプロパティにオブジェクトを使用して、**接続**オブジェクト内のパラメーターとして、[開く](../../../ado/reference/ado-api/open-method-ado-record.md)メソッドの呼び出しです。 場合、**レコード**既存から開いた**レコード**または[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)、自動的に関連付けられているし、**レコード**または**レコード セット**オブジェクトの**接続**オブジェクト。  
  
> [!NOTE]
>  Http スキームを使用する Url が自動的に起動、 [Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)です。 詳細については、次を参照してください。[絶対と相対 Url](../../../ado/guide/data/absolute-and-relative-urls.md)です。  
  
## <a name="applies-to"></a>適用対象  
  
||||  
|-|-|-|  
|[コマンド オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Record オブジェクト (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>参照  
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの例 (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの使用例 (vc++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの例 (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [接続オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [ConnectionString プロパティ (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md)

