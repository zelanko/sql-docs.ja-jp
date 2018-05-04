---
title: Find メソッド (ADO) |Microsoft ドキュメント
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
- Recordset15::raw_Find
- Recordset15::Find
helpviewer_keywords:
- Find method [ADO]
ms.assetid: 55c9810a-d8ca-46c2-a9dc-80e7ee7aa188
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 953398f5ed01cc3e0f7c0da1fee769d5e64209af
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="find-method-ado"></a>Find メソッド (ADO)
検索、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)を指定した条件を満たす行にします。 必要に応じて、検索、開始行、および開始行からのオフセットの方向を指定することがあります。 検出されたレコード; で現在の行位置を設定、条件が満たされる場合それ以外の場合、位置に設定されている (先頭または末尾) の**Recordset**です。  
  
## <a name="syntax"></a>構文  
  
```  
  
Find (Criteria, SkipRows, SearchDirection, Start)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *条件*  
 A**文字列**検索に使用するには、列名、比較演算子および値を指定するステートメントを含む値です。  
  
 *SkipRows*  
 省略可能な*します。* A**長い**値、既定値が、現在の行から行オフセットを指定する 0 または*開始*ブックマーク、検索を開始します。 既定では、検索は、現在の行で開始されます。  
  
 *SearchDirection*  
 省略可能な*します。* A [SearchDirectionEnum](../../../ado/reference/ado-api/searchdirectionenum.md)検索の方向で使用可能な次の行または現在の行に検索を開始するかどうかを指定する値。 検索が失敗したが、最後の停止、**レコード セット**値が場合**adSearchForward**です。 開始位置を検索が失敗した、 **Recordset**値が場合**adSearchBackward**です。  
  
 *コントロール パネルの  ◆セグ : 文が分断されているため、訳の位置が入れ替わっています◇*  
 省略可。 A**バリアント**ブックマーク、検索の開始位置として機能します。  
  
## <a name="remarks"></a>解説  
 単一の列名のみを指定することがあります*条件*です。 このメソッドは、複数列の検索をサポートしていません。  
  
 比較演算子で*条件*可能性があります"**>**「(より大きい)、」**\<**"(より小さい)、「=」(等しい)、"> ="(より大きいまたは等しい)"< ="(以下)、"<>"(等しくない)、または「のように」(パターン一致)。  
  
 値*条件*文字列、浮動小数点数、または日付にすることがあります。 文字列の値が単一引用符または「#」) で区切られた (たとえば、"状態 = 'WA'"または"の状態 = WA #") です。 日付の値は「#」(シャープ記号) 記号で区切られます (たとえば、"start_date > #7 月 22 日/97 #") です。 これらの値は、時間、分、および秒を示すタイムスタンプを含めることができますが、ミリ秒を含めることはできませんまたはエラーが発生します。  
  
 比較演算子が"like"にある場合は、文字列値はアスタリスク (*) を 1 つ以上の出現箇所を任意の文字または部分文字列の検索を含めることがあります。 たとえば、"のような状態にして\*'"メイン州と Massachusetts に一致します。 また、値内に含まれる部分文字列を検索するのに先頭および末尾のアスタリスクを使用することができます。 たとえば、"のような状態 '\*として\*'"アラスカ、アーカンソー、Massachusetts に一致します。  
  
 アスタリスクできます使用条件の文字列の末尾または先頭と条件の文字列の末尾の両方で上記のようにします。 先頭のワイルドカードとしてアスタリスクを使用することはできません ('* str')、または埋め込みワイルドカード ('s として\*r')。 これにより、エラーが発生します。  
  
> [!NOTE]
>  現在の行位置を呼び出す前に設定されていない場合、エラーが発生**検索**です。 など、行の位置を設定するメソッド[MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)を呼び出す前に呼び出す必要があります**検索**です。  
  
> [!NOTE]
>  呼び出す場合は、**検索**、レコード セットと、レコード セット内の現在位置でメソッドが、最後のレコードまたはファイルの末尾 (EOF) には、何も検索されません。 呼び出す必要があります、 **MoveFirst**レコード セットの先頭に現在の位置/カーソルを設定します。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [メソッドの例 (VB) を検索します。](../../../ado/reference/ado-api/find-method-example-vb.md)   
 [Index プロパティ](../../../ado/reference/ado-api/index-property.md)   
 [動的プロパティ (ADO) を最適化します。](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)   
 [Seek メソッド](../../../ado/reference/ado-api/seek-method.md)
