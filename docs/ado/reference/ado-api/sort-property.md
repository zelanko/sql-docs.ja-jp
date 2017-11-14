---
title: "プロパティを並べ替える |Microsoft ドキュメント"
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
- Recordset15::get_Sort
- Recordset15::put_Sort
- Recordset15::PutSort
- Recordset15::GetSort
- Recordset15::Sort
helpviewer_keywords:
- DESC [ADO]
- ASC [ADO]
- Sort property [ADO]
ms.assetid: 3683ffa0-6f93-4906-9533-ef6942f24f39
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 16bba12bdcf95e8e71cab6dcb8404b7b3b1916e7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sort-property"></a>並べ替えのプロパティ
1 つまたは複数のフィールド名を示す、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)が並べ替えられて、各フィールドが昇順または降順で並べ替えられたかどうかとします。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**文字列**内のフィールドを示す値名、 **Recordset**並べ替えを行う。 それぞれの名前をコンマで区切られ、空白と、キーワードを順に必要に応じて**ASC**、フィールド、昇順の並べ替えまたは**DESC**、降順でフィールドの並べ替え。 既定では、キーワードが指定されていない場合、フィールドが昇順で並べ替えられます。  
  
## <a name="remarks"></a>解説  
 このプロパティが必要、 [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)設定するプロパティを**adUseClient**です。 指定された各フィールドに一時インデックスが作成されます、**並べ替え**プロパティ、インデックスが既に存在しない場合。  
  
 並べ替え操作が効率的なデータが物理的に並べ替えられるされませんが、インデックスによって指定された順序でアクセスされるだけです。  
  
 ときの値、**並べ替え**プロパティが空の文字列以外である、**並べ替え**プロパティの順序で指定された順序よりも優先、 **ORDER BY**句開くには使用する SQL ステートメントに含まれる、 **Recordset**です。  
  
 **Recordset**にアクセスする前に開く必要はありません、**並べ替え**プロパティは後にいつでも設定できます、**レコード セット**オブジェクトをインスタンス化します。  
  
 設定、**並べ替え**プロパティを空の文字列には行は元の順序にリセットされ、一時的なインデックスを削除します。 既存のインデックスは削除されません。  
  
 たとえば、**レコード セット**という 3 つのフィールドが含まれています*firstName*、 *[middleinitial]*と*lastName*です。 設定、**並べ替え**プロパティを文字列に"`lastName DESC, firstName ASC`"、順序は、 **Recordset**昇順の最初の名前で、次の姓を降順にします。 ミドル ネームのイニシャルは無視されます。  
  
 フィールドをするという名前の"ASC"または"DESC"キーワードとそれらの名前が競合するため**ASC**と**DESC**です。 使用して、競合する名前を持つフィールドの別名を作成することができます、 **AS**を返すクエリ内のキーワード、 **Recordset**です。  
  
## <a name="applies-to"></a>適用対象  
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [並べ替えプロパティの例 (VB)](../../../ado/reference/ado-api/sort-property-example-vb.md)   
 [並べ替えプロパティの例 (vc++)](../../../ado/reference/ado-api/sort-property-example-vc.md)   
 [動的プロパティ (ADO) を最適化します。](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)   
 [SortColumn プロパティ (RDS)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)   
 [SortDirection プロパティ (RDS)](../../../ado/reference/rds-api/sortdirection-property-rds.md)

