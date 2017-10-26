---
title: "接続のトラブルシューティング |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bfba0b49-2e1f-411d-a625-d25fad9ea12d
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4adcdafe8b82a8b35dbb9b27c15749673a56bce2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="troubleshooting-connectivity"></a>接続のトラブルシューティング
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] TCP/IP がインストールして通信するために実行している必要があります、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。 使用することができます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]構成マネージャーは、ネットワーク ライブラリのプロトコルがインストールされていることを確認します。  
  
 データベース接続は、さまざまな原因により失敗する場合があります。 これらは、次に含めることができます。  
  
-   TCP/IP が有効でない[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、または指定されたサーバーやポート番号が正しくないです。 いることを確認[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]は tcp/ip が、指定されたサーバーとポートでリッスンします。 このようなエラーは、次のような例外で報告されることがあります。"ログインに失敗しました。 ホストに TCP/IP 接続できませんでした。" これは、次のいずれかの原因を示します。  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]インストールされている用のネットワーク プロトコルとして TCP/IP がインストールされていませんが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ネットワーク ユーティリティ[!INCLUDE[ssVersion2000](../../includes/ssversion2000_md.md)]、または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Configuration Manager for[!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)]およびそれ以降。  
  
    -   として TCP/IP がインストールされている、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]プロトコルがリッスンしていない、JDBC 接続 URL で指定されたポートです。 既定のポートは 1433 が[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]任意のポートでリッスンするように製品のインストール時に構成することができます。 確認して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]はポート 1433 でリッスンします。 または、ポートが変更されている場合は、JDBC 接続 URL で指定するポートを、変更されたポートと一致させます。 JDBC 接続 Url の詳細については、次を参照してください。[接続 URL の構築](../../connect/jdbc/building-the-connection-url.md)です。  
  
    -   JDBC の接続で指定されているコンピューターのアドレスの URL は、サーバーを参照しない場所[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]をインストールして開始します。  
  
    -   クライアントとサーバーを実行している間の TCP/IP のネットワーク操作[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]が動作していません。 TCP/IP 接続をチェックする[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]telnet を使用しています。 たとえば、コマンド プロンプトで次のように入力します。 `telnet 192.168.0.0 1433` 192.168.0.0 はを実行しているコンピューターのアドレス[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]がリッスンするポートは 1433 です。 TCP/IP がそのポートでリッスンしていない「Telnet が接続できません」というメッセージを受信した場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]接続します。 使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ネットワーク ユーティリティ[!INCLUDE[ssVersion2000](../../includes/ssversion2000_md.md)]、または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Configuration Manager for[!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)]とことを確認するには、後で[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ポート 1433 で TCP/IP を使用するように構成します。  
  
    -   サーバーで使用されるポートがファイアウォールで開かれていない。 これには、サーバーが使用するポート、またはオプションで、サーバーの名前付きインスタンスに関連付けられたポートが含まれます。  
  
-   指定されたデータベース名が間違っている。 既存ログインしていることを確認してください[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。  
  
-   ユーザー名またはパスワードが間違っている。 値が正しいことを確認します。  
  
-   使用すると[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]認証では、JDBC ドライバーで必要なを[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]と共にインストールされる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]認証では、既定ではありません。 インストールまたはのインスタンスを構成する場合は、このオプションが含まれることを確認してください[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーに関する問題の診断](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)   
 [JDBC ドライバーで SQL Server に接続します。](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  

