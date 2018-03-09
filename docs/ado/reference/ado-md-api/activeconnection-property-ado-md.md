---
title: "ActiveConnection プロパティ (ADO MD) |Microsoft ドキュメント"
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
- ActiveConnection
- Cellset::ActiveConnection
- Catalog::ActiveConnection
helpviewer_keywords:
- ActiveConnection property [ADO MD]
ms.assetid: 2509b32c-a995-4364-9152-d8c83129bdd8
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0ec51c77b1963832cf101278b5c00bcbfe253093
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="activeconnection-property-ado-md"></a>ActiveConnection プロパティ (ADO MD)
どの ADO に示す[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトの現在のセル セットまたはカタログが現在属しています。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**バリアント**接続を定義する文字列を格納しているか、**接続**オブジェクト。 既定値は空です。  
  
## <a name="remarks"></a>解説  
 このプロパティを設定するには有効な ado**接続**オブジェクトまたは有効な接続文字列にします。 このプロパティが接続文字列に設定されている場合、プロバイダーは、新しいを作成**接続**オブジェクトのこの定義を使用し、接続を開きます。  
  
 使用する場合、 *ActiveConnection*の引数、[開く](../../../ado/reference/ado-md-api/open-method-ado-md.md)を開くメソッドを[セルセット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)オブジェクト、 **ActiveConnection**がプロパティ引数の値を継承します。  
  
 設定、 **ActiveConnection**のプロパティ、[カタログ](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)オブジェクトを**Nothing**内のデータを含む、関連付けられているデータを解放、 [CubeDefs](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)コレクションおよび関連する[ディメンション](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)、[階層](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)、[レベル](../../../ado/reference/ado-md-api/level-object-ado-md.md)、および[メンバー](../../../ado/reference/ado-md-api/member-object-ado-md.md)オブジェクト。 閉じる、**接続**開くために使用できるオブジェクト、**カタログ**設定と同じ効果を持つ、 **ActiveConnection**プロパティを**Nothing**.  
  
 によって参照される接続の既定のデータベースを変更する、 **ActiveConnection**のプロパティ、**カタログ**オブジェクトの内容が無効になります、**カタログ**です。  
  
 変更しようとする場合、エラーが発生、 **ActiveConnection**プロパティを開いている**セルセット**オブジェクト。  
  
> [!NOTE]
>  Visual basic を使用してください、**設定**キーワードを設定する場合、 **ActiveConnection**プロパティを**接続**オブジェクト。 省略した場合、**設定**キーワード、実際に設定する場合、 **ActiveConnection**プロパティを等しく、**接続**オブジェクトの既定のプロパティ、 **ConnectionString**です。 コードを実行します。ただし、負の値のパフォーマンスに影響があります。 データ ソースに追加の接続を作成します。  
  
 MSOLAP データ プロバイダーを使用する場合は、サーバー名への接続文字列で、データ ソースを設定し、カタログの名前に、データ ソースから初期カタログを設定します。 サーバーから切断されているキューブ ファイルに接続する場合の場所への完全パスを設定します。カブ ファイルです。 どちらの場合は、プロバイダー名に、プロバイダーを設定します。 たとえば、次の文字列がという名前のサーバーからのビデオのストアをという名前のカタログに接続する MSOLAP プロバイダーを使用**Servername**:  
  
```  
"Data Source=Servername;Initial Catalog=Bobs Video Store;Provider=msolap"  
```  
  
 次の文字列は、C:\MSDASDK\samples\oledb\olap\data\bobsvid.cub の場所にローカル キューブ ファイルに接続します。  
  
```  
"Location=C:\MSDASDK\samples\oledb\olap\data\bobsvid.cub;Provider=msolap"  
```  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Catalog オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|[CellSet オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)|  
  
## <a name="see-also"></a>参照  
 [セル セットの例 (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [接続オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Open メソッド (ADO MD)](../../../ado/reference/ado-md-api/open-method-ado-md.md)
