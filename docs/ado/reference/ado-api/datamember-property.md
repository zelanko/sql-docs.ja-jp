---
title: "DataMember プロパティ |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: Recordset20::DataMember
helpviewer_keywords: DataMember property
ms.assetid: 2c8fb09e-10ad-49b5-ab41-2603771780d9
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cdb6c6dbb5d7bb7c5c10a968cffe759edb9309f6
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="datamember-property"></a>DataMember プロパティ
取得されるデータ メンバーの名前を示す、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)によって参照されている、[データソース](../../../ado/reference/ado-api/datasource-property-ado.md)プロパティです。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**文字列**値。 名前は、大文字と小文字が区別されません。  
  
## <a name="remarks"></a>解説  
 このプロパティは、データ環境とデータ バインド コントロールを作成する使用されます。 として表されるオブジェクト (データ メンバー) をという名前を含むデータ (データ ソース) のコレクションを管理、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。  
  
 **DataMember**と**データソース**プロパティを同時に使用する必要があります。  
  
 **DataMember**プロパティで指定されたどのオブジェクトを決定する、**データソース**プロパティとして表されます、 **Recordset**オブジェクト。 **Recordset**オブジェクトは、このプロパティを設定する前に閉じる必要があります。 場合、エラーが生成、 **DataMember**する前にプロパティが設定されていない、**データソース**プロパティ、または、 **DataMember**名がで指定されたオブジェクトによって認識されていません、**データソース**プロパティです。  
  
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
