---
title: getPacketSize メソッド (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getPacketSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b2e9f01a-2e51-47e5-90bf-43c62d1be74d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7790bc9eabb5127e36faddc02bb477c91ba72ac6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47838980"
---
# <a name="getpacketsize-method-sqlserverdatasource"></a>getPacketSize メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] との通信に使用される現在のネットワーク パケット サイズを返します (バイト数で指定します)。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getPacketSize()  
```  
  
## <a name="return-value"></a>戻り値  
 現在のネットワーク パケット サイズを含む **int** 値です。  
  
## <a name="remarks"></a>Remarks  
 packetSize プロパティが設定されていない場合、getPacketSize メソッドは既定値の 8000 が返されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
