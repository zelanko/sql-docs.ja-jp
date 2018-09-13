---
title: getServerName メソッド (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDataSource.getServerName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3004ed22-5d69-4dd0-8761-d39f0b7dde13
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8e709a5adc084c316733333a9012beee3fd77ef4
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2018
ms.locfileid: "42787026"
---
# <a name="getservername-method-sqlserverdatasource"></a>getServerName メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスの名前が返されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getServerName()  
```  
  
## <a name="return-value"></a>戻り値  
 サーバー名を含む**文字列**です。値が設定されていない場合は null です。  
  
## <a name="remarks"></a>Remarks  
 サーバー名は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を実行している、対象のコンピューターのホスト名です。 getServerName プロパティが設定されていない場合、getServerName は既定値の null が返されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
