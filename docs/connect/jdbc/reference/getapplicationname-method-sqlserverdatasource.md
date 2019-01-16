---
title: getApplicationName メソッド (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getApplicationName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f71e501c-ccd7-4a1e-b6ea-4d47a81c18c6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a2eefa7cc5c2c46f93d1c9bc1230143fe74236fb
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2018
ms.locfileid: "53207702"
---
# <a name="getapplicationname-method-sqlserverdatasource"></a>getApplicationName メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  アプリケーション名を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getApplicationName()  
```  
  
## <a name="return-value"></a>戻り値  
 アプリケーション名を含む**文字列**です。値が設定されていない場合は、"[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]" です。  
  
## <a name="remarks"></a>Remarks  
 アプリケーション名は、個別のアプリケーションを識別するために、さまざまな [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] プロファイリング ツールおよびロギング ツールで使用されます。 アプリケーション名を設定しない場合は、getApplicationName メソッドによって非ローカライズ文字列 "[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]" が返されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
