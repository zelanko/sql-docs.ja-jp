---
title: "サーバーに java.sql.Time 値を送信する方法の構成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07eb00dd-621a-46f9-a5a5-8cab4d6058b5
caps.latest.revision: "18"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8492c3271950abbf7c99a571c2bfc9a68d35ed76
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="configuring-how-javasqltime-values-are-sent-to-the-server"></a>java.sql.Time の値をサーバーに送信する方法の構成
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  パラメーターを設定する java.sql.Time オブジェクトまたは java.sql.Types.TIME JDBC の型を使用する場合は、java.sql.Time 値をサーバーに送信する方法を構成することができます。いずれかとして、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **時間**型か、または、 **datetime**型です。  
  
 次のいずれかのメソッドを使用するケースが、このシナリオに該当します。  
  
-   [SQLServerCallableStatement.registerOutParameter (int, int)](../../connect/jdbc/reference/registeroutparameter-method-int-int.md)  
  
-   [SQLServerCallableStatement.registerOutParameter (int、int, int)](../../connect/jdbc/reference/registeroutparameter-method-int-int-int.md)  
  
-   [SQLServerCallableStatement.setTime](../../connect/jdbc/reference/settime-method-sqlservercallablestatement.md)  
  
-   [SQLServerPreparedStatement.setTime](../../connect/jdbc/reference/settime-method-sqlserverpreparedstatement.md)  
  
-   [SQLServerCallableStatement.setObject](../../connect/jdbc/reference/setobject-method-sqlservercallablestatement.md)  
  
-   [SQLServerPreparedStatement.setObject](../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)  
  
 Java.sql.Time 値を使用して送信する方法を構成することができます、 **sendTimeAsDatetime**接続プロパティです。 詳細については、次を参照してください。[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)です。  
  
 プログラムによっての値を変更することができます、 **sendTimeAsDatetime**接続プロパティに[SQLServerDataSource.setSendTimeAsDatetime](../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md)です。  
  
 バージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]よりも前[!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)]サポートしていない、**時間**通常 java.sql.Time を使用してアプリケーションを java.sql.Time を格納するように、データ型の値として**datetime**または**smalldatetime** [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型。  
  
 使用する場合、 **datetime**と**smalldatetime** [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] java.sql.Time 値を使用する場合のデータ型を設定する必要あります、 **sendTimeAsDatetime**接続プロパティを**true**です。 使用する場合、**時間**[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型の場合に java.sql.Time 値を使用する必要があります設定、 **sendTimeAsDatetime**接続プロパティを**false**.  
  
 格納した場合のデータ型をパラメーターに java.sql.Time 値を送信することができます、日付は、既定の日付として java.sql.Time 値を送信するかどうかに応じて異なることに注意してください、 **datetime** (1970 年 1/1/) または**時間**(1900 年 1 月 1 日) の値。 データを送信する際のデータ変換の詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]を参照してください[を使用して日付と時刻のデータ](http://go.microsoft.com/fwlink/?LinkID=145211)です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] JDBC Driver 3.0 **sendTimeAsDatetime**が既定では true です。 将来のリリースで、 **sendTimeAsDatetime**既定では、接続プロパティを false に設定することがあります。  
  
 アプリケーションが引き続きの既定値に関係なく期待どおりに動作できるように、 **sendTimeAsDatetime**接続プロパティをすることができます。  
  
-   使用する場合、java.sql.Time を使用して、**時間**[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型。  
  
-   使用する場合は java.sql.Timestamp を使用して、 **datetime**、 **smalldatetime**、および**datetime2** [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型。  
  
暗号化された列は時刻から datetime への変換をサポートしていないために、その sendTimeAsDatetime が暗号化された列の場合は false にする必要がありますに注意してください。 Microsoft JDBC Driver 6.0 for SQL Server から始まり、SQLServerConnection クラスが、sendTimeAsDatetime プロパティの値を設定/取得する次の 2 つの方法です。

```
  public boolean getSendTimeAsDatetime()
  public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)
```
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーのデータ型について](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
