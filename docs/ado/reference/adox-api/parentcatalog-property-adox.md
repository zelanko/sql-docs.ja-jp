---
title: "ParentCatalog プロパティ (ADOX) |Microsoft ドキュメント"
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
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c255beddbc240f30f51642a0e8fe4fd785cf88bb
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="parentcatalog-property-adox"></a>ParentCatalog プロパティ (ADOX)
プロバイダー固有のプロパティへのアクセスを提供するテーブル、ユーザー、または列のオブジェクトの親のカタログを指定します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 設定を返します、[カタログ](../../../ado/reference/adox-api/catalog-object-adox.md)オブジェクト。 設定**ParentCatalog**開いた**カタログ**テーブルまたは列を追加する前に、プロバイダー固有のプロパティにアクセスできるように、**カタログ**コレクション。  
  
## <a name="remarks"></a>解説  
 一部のデータ プロバイダーの作成時のみ書き込まれるプロバイダー固有のプロパティ値を許可する: つまり、ときにテーブルまたは列が追加されますをその**カタログ**コレクション。 これらのオブジェクトを追加する前にこれらのプロパティにアクセスする、**カタログ**を指定して、**カタログ**で、 **ParentCatalog**プロパティ最初。  
  
 テーブルまたは列は別に追加するときにエラーが発生した**カタログ**よりも、 **ParentCatalog**です。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Column オブジェクト (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)|[Table オブジェクト (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|  
|[User オブジェクト (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)||  
  
## <a name="see-also"></a>参照  
 [ParentCatalog プロパティの例 (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)
