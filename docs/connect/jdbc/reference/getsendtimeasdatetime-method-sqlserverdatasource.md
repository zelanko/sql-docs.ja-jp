---
title: getSendTimeAsDatetime メソッド (SQLServerDataSource) |Microsoft Docs
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
manager: jroth
ms.openlocfilehash: 36cdeda1cdad226c00449d118f154fd555e7246d
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66792088"
---
# <a name="getsendtimeasdatetime-method-sqlserverdatasource"></a>getSendTimeAsDatetime メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  このメソッドは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0 で追加されました。  
  
 設定を返します、**で sendTimeAsDatetime**接続プロパティです。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean getSendTimeAsDatetime();  
```  
  
## <a name="return-value"></a>戻り値  
 **true** java.sql.Time 値としてサーバーに送信するかどうか、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **datetime**型。 **false** java.sql.Time 値としてサーバーに送信するかどうか、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **時間**型。  
  
## <a name="remarks"></a>Remarks  
 参照してください[接続プロパティの設定](../../../connect/jdbc/setting-the-connection-properties.md)の詳細については、**で sendTimeAsDatetime**接続プロパティです。  
  
 [SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md) を使用すると、**sendTimeAsDatetime** 接続プロパティをプログラムから設定することができます。  
  
 詳細については、次を参照してください。[を構成する方法の java.sql.Time 値は、サーバーに送信される](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md)します。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
