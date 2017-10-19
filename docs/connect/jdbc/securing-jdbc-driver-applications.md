---
title: "JDBC ドライバー アプリケーションをセキュリティで保護する |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90724ec6-a9cb-43ef-903e-793f89410bc0
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 5051d2d668105bd0a309eb64f2b8becd459d8a6b
ms.openlocfilehash: 097978fa39709dc3c5cd1b8ef150ce4f4c189b17
ms.contentlocale: ja-jp
ms.lasthandoff: 10/12/2017

---
# <a name="securing-jdbc-driver-applications"></a>JDBC ドライバー アプリケーションのセキュリティ保護
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  セキュリティを強化、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]アプリケーションで複数のコーディングよくある落とし穴を回避します。 データにアクセスするアプリケーションには、機密データを取得、操作、または破壊するために攻撃者から悪用されるような障害箇所が、潜在的に数多く含まれています。 重要なのは、アプリケーションの設計段階の脅威モデリングのプロセスから、最終的な配置、さらには運用時のメンテナンスに至るまで、セキュリティのすべての側面を理解することです。  
  
 このセクションのトピックでは、接続文字列、ユーザー入力の検証、全般的なアプリケーション セキュリティなどを含む、一般的なセキュリティの問題について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[接続文字列のセキュリティ保護](../../connect/jdbc/securing-connection-strings.md)|データ ソースへの接続に使用される情報を保護する方法について説明します。|  
|[ユーザー入力の検証](../../connect/jdbc/validating-user-input.md)|ユーザー入力を検証する方法について説明します。|  
|[アプリケーション セキュリティ](../../connect/jdbc/application-security.md)|Java のポリシー アクセス許可を使用して、JDBC ドライバー アプリケーションをセキュリティで保護する方法について説明します。|  
|[SSL 暗号化の使用](../../connect/jdbc/using-ssl-encryption.md)|セキュリティで保護された通信チャネルを確立する方法について説明します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]安全な Sockets Layer (SSL) を使用してデータベースします。|  
|[FIPS モード](../../connect/jdbc/fips-mode.md)|FIPS 準拠モードでは JDBC driver を使用する方法について説明します。| 
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  

