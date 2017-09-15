---
title: "レコード セットのベース テーブル (ADO) にコントロールが変更された |Microsoft ドキュメント"
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
helpviewer_keywords:
- Unique Table property [ADO]
- Unique Schema property [ADO]
- Unique Catalog property [ADO]
ms.assetid: d0e775d8-e353-46a1-ad10-ed4cc240dfaa
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: da2f70b0f3d6f1ae3983e44f26191e13cc26f5a2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="unique-table-unique-schema-unique-catalog-properties-dynamic-ado"></a>一意テーブル、一意なスキーマ、一意なカタログ プロパティ動的 (ADO)
特定のベース テーブルに密接にコントロール変更に使用すると、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)を複数のベース テーブルに対して結合操作によって形式がありません。  
  
-   **一意テーブル**更新、挿入、および削除を許可する基になるベース テーブルの名前を指定します。  
  
-   **一意なスキーマ**を指定します、*スキーマ*、またはテーブルの所有者の名前。  
  
-   **固有のカタログ**を指定します、*カタログ*、またはテーブルを含むデータベースの名前。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**文字列**テーブル、スキーマ、またはカタログの名前を指定する値。  
  
## <a name="remarks"></a>解説  
 目的の基底のテーブルは、カタログ、スキーマ、およびテーブル名によって一意に識別します。 ときに、**一意テーブル**プロパティは、の値を設定、**一意なスキーマ**または**固有のカタログ**プロパティを使用して、ベース テーブルを検索します。 これはためのもので、必須ではありませんがそのいずれかまたは両方、**一意なスキーマ**と**固有のカタログ**プロパティを設定する前に、**一意テーブル**プロパティを設定します。  
  
 主キー、**一意テーブル**全体の主キーとして扱われます**Recordset**です。 これは、主キーを必要とするすべてのメソッドで使用されるキーです。  
  
 中に**一意テーブル**が設定されている、[削除](../../../ado/reference/ado-api/delete-method-ado-recordset.md)メソッドは、名前付きのテーブルのみに影響します。 [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)、[再同期](../../../ado/reference/ado-api/resync-method.md)、[更新](../../../ado/reference/ado-api/update-method.md)、および[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)メソッド、の適切な基になるベーステーブルに影響を与える**Recordset**です。  
  
 **一意テーブル**カスタムの再同期を実行する前に指定する必要があります。 場合**一意テーブル**が指定されていません、[コマンドを再同期](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md)プロパティには影響はありません。  
  
 実行時エラーは、一意のベース テーブルが見つからない場合になります。  
  
 これらの動的プロパティはすべてに追加されます、 **Recordset**オブジェクト[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションと、 [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティに設定されている**adUseClient**です。  
  
## <a name="applies-to"></a>適用対象  
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)

