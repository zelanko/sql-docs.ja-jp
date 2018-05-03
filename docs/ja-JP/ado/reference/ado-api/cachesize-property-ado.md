---
title: CacheSize プロパティ (ADO) |Microsoft ドキュメント
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
- Recordset15::CacheSize
helpviewer_keywords:
- CacheSize property [ADO]
ms.assetid: 49dc9a49-af7b-433b-be36-7a14ca984fb7
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e9ce6769de6a4dded7f5438ab617cf531e72ba3f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="cachesize-property-ado"></a>CacheSize プロパティ (ADO)
レコードの数を示す、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)メモリにローカルにキャッシュされたオブジェクト。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**長い**値は 0 より大きい値で使用する必要があります。 既定値は 1 です。  
  
## <a name="remarks"></a>解説  
 使用して、 **CacheSize**プロパティは、プロバイダーからローカル メモリに一度に取得するレコードの数を制御します。 たとえば場合、 **CacheSize**は 10 ですが最初に開く後、**レコード セット**オブジェクト、プロバイダーがローカル メモリに最初の 10 個のレコードを取得します。 間を移動すると、 **Recordset**オブジェクト、プロバイダーがローカル メモリ バッファーからデータを返します。 過去のキャッシュの最後のレコードを移動するとすぐに、プロバイダーは、キャッシュにデータ ソースから、次の 10 個のレコードを取得します。  
  
> [!NOTE]
>  **CacheSize**に基づく、**開いている行の最大数**プロバイダー固有のプロパティ (で、**プロパティ**のコレクション、 **Recordset**オブジェクト)。 設定することはできません**CacheSize**より大きい値に**最大行数は開いている**です。 セットを開くことができます、プロバイダーによって行の数を変更する**最大行数は開いている**です。  
  
 値**CacheSize**の有効期間中に調整されることができます、 **Recordset**データ ソースから次に、キャッシュ内のレコードの数にのみ影響、オブジェクトがこの値を変更します。 プロパティの値のみを変更しても、キャッシュの現在の内容は変更されません。  
  
 も取得するレコードが少ない場合**CacheSize**を示す、プロバイダーは、残りのレコードを返し、エラーは発生しません。  
  
 A **CacheSize**ゼロに設定は許可されていませんし、エラーが返されます。  
  
 キャッシュから取得したレコードには、他のユーザーが、ソース データに対する同時変更が反映されていません。 すべてのキャッシュされたデータの更新を強制するを使用して、[再同期](../../../ado/reference/ado-api/resync-method.md)メソッドです。  
  
 場合**CacheSize** 1 ナビゲーション メソッドよりも大きい値に設定されます ([移動](../../../ado/reference/ado-api/move-method-ado.md)、 [MoveFirst、MoveLast、MoveNext、および MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)) へのナビゲーションで発生する可能性があります、レコードを取得した後、削除が発生した場合、レコードが削除されます。 最初のフェッチ後以降の削除は反映されませんデータ キャッシュ内の削除された行のデータ値にアクセスしようとするまで。 ただし、設定**CacheSize**いずれかに削除された行は取得できないためにこの問題を排除します。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [CacheSize プロパティの例 (VB)](../../../ado/reference/ado-api/cachesize-property-example-vb.md)   
 [CacheSize プロパティの例 (vc++)](../../../ado/reference/ado-api/cachesize-property-example-vc.md)   
 [CacheSize プロパティの例 (JScript)](../../../ado/reference/ado-api/cachesize-property-example-jscript.md)
