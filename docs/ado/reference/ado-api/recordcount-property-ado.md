---
title: RecordCount プロパティ (ADO) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::RecordCount
- Recordset15::GetRecordCount
- Recordset15::get_RecordCount
helpviewer_keywords:
- RecordCount property [ADO]
ms.assetid: 834f0121-394a-44d4-ad7d-999b43a6fe63
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 7c2a7900d47b2e80227e470219fd7a7566dc41e4
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="recordcount-property-ado"></a>RecordCount プロパティ (ADO)

内のレコードの数を示す、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。
  
## <a name="return-value"></a>戻り値

返します、**長い**内のレコードの数を示す値、 **Recordset**です。
  
## <a name="remarks"></a>解説

使用して、 **RecordCount**でどれくらいのレコードを検索するプロパティには、 **Recordset**オブジェクト。 プロパティは、ADO レコードの数を判断できない場合や、プロバイダーまたはカーソルの種類がサポートされていない場合に-1 を返します**RecordCount**です。 読み取り、 **RecordCount**プロパティに、閉じられた**Recordset**エラーが発生します。

#### <a name="bookmarks-or-approximate-positioning"></a>ブックマークまたは概数の配置

場合、レコード セット オブジェクト*は*いずれかのブックマークをサポートまたは概数配置、このプロパティを返しますレコードの正確な数のレコード セット。 このプロパティは、かどうか、レコード セットが完全に読み込まれたに関係なく正確な数を返します。

これに対して、レコード セット オブジェクトは*いない*ブックマークまたはおおよその位置のいずれかをサポートして、このプロパティにアクセスすると、リソースの大量消費する可能性があります。 すべてのレコードが取得する必要があります、カウントを正確な RecordCount 値を返すために、ドレインが発生します。

- **adBookmark**ブックマークに関連します。
- **adApproxPosition**おおよその位置に関連します。

> [!NOTE]
> SQLOLEDB プロバイダーがサーバー側カーソルが使用される場合でも、返されるすべてのレコードをフェッチ ADO 2.8 およびそれ以前のバージョン、 **True**両方の**サポート (adApproxPosition)**と**サポート (adBookmark)**です。
  
カーソルの種類、 **Recordset**オブジェクトは、レコードの数を決定できるかどうかに影響します。 **RecordCount**プロパティは、順方向専用カーソル以外の場合は、静的な実際の数またはキーセット カーソル; し、-1 の場合は-1 または動的カーソルの場合は、データ ソースによって実際の数を返します。
  
## <a name="applies-to"></a>適用対象

[Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照

[フィルターおよび RecordCount のプロパティの例 (VB)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vb.md)   
[フィルターおよび RecordCount のプロパティの例 (vc++)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vc.md)   
[AbsolutePosition プロパティ (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)   
[PageCount プロパティ (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)
