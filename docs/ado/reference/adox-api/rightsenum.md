---
title: RightsEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RightsEnum
helpviewer_keywords:
- RightsEnum enumeration [ADOX]
ms.assetid: 55ee67c7-a583-42aa-849a-78264b4cb614
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1904a77ae104576f2a9f82fc09d8728e2ec88c11
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47760510"
---
# <a name="rightsenum"></a>RightsEnum
オブジェクトの権利またはグループまたはユーザーのアクセス許可を指定します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adRightCreate**|16384 (&AMP; H4000)|ユーザーまたはグループは、この型の新しいオブジェクトを作成するアクセス許可を持っています。|  
|**adRightDelete**|65536 (&AMP; H10000)|ユーザーまたはグループは、オブジェクトからデータを削除するアクセス許可を持っています。 などのオブジェクトの**テーブル**ユーザーがレコードからのデータ値を削除する権限。|  
|**adRightDrop**|256 (&AMP; H100)|ユーザーまたはグループは、カタログからオブジェクトを削除するアクセス許可を持っています。 たとえば、**テーブル**DROP TABLE SQL コマンドによって削除できます。|  
|**adRightExclusive**|512 (&H200)|ユーザーまたはグループは、オブジェクトを排他的にアクセスするためのアクセス許可を持っています。|  
|**adRightExecute**|536870912 (&AMP; H20000000)|ユーザーまたはグループは、オブジェクトを実行するためのアクセス許可を持っています。|  
|**adRightFull**|268435456 (&AMP; H10000000)|ユーザーまたはグループは、オブジェクトのすべてのアクセス許可を持っています。|  
|**adRightInsert**|32768 (&AMP; H8000)|ユーザーまたはグループは、オブジェクトを挿入する権限を持っています。 などのオブジェクトの**テーブル**ユーザーがテーブルにデータを挿入する権限。|  
|**adRightMaximumAllowed**|33554432 (&AMP; H2000000)|ユーザーまたはグループは、プロバイダーによって許可されるアクセス許可の最大数を持っています。 特定のアクセス許可は、プロバイダーに依存します。|  
|**adRightNone**|0|ユーザーまたはグループには、オブジェクトのアクセス許可がありません。|  
|**adRightRead**|-2147483648 (&AMP; H80000000)|ユーザーまたはグループは、オブジェクトの読み取りアクセス許可を持っています。 などのオブジェクトの[テーブル](../../../ado/reference/adox-api/table-object-adox.md)ユーザーがテーブル内のデータを読み取るアクセス許可。|  
|**adRightReadDesign**|1024 ((&AMP; A) H400)|ユーザーまたはグループは、オブジェクトのデザインを読み取るアクセス許可を持っています。|  
|**adRightReadPermissions**|131072 (&AMP; H20000)|ユーザーまたはグループは、表示しますが、カタログ内のオブジェクトの特定の権限は変更されません。|  
|**adRightReference**|8192 ((&AMP; A) H2000)|ユーザーまたはグループは、オブジェクトを参照するためのアクセス許可を持っています。|  
|**adRightUpdate**|1073741824 (&AMP; H40000000)|ユーザーまたはグループは、オブジェクトを更新するアクセス許可を持っています。 などのオブジェクトの**テーブル**ユーザーがテーブル内のデータを更新する権限。|  
|**adRightWithGrant**|4096 ((&AMP; A) H1000)|ユーザーまたはグループは、オブジェクトのアクセス許可を付与するアクセス許可を持っています。|  
|**adRightWriteDesign**|2048 ((&AMP; A) H800)|ユーザーまたはグループは、オブジェクトのデザインを変更するアクセス許可を持っています。|  
|**adRightWriteOwner**|524288 (&AMP; H80000)|ユーザーまたはグループは、オブジェクトの所有者を変更するアクセス許可を持っています。|  
|**adRightWritePermissions**|262144 (&AMP; H40000)|ユーザーまたはグループには、カタログ内のオブジェクトの特定のアクセス許可を変更できます。|  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[GetPermissions メソッド (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)|[SetPermissions メソッド (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)|
