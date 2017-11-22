---
title: "setEncrypt メソッド (SQLServerDataSource) |Microsoft ドキュメント"
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
apiname: setEncrypt Method (SQLServerDataSource)
apilocation: setEncrypt Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 0c85a9c1-f27c-457e-8461-403cc03e2d17
caps.latest.revision: "22"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9e90e49bff2956be8aa6950ec9612ea534921aac
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="setencrypt-method-sqlserverdatasource"></a>setEncrypt メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  セット、**ブール**encrypt プロパティが有効になっているかどうかを示す値。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setEncypt(boolean encrypt)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *暗号化します。*  
  
 **true**クライアント間で Secure Sockets Layer (SSL) 暗号化が有効になっているかどうか、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。 それ以外の場合は、 **false**です。  
  
## <a name="remarks"></a>解説  
 Encrypt プロパティ設定されている場合**true**、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]確実[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]サーバーにインストールされている証明書がある場合に、クライアントとサーバー間で送信されるすべてのデータに SSL 暗号化を使用します。 既定値は **false**です。  
  
 JDBC ドライバーは、SSL ハンドシェイクの確立を試みる際に、使用中の Java 仮想マシン (JVM) を検出します。  
  
 Encrypt プロパティ設定されている場合**true**、 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] JVM の既定の JSSE セキュリティ プロバイダーを使用して、SSL 暗号化をネゴシエートする[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。 既定のセキュリティ プロバイダーでは、SSL 暗号化の正常なネゴシエートに必要なすべての機能がサポートされているとは限りません。 たとえば、既定のセキュリティ プロバイダーがサポートしていませんで使用される RSA 公開キーのサイズ、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] SSL 証明書。 この場合、既定のセキュリティ プロバイダーでエラーが発生し、その結果 JDBC ドライバーが接続を終了する可能性があります。 この問題を解決するには、次のいずれかを実行します。  
  
-   構成、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]小さい RSA 公開キーを持つサーバー証明書を使用  
  
-   別の JSSE セキュリティ プロバイダーを使用するように JVM を構成する、"\<java ホーム >/lib/security/java.security"セキュリティ プロパティ ファイル  
  
-   別の JVM を使用します。  
  
 Encrypt プロパティが指定されていないかに設定する場合**false**、ドライバーは強制されません、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] SSL 暗号化をサポートするためにします。 場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]インスタンスが SSL 暗号化を強制的に構成されていない、すべての暗号化を使用せず、接続が確立します。 場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]インスタンスが SSL 暗号化を強制的に構成されている、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]は自動的に SSL 暗号化を有効にする接続は終了しますか、または、JVM で正しく実行されているように構成し、ドライバーは、エラーが発生します。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
