---
title: getTrustStore メソッド (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- getTrustStore Method (SQLServerDataSource)
apilocation:
- getTrustStore Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 8f5850e4-8627-49a8-ba0e-b1f4014322a5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 561148cb1492457c4528bd1fdbf60e66233c6b6e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47708870"
---
# <a name="gettruststore-method-sqlserverdatasource"></a>getTrustStore メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  証明書の trustStore ファイルへのパス (ファイル名を含む) を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getTrustStore()  
```  
  
## <a name="return-value"></a>戻り値  
 証明書の trustStore ファイルへのパス (ファイル名を含む) を含む**文字列**です。値が設定されていない場合は null です。  
  
## <a name="remarks"></a>Remarks  
 trustStore プロパティが設定されていない場合、[getTrustStore](../../../connect/jdbc/reference/gettruststore-method-sqlserverdatasource.md) メソッドは null を返します。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
