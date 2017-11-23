---
title: "RightsEnum |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: RightsEnum
helpviewer_keywords: RightsEnum enumeration [ADOX]
ms.assetid: 55ee67c7-a583-42aa-849a-78264b4cb614
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0ff15518703e8e8ec2d2c3ee67df691abb1974ac
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="rightsenum"></a>RightsEnum
オブジェクトの権限またはグループまたはユーザーのアクセス許可を指定します。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adRightCreate**|16384 (& H4000)|ユーザーまたはグループは、この型の新しいオブジェクトを作成する権限を持っています。|  
|**adRightDelete**|65536 (& H10000)|ユーザーまたはグループは、オブジェクトからデータを削除するアクセス許可を持っています。 などのオブジェクト**テーブル**ユーザーがレコードからのデータ値を削除する権限を持っています。|  
|**adRightDrop**|256 (& H100)|ユーザーまたはグループは、カタログからオブジェクトを削除するアクセス許可を持っています。 たとえば、**テーブル**DROP TABLE SQL コマンドで削除できます。|  
|**adRightExclusive**|512 (& H200)|ユーザーまたはグループは、オブジェクトを排他的にアクセスする権限を持っています。|  
|**adRightExecute**|536870912 (& H20000000)|ユーザーまたはグループは、オブジェクトを実行するアクセス許可を持っています。|  
|**adRightFull**|268435456 (& H10000000)|ユーザーまたはグループは、オブジェクトのすべてのアクセス許可を持っています。|  
|**adRightInsert**|32768 (& H8000)|ユーザーまたはグループは、オブジェクトを挿入する権限を持っています。 などのオブジェクト**テーブル**ユーザーがテーブルにデータを挿入する権限を持っています。|  
|**adRightMaximumAllowed**|33554432 (& H2000000)|ユーザーまたはグループは、プロバイダーによって許可されるアクセス許可の最大数を持っています。 特定のアクセス許可は、プロバイダーによって異なります。|  
|**adRightNone**|0|ユーザーまたはグループには、オブジェクトのアクセス許可がありません。|  
|**adRightRead**|-2147483648 (& H80000000)|ユーザーまたはグループは、オブジェクトの読み取りアクセス許可を持っています。 などのオブジェクト[テーブル](../../../ado/reference/adox-api/table-object-adox.md)ユーザーがテーブル内のデータの読み取りアクセス許可を持っています。|  
|**adRightReadDesign**|1024 ((& A) H400)|ユーザーまたはグループは、オブジェクトのデザインの読み取りアクセス許可を持っています。|  
|**adRightReadPermissions**|131, 072 (& H20000)|ユーザーまたはグループ表示できますが、変更、カタログ内のオブジェクトの特定のアクセスを許可します。|  
|**adRightReference**|8192 ((& A) H2000)|ユーザーまたはグループは、オブジェクトを参照するアクセス許可を持っています。|  
|**adRightUpdate**|1073741824 (& H40000000)|ユーザーまたはグループは、オブジェクトを更新するアクセス許可を持っています。 などのオブジェクト**テーブル**ユーザーがテーブル内のデータを更新するアクセス許可を持っています。|  
|**adRightWithGrant**|4096 ((& A) H1000)|ユーザーまたはグループは、オブジェクトに対する権限を許可する権限を持っています。|  
|**adRightWriteDesign**|2048 ((& A) H800)|ユーザーまたはグループは、オブジェクトのデザインを変更する権限を持っています。|  
|**adRightWriteOwner**|524288 (& H80000)|ユーザーまたはグループは、オブジェクトの所有者を変更する権限を持っています。|  
|**adRightWritePermissions**|262144 (& H40000)|ユーザーまたはグループは、カタログ内のオブジェクトの特定のアクセス許可を変更できます。|  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[GetPermissions メソッド (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)|[SetPermissions メソッド (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)|
