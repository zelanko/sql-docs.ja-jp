---
title: DataMember プロパティ |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::DataMember
helpviewer_keywords:
- DataMember property
ms.assetid: 2c8fb09e-10ad-49b5-ab41-2603771780d9
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9de69478469a6bd177d12beab96e199b4720f3f5
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66695485"
---
# <a name="datamember-property"></a>DataMember プロパティ
取得するデータ メンバーの名前を示します、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)によって参照される、 [DataSource](../../../ado/reference/ado-api/datasource-property-ado.md)プロパティ。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 設定または取得を**文字列**値。 名前は大文字小文字を区別します。  
  
## <a name="remarks"></a>コメント  
 このプロパティは、データ環境でのデータ バインド コントロールの作成に使用されます。 データ環境の保持を含むデータ (データ ソース) のコレクションの名前付きのオブジェクト (データ メンバー) として表される、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。  
  
 **DataMember**と**DataSource**プロパティを一緒に使用する必要があります。  
  
 **DataMember**プロパティで指定されたどのオブジェクトを決定する、 **DataSource**プロパティとして表されます、**レコード セット**オブジェクト。 **Recordset**オブジェクトは、このプロパティを設定する前に閉じる必要があります。 場合にエラーが生成されます、 **DataMember**する前にプロパティが設定されていない、 **DataSource**プロパティ、または、 **DataMember**で指定されたオブジェクトで名前が認識されない、**DataSource**プロパティ。  
  
## <a name="usage"></a>使用方法  
  
```  
Dim rs as New ADODB.Recordset  
rs.DataMember = "Command"     'Name of the rowset to bind to  
Set rs.DataSource = myDE      'Name of the object containing an IRowset  
```  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [DataSource プロパティ (ADO)](../../../ado/reference/ado-api/datasource-property-ado.md)
