---
title: getApplicationName メソッド (SQLServerDataSource) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLServerDataSource.getApplicationName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f71e501c-ccd7-4a1e-b6ea-4d47a81c18c6
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 12b6e13acc5e88f223298a0eb4c5d13aba602f43
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getapplicationname-method-sqlserverdatasource"></a>getApplicationName メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  アプリケーション名を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getApplicationName()  
```  
  
## <a name="return-value"></a>戻り値  
 A**文字列**を含む、アプリケーション名、または"[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]"値が設定されていない場合。  
  
## <a name="remarks"></a>解説  
 アプリケーション名を特定のアプリケーションで各種の識別に使用[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]プロファイリング ツールおよびロギング ツールです。 GetApplicationName メソッドがローカライズされていない文字列を返します、アプリケーション名が設定されていない場合は、"[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]"です。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
