---
title: setClientInfo メソッド (java.util.Properties) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b2a8ec0b-40a2-44d1-90d9-a810d4132e56
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a332f42c8193c851a33036af214ac31366986023
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "67974741"
---
# <a name="setclientinfo-method-javautilproperties"></a>setClientInfo (java.util.Properties) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  接続のクライアント情報のプロパティの値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setClientInfo (java.util.Properties properties)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *properties*  
  
 設定するクライアント情報のプロパティの一覧を含む Properties オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setClientInfo メソッドは、javax.sql.Connection インターフェイスの setClientInfo メソッドによって指定されます。  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] ではクライアント情報のプロパティをサポートしていません。 *properties* 入力パラメーターが空のプロパティ セットを参照しない場合、このメソッドは警告を生成します。 つまり、このメソッドはアプリケーションが設定しようとするプロパティへの警告を生成します。 アプリケーションは、[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) クラスの [getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverconnection.md) メソッドを使用して各警告を取得する必要があります。  
  
## <a name="see-also"></a>参照  
 [setClientInfo メソッド &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/setclientinfo-method-sqlserverconnection.md)   
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
