---
title: setSendTimeAsDatetime メソッド (SQLServerDataSource) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 705a0494-b5e2-43db-940a-1b8cec550cdb
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4a5e9d17255ac790fbf2d1466555a2e2e877e13d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32843967"
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
  
  
