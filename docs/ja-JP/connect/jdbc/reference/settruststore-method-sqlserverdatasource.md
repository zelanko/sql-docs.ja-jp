---
title: setTrustStore メソッド (SQLServerDataSource) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- setTrustStore Method (SQLServerDataSource)
apilocation:
- setTrustStore Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: bab5485d-4547-426c-adbe-44e2b5702d1d
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 69e1a64ea387f97b9cf478366c3d269002e07cdf
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="settruststore-method-sqlserverdatasource"></a>setTrustStore メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  証明書の trustStore ファイルへのパス (ファイル名を含む) を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setTrustStore(java.lang.String trustStore)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *trustStore*  
  
 A**文字列**パス (ファイル名を含む) を証明書の trustStore ファイルを含むです。  
  
## <a name="remarks"></a>解説  
 TrustStore プロパティが指定されていないかに設定の null の場合、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]は、信頼マネージャー ファクトリの検索を使用する証明書ストアの場所を決定するルールに依存します。 既定の SunX509 TrustManagerFactory この順序で次の場所にトラスト マテリアルを見つけようと試みます。  
  
-   1. Java 仮想マシン (JVM) システム プロパティの "javax.net.ssl.trustStore" で指定されたファイル  
  
-   2. "\<java-home>/lib/security/jssecacerts" file.  
  
-   3. "\<java ホーム >/ライブラリ/セキュリティ/cacerts"ファイル。  
  
 詳細については、Sun Microsystems の Web サイトにある SunX509 TrustManager Interface に関するドキュメントを参照してください。  
  
 trustStore プロパティが文字列または空の文字列 "" に設定されている場合、ドライバーはその値を使用して trustStore ファイルを検索し、サーバーの SSL 証明書を検証します。  
  
 trustStorePassword プロパティは trustStore プロパティと共に指定でき、その値を trustStore ファイルを開くために使用します。 詳細については、次を参照してください。 [setTrustStorePassword](../../../connect/jdbc/reference/settruststorepassword-method-sqlserverdatasource.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
