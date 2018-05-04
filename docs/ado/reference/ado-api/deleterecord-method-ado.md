---
title: 関係するメソッド (ADO) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_DeleteRecord
- _Record::DeleteRecord
helpviewer_keywords:
- DeleteRecord method [ADO]
ms.assetid: 2726498c-dbd8-4266-983b-ae7d62c39142
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ca7b2a425e24a115b8572f26ec7b2efb103ba9ec
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="deleterecord-method-ado"></a>関係するメソッド (ADO)
によって表されるエンティティを削除、[レコード](../../../ado/reference/ado-api/record-object-ado.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
Record.DeleteRecord Source, Async  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ソース*  
 省略可。 A**文字列**を削除する (たとえば、ファイルまたはディレクトリ) のエンティティを識別する URL を含む値です。 場合*ソース*を省略するか、空の文字列は、現在で表されるエンティティを示す[レコード](../../../ado/reference/ado-api/record-object-ado.md)を削除します。 場合は、レコードは、コレクション ([RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md)の**adCollectionRecord**、ディレクトリなど) (たとえば、サブディレクトリ) のすべての子も削除されます。  
  
 *非同期*  
 省略可。 A**ブール**値と**True**、削除操作を非同期に指定します。  
  
## <a name="remarks"></a>解説  
 これによって表されるオブジェクトで操作**レコード**メソッドの完了後に失敗する可能性があります。 呼び出した後**関係する**、**レコード**ために閉じる必要がありますの動作、**レコード**予測に応じて、プロバイダーを更新したときになる可能性があります、**レコード**データ ソースとします。  
  
 この場合**レコード**から取得された、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)、この操作の結果はすぐに反映されず、**レコード セット**です。 更新、 **Recordset**閉じ、再度開いたとき、またはを実行して、**レコード セット** [Requery](../../../ado/reference/ado-api/requery-method.md)メソッドを[更新](../../../ado/reference/ado-api/update-method.md)メソッド、または[再同期](../../../ado/reference/ado-api/resync-method.md)メソッドです。  
  
> [!NOTE]
>  Http スキームを使用する Url が自動的に起動、 [Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)です。 詳細については、次を参照してください。[絶対と相対 Url](../../../ado/guide/data/absolute-and-relative-urls.md)です。  
  
## <a name="applies-to"></a>適用対象  
 [Record オブジェクト (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Delete メソッド (ADO フィールドのコレクション)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Delete メソッド (ADO パラメーターのコレクション)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Delete メソッド (ADO Recordset)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)
