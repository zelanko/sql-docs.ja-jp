---
title: NULL の取り扱い (SQLXML 4.0) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- updg:nullvalue attribute
- updategrams [SQLXML], null values
- nullvalue attribute
- null values [SQLXML]
ms.assetid: 5e11eebb-d94e-4ce6-a6d0-870225706bc1
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 67386e9eb951135f0a7dbd70fb02774dde82d0d1
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43101895"
---
# <a name="null-handling-sqlxml-40"></a>NULL の取り扱い (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  XML 構文では、NULL は "存在しない" ことを表します。 たとえば、属性または要素値が NULL の場合、その属性または要素は XML ドキュメントに存在しません。[!INCLUDE[msCoName](../../../includes/msconame-md.md)] 、SQLXML、 **updg:nullvalue**属性を使用して、要素または属性値に NULL を指定します。  
  
 たとえば、次のアップデート グラムにより、**タイトル**値へのアクセスを**ContactID** 64 が null の場合、し、更新、**タイトル**値を"Mr." この連絡先にします。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync updg:nullvalue="IsNULL"  >  
    <updg:before>  
       <Person.Contact ContactID="64" Title="IsNULL" />  
    </updg:before>  
    <updg:after>  
       <Person.Contact ContactID="64" Title="Mr." />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 パラメーターをアップデートグラムに渡すときには、パラメーター値として NULL を指定できます。 これは、指定することで、 **nullvalue**属性、  **\<updg:header >** ブロックします。 例については、次を参照してください。[アップデート グラムにパラメーターを渡す&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/passing-parameters-to-updategrams-sqlxml-4-0.md)します。  
  
## <a name="see-also"></a>参照  
 [アップデート グラムのセキュリティに関する考慮事項&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
