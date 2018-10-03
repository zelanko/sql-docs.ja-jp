---
title: ISQLServerStatement インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7f83b514-6e76-4f37-baf3-a10db2010e7c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 41441e49140f914fa5d14562d774a2fccea2696f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47811640"
---
# <a name="isqlserverstatement-interface"></a>ISQLServerStatement インターフェイス
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  JDBC ステートメント機能の基本的な実装を表します。 このインターフェイスは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0 で追加されました。  
  
 **パッケージ:** com.microsoft.sqlserver.jdbc  
  
 **継承:** java.sql.Statement  
  
## <a name="syntax"></a>構文  
  
```  
  
public interface ISQLServerStatement  
```  
  
## <a name="remarks"></a>Remarks  
 このインターフェイスによって実装されます[SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)します。  
  
 このインターフェイスでは、次の [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 固有のメソッドが公開されます。  
  
|方法|詳細については、「|  
|------------|-------------------------------|  
|public String getResponseBuffering|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md)|  
|public void setResponseBuffering|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)|  
  
## <a name="see-also"></a>参照  
 [JDBC Driver API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
