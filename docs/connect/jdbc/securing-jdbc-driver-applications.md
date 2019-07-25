---
title: JDBC Driver アプリケーションのセキュリティ保護 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 90724ec6-a9cb-43ef-903e-793f89410bc0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c539e94b9fdcd3d1cd281e1a0f1043eec55739bc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67945742"
---
# <a name="securing-jdbc-driver-applications"></a>JDBC ドライバー アプリケーションのセキュリティ保護

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] アプリケーションのセキュリティは、陥りやすい一般的なコーディング ミスをなくせば確保できるというものではありません。 データにアクセスするアプリケーションには、機密データを取得、操作、または破壊するために攻撃者から悪用されるような障害箇所が、潜在的に数多く含まれています。 重要なのは、アプリケーションの設計段階の脅威モデリングのプロセスから、最終的な配置、さらには運用時のメンテナンスに至るまで、セキュリティのすべての側面を理解することです。  
  
このセクションのトピックでは、接続文字列、ユーザー入力の検証、全般的なアプリケーション セキュリティなどを含む、一般的なセキュリティの問題について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
| トピック                                                                            | [説明]                                                                                                                                                           |
| -------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [接続文字列のセキュリティ保護](../../connect/jdbc/securing-connection-strings.md) | データ ソースへの接続に使用される情報を保護する方法について説明します。                                                                                    |
| [ユーザー入力の検証](../../connect/jdbc/validating-user-input.md)             | ユーザー入力を検証する方法について説明します。                                                                                                                          |
| [アプリケーション セキュリティ](../../connect/jdbc/application-security.md)               | Java のポリシー アクセス許可を使用して、JDBC ドライバー アプリケーションをセキュリティで保護する方法について説明します。                                                                                |
| [SSL 暗号化の使用](../../connect/jdbc/using-ssl-encryption.md)               | SSL (Secure Sockets Layer) を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースとの通信チャネルを確立する方法について説明します。 |
| [FIPS モード](../../connect/jdbc/fips-mode.md)                                     | FIPS 準拠モードで JDBC driver を使用する方法について説明します。                                                                                                              |
  
## <a name="see-also"></a>参照  

 [JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
