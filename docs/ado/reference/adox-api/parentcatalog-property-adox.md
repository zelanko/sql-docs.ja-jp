---
title: "ParentCatalog プロパティ (ADOX) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
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
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f5229c37299494ca2b3b31e3ca3e0d091c93d96a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

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
|[ユーザー オブジェクト (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)||  
  
## <a name="see-also"></a>参照  
 [ParentCatalog プロパティの例 (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)
