---
description: ParentCatalog プロパティ (ADOX)
title: ParentCatalog プロパティ (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _User::get_ParentCatalog
- _Column::ParentCatalog
- _Table::put_ParentCatalog
- _Group::put_ParentCatalog
- _Column::get_ParentCatalog
- _Table::PutParentCatalog
- _Group::putref_ParentCatalog
- _Group::ParentCatalog
- _Column::PutParentCatalog
- _Column::put_ParentCatalog
- _Group::get_ParentCatalog
- _User::put_ParentCatalog
- _User::putref_ParentCatalog
- _Table::get_ParentCatalog
- _Group::PutParentCatalog
- _Table::ParentCatalog
- _Column::GetParentCatalog
- _Table::PutRefParentCatalog
- _User::GetParentCatalog
- _Table::GetParentCatalog
- _Table::putref_ParentCatalog
- _User::PutParentCatalog
- _User::ParentCatalog
- _User::PutRefParentCatalog
- _Group::GetParentCatalog
- _Group::PutRefParentCatalog
helpviewer_keywords:
- ParentCatalog property [ADOX]
ms.assetid: a0bb2ed8-d4cb-4f92-8de7-769bbe0e6273
author: rothja
ms.author: jroth
ms.openlocfilehash: 93d15cdac3d8f7a47c74a783d176d806271f68a3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439724"
---
# <a name="parentcatalog-property-adox"></a>ParentCatalog プロパティ (ADOX)
プロバイダー固有のプロパティへのアクセスを提供する、テーブル、ユーザー、または列オブジェクトの親カタログを指定します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 [カタログ](../../../ado/reference/adox-api/catalog-object-adox.md)オブジェクトを設定して返します。 **ParentCatalog**を開いている**カタログ**に設定すると、テーブルまたは列を**カタログ**コレクションに追加する前に、プロバイダー固有のプロパティにアクセスできます。  
  
## <a name="remarks"></a>解説  
 一部のデータプロバイダーでは、プロバイダー固有のプロパティ値を作成時にのみ書き込むことができます。つまり、テーブルまたは列がその **カタログ** コレクションに追加されたときです。 これらのオブジェクトを**カタログ**に追加する前にこれらのプロパティにアクセスするには、まず、 **ParentCatalog**プロパティで**カタログ**を指定します。  
  
 テーブルまたは列が**ParentCatalog**とは別の**カタログ**に追加されると、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  

:::row:::
    :::column:::
        [Column オブジェクト (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)  
    :::column-end:::
    :::column:::
        [Table オブジェクト (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)  
    :::column-end:::
    :::column:::
        [User オブジェクト (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>参照  
 [ParentCatalog プロパティの例 (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)
