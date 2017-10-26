---
title: "setSendTimeAsDatetime メソッド (SQLServerDataSource) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 705a0494-b5e2-43db-940a-1b8cec550cdb
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f6a576e4cb3ef155092a1244bbf9e7c2fcaaadd5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="setsendtimeasdatetime-method-sqlserverdatasource"></a>setSendTimeAsDatetime メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  このメソッドで追加された[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]JDBC Driver 3.0 です。  
  
 設定を変更、 **sendTimeAsDatetime**接続プロパティです。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setSendTimeAsDatetime(boolean sendTimeAsDateTime)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sendTimeAsDateTime*  
  
 ブール値です。 True の場合、java.sql.Time 値としてサーバーに送信するを原因[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **datetime**型です。 False の場合、java.sql.Time 値としてサーバーに送信するを原因[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]**時間**型です。  
  
## <a name="remarks"></a>解説  
 [SQLServerDataSource.getSendTimeAsDatetime](../../../connect/jdbc/reference/getsendtimeasdatetime-method-sqlserverdatasource.md)の設定値を返します、 **sendTimeAsDatetime**接続プロパティです。  
  
 詳細については、 **sendTimeAsDatetime**接続プロパティを参照してください[接続プロパティの設定](../../../connect/jdbc/setting-the-connection-properties.md)です。  
  
 詳細については、次を参照してください。[を構成する方法の java.sql.Time 値は、サーバーに送信される](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

