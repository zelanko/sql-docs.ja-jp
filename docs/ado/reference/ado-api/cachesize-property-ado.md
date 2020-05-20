---
title: CacheSize プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::CacheSize
helpviewer_keywords:
- CacheSize property [ADO]
ms.assetid: 49dc9a49-af7b-433b-be36-7a14ca984fb7
author: rothja
ms.author: jroth
ms.openlocfilehash: 502459b890c533ace8a96847bcf79eb09929e53f
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82758918"
---
# <a name="cachesize-property-ado"></a>CacheSize プロパティ (ADO)
メモリ内にローカルにキャッシュされているレコード[セット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトのレコードの数を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 0より大きくなければならない**Long 型**の値を設定または返します。 既定値は 1 です。  
  
## <a name="remarks"></a>解説  
 プロバイダーからローカルメモリに一度に取得するレコードの数を制御するには、 **CacheSize**プロパティを使用します。 たとえば、 **CacheSize**が10の場合、最初に**レコードセット**オブジェクトを開いた後、プロバイダーは最初の10個のレコードをローカルメモリに取得します。 **レコードセット**オブジェクト内を移動すると、プロバイダーはローカルメモリバッファーからデータを返します。 キャッシュ内の最後のレコードを越えて移動すると、プロバイダーは、次の10個のレコードをデータソースからキャッシュに取得します。  
  
> [!NOTE]
>  **CacheSize**は、**最大 Open Rows**プロバイダー固有のプロパティ ( **Recordset**オブジェクトの**Properties**コレクション内) に基づいています。 **CacheSize**は、**最大開い**ている行よりも大きい値に設定することはできません。 プロバイダーによって開くことができる行の数を変更するには、 **[最大開い**ている行数] を設定します。  
  
 **CacheSize**の値は、**レコードセット**オブジェクトの有効期間中に調整できますが、この値を変更しても、後でデータソースからデータを取得した後のキャッシュ内のレコードの数に影響します。 プロパティ値だけを変更しても、キャッシュの現在の内容は変更されません。  
  
 取得するレコードの数が**CacheSize**よりも小さい場合、プロバイダーは残りのレコードを返し、エラーは発生しません。  
  
 **CacheSize**設定0は許可されていないため、エラーが返されます。  
  
 キャッシュから取得されたレコードには、他のユーザーがソースデータに対して行った同時変更は反映されません。 キャッシュされたすべてのデータを強制的に更新するには、 [Resync](../../../ado/reference/ado-api/resync-method.md)メソッドを使用します。  
  
 **CacheSize**が1より大きい値に設定されている場合、ナビゲーションメソッド ([Move](../../../ado/reference/ado-api/move-method-ado.md)、 [MoveFirst、MoveLast、MoveNext、および MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)) は、レコードの取得後に削除が発生すると、削除されたレコードに移動する可能性があります。 最初のフェッチの後、削除された行からデータ値にアクセスしようとするまで、その後の削除はデータキャッシュに反映されません。 ただし、 **CacheSize**を1に設定すると、削除された行をフェッチできないため、この問題は解消されます。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [CacheSize プロパティの例 (VB)](../../../ado/reference/ado-api/cachesize-property-example-vb.md)   
 [CacheSize プロパティの例 (VC + +)](../../../ado/reference/ado-api/cachesize-property-example-vc.md)   
 [CacheSize プロパティの例 (JScript)](../../../ado/reference/ado-api/cachesize-property-example-jscript.md)
