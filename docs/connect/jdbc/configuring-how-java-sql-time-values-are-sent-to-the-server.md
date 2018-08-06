---
title: java.sql.Time の値をサーバーに送信する方法の構成 | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 07eb00dd-621a-46f9-a5a5-8cab4d6058b5
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6a52f214b0383a8cabe04bd8c10b7c9ecdef2b21
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2018
ms.locfileid: "39278723"
---
# <a name="configuring-how-javasqltime-values-are-sent-to-the-server"></a>java.sql.Time の値をサーバーに送信する方法の構成
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  パラメーターを設定するために java.sql.Time オブジェクトまたは java.sql.Types.TIME JDBC 型を使用する場合、サーバーに対して java.sql.Time 値をどのように送信するか ([!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] の **time** 型として送信するか、**datetime** 型として送信するか) を構成することができます。  
  
 次のいずれかのメソッドを使用するケースが、このシナリオに該当します。  
  
-   [SQLServerCallableStatement.registerOutParameter(int, int)](../../connect/jdbc/reference/registeroutparameter-method-int-int.md)  
  
-   [SQLServerCallableStatement.registerOutParameter(int, int, int)](../../connect/jdbc/reference/registeroutparameter-method-int-int-int.md)  
  
-   [SQLServerCallableStatement.setTime](../../connect/jdbc/reference/settime-method-sqlservercallablestatement.md)  
  
-   [SQLServerPreparedStatement.setTime](../../connect/jdbc/reference/settime-method-sqlserverpreparedstatement.md)  
  
-   [SQLServerCallableStatement.setObject](../../connect/jdbc/reference/setobject-method-sqlservercallablestatement.md)  
  
-   [SQLServerPreparedStatement.setObject](../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)  
  
 java.sql.Time 値の送信方法を構成するには **sendTimeAsDatetime** 接続プロパティを使用します。 詳細については、「[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)」を参照してください。  
  
 **sendTimeAsDatetime** 接続プロパティの値は、[SQLServerDataSource.setSendTimeAsDatetime](../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md) を使用してプログラムから変更できます。  
  
 バージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]よりも前[!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)]をサポートしていない、**時間**通常 java.sql.Time を使用してアプリケーション java.sql.Time を保存するように、データ型の値として**datetime**または**smalldatetime** [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型。  
  
 使用する場合、 **datetime**と**smalldatetime** [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] java.sql.Time 値を使用する場合のデータ型に設定する必要がある、**で sendTimeAsDatetime**接続プロパティを**true**します。 使用する場合、**時間**[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ときに、データ型 java.sql.Time 値を使用する必要がありますを設定する、**で sendTimeAsDatetime**接続プロパティを**false**.  
  
 日付と時刻の両方を格納できるパラメーターに java.sql.Time 値を送信した場合、java.sql.Time 値の送信方法によって、既定の日付は異なる点に注意してください。**datetime** 値として送信された場合は 1/1/1970 に、**time** 値として送信された場合は 1/1/1900 になります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] にデータを送信する際のデータ変換の詳細については、「[日時データの使用](http://go.microsoft.com/fwlink/?LinkID=145211)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] JDBC Driver 3.0 で**で sendTimeAsDatetime**が既定では true。 今後のリリースでは、**sendTimeAsDatetime** 接続プロパティの既定値が false になる予定です。  
  
 アプリケーションの動作が **sendTimeAsDatetime** 接続プロパティの既定値に左右されないようにするための対策としては、次のような方法があります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] の **time** データ型を使用する場合は java.sql.Time を使用する。  
  
-   使用する場合は java.sql.Timestamp を使用して、 **datetime**、 **smalldatetime**、および**datetime2** [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型。  
  
SendTimeAsDatetime は、暗号化された列が時間から datetime への変換をサポートしない、暗号化された列の場合は false である必要があります。 Microsoft JDBC Driver 6.0 for SQL Server 以降、SQLServerConnection クラスで sendTimeAsDatetime プロパティの値の設定/取得する次の 2 つのメソッドです。

```java
  public boolean getSendTimeAsDatetime()
  public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)
```
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーのデータ型について](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
