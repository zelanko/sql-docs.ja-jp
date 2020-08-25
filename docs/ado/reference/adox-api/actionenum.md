---
description: ActionEnum
title: ActionEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ActionEnum
helpviewer_keywords:
- ActionEnum enumeration [ADOX]
ms.assetid: f948febd-c885-4621-823b-421e116fec4e
author: rothja
ms.author: jroth
ms.openlocfilehash: 2c9032dfdb3394e582541f60afce7b930751a5c0
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777781"
---
# <a name="actionenum"></a>ActionEnum
[SetPermissions](./setpermissions-method-adox.md)が呼び出されたときに実行されるアクションの種類を指定します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adAccessDeny**|3|グループまたはユーザーは、指定されたアクセス許可を拒否されます。|  
|**adAccessGrant**|1|グループまたはユーザーには、少なくとも要求されたアクセス許可が付与されます。|  
|**adAccessRevoke**|4|グループまたはユーザーの明示的なアクセス権はすべて取り消されます。|  
|**adAccessSet**|2|グループまたはユーザーには、要求されたアクセス許可だけが付与されます。|