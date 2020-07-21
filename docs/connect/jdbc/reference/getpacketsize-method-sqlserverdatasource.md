---
title: getPacketSize メソッド (SQLServerDataSource) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: be0d32d8dbb8dea35d354426c75c5cdd1af3f3f9
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80904676"
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
  
## <a name="remarks"></a>解説  
 packetSize プロパティが設定されていない場合、getPacketSize メソッドは既定値の 8000 が返されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
