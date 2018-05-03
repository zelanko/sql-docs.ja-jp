---
title: SSL のサポートについて |Microsoft ドキュメント
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
ms.assetid: 073f3b9e-8edd-4815-88ea-de0655d0325e
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 12d7d92bd86cfd5851715c839f8772d4bc7ae94a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="understanding-ssl-support"></a>SSL のサポートについて
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  接続するときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]アプリケーション暗号化を要求し、インスタンスの場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SSL 暗号化をサポートするように構成、 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] SSL ハンドシェイクを開始します。 サーバーとクライアントは、このハンドシェイクによって、データの保護に使用する暗号化と暗号アルゴリズムをネゴシエートします。 SSL ハンドシェイクが完了すると、暗号化されたデータを安全に送信できるようになります。 SSL ハンドシェイク中には、サーバーは、その公開キー証明書をクライアントに送信します。 公開キー証明書の発行者は証明機関 (CA) と呼ばれます。 その証明機関が、クライアントが信頼するいずれかの証明機関に該当するかどうかは、クライアント側で検証する必要があります。  
  
 アプリケーションが、暗号化を要求しない場合、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]を強制しません[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SSL 暗号化をサポートするためにします。 場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]インスタンスが SSL 暗号化を強制的に構成されていない、暗号化なしの接続が確立します。 場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]インスタンスが SSL 暗号化を強制的に構成されている、適切に構成された Java 仮想マシン (JVM) で実行されている場合、ドライバーは SSL 暗号化を有効に自動的にはまたはそれ以外の場合、接続が終了およびドライバーには、エラーが発生します。  
  
> [!NOTE]  
>  渡された値を確認してください**serverName**で、サブジェクト代替名 (SAN) SSL 接続のサーバー証明書を成功させるのには共通名 (CN) または DNS 名と完全に一致します。  
  
> [!NOTE]  
>  SSL を構成する方法の詳細についての[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]への接続の暗号化を参照してください[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]でトピック[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。  
  
## <a name="remarks"></a>解説  
 アプリケーションが SSL 暗号化を使用できるようにするために、 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] version 1.2 リリース以降で、次の接続プロパティが導入されました**暗号化**、 **trustServerCertificate**。、 **trustStore**、 **trustStorePassword**、および**hostNameInCertificate**です。 詳細については、次を参照してください。[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)です。  
  
 次の表方法、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]バージョンの SSL 接続シナリオ動作します。 使用する SSL 接続プロパティの組み合わせをシナリオごとに変えています。 表の値の意味を以下に示します。  
  
-   **空白**:「、プロパティは、接続文字列には存在しない」  
  
-   **値**:「プロパティ、接続文字列内に存在し、その値が無効です」  
  
-   **どの**:「には関係ない接続文字列にプロパティが存在するか、その値が有効かどうか」  
  
> [!NOTE]  
>  同じ動作が適用されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ユーザー認証と Windows 統合認証です。  
  
|encrypt|trustServerCertificate|hostNameInCertificate|trustStore|trustStorePassword|動作|  
|-------------|----------------------------|---------------------------|----------------|------------------------|--------------|  
|false または blank|any|any|any|any|[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]を強制しません[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SSL 暗号化をサポートするためにします。 サーバーに自己署名証明書が存在する場合、その SSL 証明書の交換をドライバーは開始します。 SSL 証明書の検証は行われず、(ログイン パケット内の) 資格情報のみが暗号化されます。<br /><br /> サーバーがクライアントに SSL 暗号化のサポートを要求している場合は、SSL 証明書の交換が開始されます。 SSL 証明書の検証は行われませんが、通信全体が暗号化されます。|  
|true|true|any|any|any|[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]で SSL 暗号化を使用する要求、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。<br /><br /> サーバーがクライアントに SSL 暗号化のサポートを要求している場合、またはサーバーが暗号化をサポートしている場合、ドライバーが SSL 証明書の交換を開始します。 されている場合、 **trustServerCertificate**プロパティが"true"、ドライバーは、SSL 証明書を検証できません。<br /><br /> サーバーが暗号化をサポートするように構成されていない場合、ドライバーはエラーを生成して接続を終了します。|  
|true|false または blank|空白|空白|空白|[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]で SSL 暗号化を使用する要求、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。<br /><br /> サーバーがクライアントに SSL 暗号化のサポートを要求している場合、またはサーバーが暗号化をサポートしている場合、ドライバーが SSL 証明書の交換を開始します。<br /><br /> ドライバーを使用して、 **serverName**サーバー SSL 証明書を検証し、信頼マネージャー ファクトリのルックアップ規則を使用する証明書ストアを決定に依存する、接続 URL の指定されたプロパティ。<br /><br /> サーバーが暗号化をサポートするように構成されていない場合、ドライバーはエラーを生成して接続を終了します。|  
|true|false または blank|value|空白|空白|[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]で SSL 暗号化を使用する要求、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。<br /><br /> サーバーがクライアントに SSL 暗号化のサポートを要求している場合、またはサーバーが暗号化をサポートしている場合、ドライバーが SSL 証明書の交換を開始します。<br /><br /> ドライバーに指定された値を使用して、SSL 証明書のサブジェクト値を検証、 **hostNameInCertificate**プロパティです。<br /><br /> サーバーが暗号化をサポートするように構成されていない場合、ドライバーはエラーを生成して接続を終了します。|  
|true|false または blank|空白|value|value|[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]で SSL 暗号化を使用する要求、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。<br /><br /> サーバーがクライアントに SSL 暗号化のサポートを要求している場合、またはサーバーが暗号化をサポートしている場合、ドライバーが SSL 証明書の交換を開始します。<br /><br /> ドライバーを使用して、 **trustStore**証明書の trustStore ファイルを検索するプロパティ値と**trustStorePassword**プロパティの値を trustStore ファイルの整合性を確認します。<br /><br /> サーバーが暗号化をサポートするように構成されていない場合、ドライバーはエラーを生成して接続を終了します。|  
|true|false または blank|空白|空白|value|[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]で SSL 暗号化を使用する要求、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。<br /><br /> サーバーがクライアントに SSL 暗号化のサポートを要求している場合、またはサーバーが暗号化をサポートしている場合、ドライバーが SSL 証明書の交換を開始します。<br /><br /> ドライバーを使用して、 **trustStorePassword**プロパティの値を既定の trustStore ファイルの整合性を確認します。<br /><br /> サーバーが暗号化をサポートするように構成されていない場合、ドライバーはエラーを生成して接続を終了します。|  
|true|false または blank|空白|value|空白|[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]で SSL 暗号化を使用する要求、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。<br /><br /> サーバーがクライアントに SSL 暗号化のサポートを要求している場合、またはサーバーが暗号化をサポートしている場合、ドライバーが SSL 証明書の交換を開始します。<br /><br /> ドライバーを使用して、 **trustStore**プロパティの値を trustStore ファイルの場所を検索します。<br /><br /> サーバーが暗号化をサポートするように構成されていない場合、ドライバーはエラーを生成して接続を終了します。|  
|true|false または blank|value|空白|value|[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]で SSL 暗号化を使用する要求、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。<br /><br /> サーバーがクライアントに SSL 暗号化のサポートを要求している場合、またはサーバーが暗号化をサポートしている場合、ドライバーが SSL 証明書の交換を開始します。<br /><br /> ドライバーを使用して、 **trustStorePassword**プロパティの値を既定の trustStore ファイルの整合性を確認します。 さらに、ドライバーが使用されます、 **hostNameInCertificate**プロパティの値を SSL 証明書を検証します。<br /><br /> サーバーが暗号化をサポートするように構成されていない場合、ドライバーはエラーを生成して接続を終了します。|  
|true|false または blank|value|value|空白|[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]で SSL 暗号化を使用する要求、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。<br /><br /> サーバーがクライアントに SSL 暗号化のサポートを要求している場合、またはサーバーが暗号化をサポートしている場合、ドライバーが SSL 証明書の交換を開始します。<br /><br /> ドライバーを使用して、 **trustStore**プロパティの値を trustStore ファイルの場所を検索します。 さらに、ドライバーが使用されます、 **hostNameInCertificate**プロパティの値を SSL 証明書を検証します。<br /><br /> サーバーが暗号化をサポートするように構成されていない場合、ドライバーはエラーを生成して接続を終了します。|  
|true|false または blank|value|value|value|[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]で SSL 暗号化を使用する要求、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。<br /><br /> サーバーがクライアントに SSL 暗号化のサポートを要求している場合、またはサーバーが暗号化をサポートしている場合、ドライバーが SSL 証明書の交換を開始します。<br /><br /> ドライバーを使用して、 **trustStore**証明書の trustStore ファイルを検索するプロパティ値と**trustStorePassword**プロパティの値を trustStore ファイルの整合性を確認します。 さらに、ドライバーが使用されます、 **hostNameInCertificate**プロパティの値を SSL 証明書を検証します。<br /><br /> サーバーが暗号化をサポートするように構成されていない場合、ドライバーはエラーを生成して接続を終了します。|  
  
 Encrypt プロパティ設定されている場合**true**、 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] JVM の既定の JSSE セキュリティ プロバイダーを使用して、SSL 暗号化をネゴシエートする[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 既定のセキュリティ プロバイダーでは、SSL 暗号化の正常なネゴシエートに必要なすべての機能がサポートされているとは限りません。 たとえば、既定のセキュリティ プロバイダーがサポートしていませんで使用される RSA 公開キーのサイズ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SSL 証明書。 この場合、既定のセキュリティ プロバイダーでエラーが発生し、その結果 JDBC ドライバーが接続を終了する可能性があります。 この問題を解決するには、次のいずれかを実行します。  
  
-   構成、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]小さい RSA 公開キーを持つサーバー証明書を使用  
  
-   別の JSSE セキュリティ プロバイダーを使用するように JVM を構成する、"\<java ホーム >/lib/security/java.security"セキュリティ プロパティ ファイル  
  
-   別の JVM を使用します。  
  
## <a name="validating-server-ssl-certificate"></a>サーバーの SSL 証明書の検証  
 SSL ハンドシェイク中には、サーバーは、その公開キー証明書をクライアントに送信します。 そのサーバー証明書が、クライアントが信頼している証明機関によって発行されているかどうかを、JDBC ドライバーまたはクライアントが検証する必要があります。 ドライバーは、サーバー証明書で次の条件が満たされている状態を必要とします。  
  
-   信頼されている証明機関から発行されている。  
  
-   サーバー認証用に証明書が発行されている。  
  
-   証明書の有効期限が切れていない。  
  
-   サブジェクトで共通名 (CN) または証明書のサブジェクト代替名 (SAN) に DNS 名が正確に一致する、 **serverName**接続文字列で指定された値または指定した場合、 **hostNameInCertificate**プロパティの値。  
  
-   DNS 名にはワイルドカード文字を含めることができます。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]はワイルドカードをサポートしていません。 つまり、abc.com は *.com いない一致しますが、\*と一致する .com \*。 com です。  
  
## <a name="see-also"></a>参照  
 [SSL 暗号化を使用します。](../../connect/jdbc/using-ssl-encryption.md)   
 [JDBC ドライバー アプリケーションのセキュリティ保護](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
