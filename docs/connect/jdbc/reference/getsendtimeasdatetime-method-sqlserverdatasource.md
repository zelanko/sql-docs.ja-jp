---
title: getSendTimeAsDatetime メソッド (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 02287122-5dc1-455d-987f-95fd9a69d503
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e1396ac28a7e41dbf530f7e4a251876f6c340871
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67979943"
---
# <a name="getsendtimeasdatetime-method-sqlserverdatasource"></a>getSendTimeAsDatetime メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  このメソッドは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0 で追加されました。  
  
 **sendTimeAsDatetime** 接続プロパティの設定が返されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean getSendTimeAsDatetime();  
```  
  
## <a name="return-value"></a>戻り値  
 java.sql.Time 値が [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の **datetime** 型としてサーバーに送信される場合は、**true** です。 java.sql.Time 値が [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の **time** 型としてサーバーに送信される場合は、**false** です。  
  
## <a name="remarks"></a>解説  
 **sendTimeAsDatetime** 接続プロパティの詳細については、「[接続プロパティの設定](../../../connect/jdbc/setting-the-connection-properties.md)」を参照してください。  
  
 [SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md) を使用すると、**sendTimeAsDatetime** 接続プロパティをプログラムから設定することができます。  
  
 詳細については、「[java.sql.Time の値をサーバーに送信する方法の構成](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
