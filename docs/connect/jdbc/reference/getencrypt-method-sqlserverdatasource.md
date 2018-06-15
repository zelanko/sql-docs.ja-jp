---
title: getEncrypt メソッド (SQLServerDataSource) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- getEncrypt Method (SQLServerDataSource)
apilocation:
- getEncrypt Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 1cdb12dd-6e6f-4bbd-8f5f-9e630f3ee2c9
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9262c2fb18160f5072d21a71c082bd00d17fc302
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32835007"
---
# <a name="getencrypt-method-sqlserverdatasource"></a>getEncrypt メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  返します、**ブール**encrypt プロパティが有効になっているかどうかを示す値。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean getEncypt()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**場合の暗号化を有効にします。 それ以外の場合は、 **false**です。  
  
## <a name="remarks"></a>解説  
 Encrypt プロパティ設定されている場合**true**、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]確実[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]サーバーにインストールされている証明書がある場合に、クライアントとサーバー間で送信されるすべてのデータに SSL 暗号化を使用します。  
  
 Encrypt プロパティが指定されていないかに設定する場合**false**、ドライバーは強制されません、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] SSL 暗号化をサポートするためにします。 場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]インスタンスが SSL 暗号化を強制的に構成されていない、すべての暗号化を使用せず、接続が確立します。 場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]インスタンスが SSL 暗号化を強制的に構成されている、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]は自動的に SSL 暗号化を有効にする接続は終了しますか、または適切に構成されて Java 仮想マシン (JVM) と、ドライバーが発生します。エラーがあります。 暗号化プロパティが設定されていない場合、 [getEncrypt](../../../connect/jdbc/reference/getencrypt-method-sqlserverdatasource.md)メソッドの既定値を返します**false**です。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
