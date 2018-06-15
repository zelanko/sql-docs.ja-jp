---
title: 後続のメソッド (ADO) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::MoveRecord
- _Record::raw_MoveRecord
helpviewer_keywords:
- MoveRecord method [ADO]
ms.assetid: 6d2807b0-b861-4583-bcaf-fb0b82e0f2d0
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c5171b0399614e266ff5ecfa974921f7bdef7646
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35279621"
---
# <a name="moverecord-method-ado"></a>後続のメソッド (ADO)
表されるエンティティに移動、[レコード](../../../ado/reference/ado-api/record-object-ado.md)別の場所にします。  
  
## <a name="syntax"></a>構文  
  
```  
  
Record.MoveRecord (Source, Destination, UserName, Password, Options, Async)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ソース*  
 任意。 A**文字列**を識別する URL を含む値、**レコード**を移動します。 場合*ソース*を省略するか、空の文字列、これによって表されるオブジェクトを示す**レコード**が移動します。 たとえば場合、**レコード**ファイル、ファイルの内容を表しますが指定された場所に移動されます*先*です。  
  
 *変換先*  
 任意。 A**文字列**場所を指定する URL を含む値で*ソース*移動されます。  
  
 *UserName*  
 任意。 A**文字列**が必要な場合へのアクセスを許可するユーザー ID を表す値*先*です。  
  
 *Password*  
 任意。 A**文字列**必要な場合は、以下のことを確認するためのパスワードを格納している*UserName*です。  
  
 *[オプション]*  
 任意。 A [MoveRecordOptionsEnum](../../../ado/reference/ado-api/moverecordoptionsenum.md)値が既定値は**adMoveUnspecified**です。 このメソッドの動作を指定します。  
  
 *非同期*  
 任意。 A**ブール**値と**True**、この操作を非同期にする必要がありますを指定します。  
  
## <a name="return-value"></a>戻り値  
 A**文字列**値。 値では通常、*先*が返されます。 ただし、返される正確な値は、プロバイダーによって異なります。  
  
## <a name="remarks"></a>コメント  
 値*ソース*と*先*することはできませんと同じです。 それ以外の場合、実行時エラーが発生します。 少なくともサーバー、パス、およびリソースの名前が異なる必要があります。  
  
 インターネット、パブリッシング用プロバイダーを使用して、ファイルに対しては、このメソッドはそれ以外の場合指定しない限り、移動対象のファイルにすべてのハイパー テキスト リンクを更新*オプション*です。 このメソッドは失敗*先*しない限り (たとえば、ファイルまたはディレクトリ)、既存のオブジェクトを識別**adMoveOverWrite**が指定されています。  
  
> [!NOTE]
>  使用して、 **adMoveOverWrite**慎重に行うオプションします。 たとえば、ディレクトリにファイルを移動するときに、このオプションを指定するディレクトリを削除されファイルで置き換えます。  
  
 特定の属性、**レコード**などのオブジェクト、 [ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md)この操作の完了後、プロパティは更新されません。 更新、**レコード**閉じることによってオブジェクトのプロパティ、**レコード**、もう一度開いて、ファイルまたはディレクトリが移動された場所の URL に置き換えます。  
  
 この場合**レコード**から取得された、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)、移動したファイルまたはディレクトリの新しい場所にすぐに反映されません、**レコード セット**です。 更新、**レコード セット**を閉じてから再度開くことができます。  
  
> [!NOTE]
>  Http スキームを使用する Url が自動的に起動、 [Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)です。 詳細については、次を参照してください。[絶対と相対 Url](../../../ado/guide/data/absolute-and-relative-urls.md)です。  
  
## <a name="applies-to"></a>適用対象  
 [Record オブジェクト (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Move メソッド (ADO)](../../../ado/reference/ado-api/move-method-ado.md)   
 [MoveFirst、MoveLast、MoveNext、および MovePrevious メソッド (ADO)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)   
 [MoveFirst、MoveLast、MoveNext、MovePrevious メソッド (RDS)](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)
