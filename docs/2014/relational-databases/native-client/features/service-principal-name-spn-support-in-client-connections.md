---
title: クライアント接続でのサービス プリンシパル名 (SPN) のサポート |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, SPNs
- ODBC, SPNs
- OLE DB, SPNs
- SPNs [SQL Server]
ms.assetid: 96598c69-ce9a-4090-aacb-d546591e8af7
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d7c1401c3f6ac3407b7fa489a90ad32290af5b69
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074582"
---
# <a name="service-principal-name-spn-support-in-client-connections"></a>クライアント接続でのサービス プリンシパル名 (SPN) のサポート
  以降で[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]、あらゆるプロトコルで相互認証を有効にするサービス プリンシパル名 (Spn) のサポートが拡張されています。 以前のバージョンの[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、Spn が kerberos over TCP サポートのみときに、既定の SPN、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンスは、Active Directory に登録されました。  
  
 Spn を使用して、認証プロトコルによって判断いるアカウントを[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンスが実行されています。 インスタンスのアカウントが判明した場合は、Kerberos 認証を使用したクライアントとサーバーによる相互認証が可能となります。 インスタンスのアカウントが不明である場合は、NTLM 認証を使用して、サーバーによるクライアントの認証のみが行われます。 現在、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client が、認証を参照して、インスタンス名とネットワーク接続のプロパティから SPN を生成します。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスはスタートアップ時に、Spn を登録しようとします。 または、手動で登録できます。 ただし、SPN を登録するアカウントのアクセス権が不十分である場合は、登録が失敗します。  
  
 ドメインおよびコンピューター アカウントは、自動的に Active Directory に登録されます。 これらのアカウントを SPN として使用することも、管理者が独自に SPN を定義することもできます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] クライアントが直接使用する SPN を指定できるようにしてより管理し、信頼性の高い認証を安全になります。  
  
> [!NOTE]  
>  クライアント アプリケーションで指定された SPN は、Windows 統合セキュリティを使用して接続されている場合にのみ使用されます。  
  
> [!TIP]  
>  **[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Kerberos Configuration Manager for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]** は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]と Kerberos に関する接続性の問題のトラブルシューティングに役立つ診断ツールです。 Kerberos 認証の詳細については、「 [Microsoft® Kerberos Configuration Manager for SQL Server®](http://www.microsoft.com/download/details.aspx?id=39046)」をご覧ください。  
  
> [!TIP]  
>  **[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Kerberos Configuration Manager for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]** は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]と Kerberos に関する接続性の問題のトラブルシューティングに役立つ診断ツールです。 Kerberos 認証の詳細については、「 [Microsoft® Kerberos Configuration Manager for SQL Server®](http://www.microsoft.com/download/details.aspx?id=39046)」をご覧ください。  
  
 Kerberos の詳細については、次の記事を参照してください。  
  
-   [Windows 用の Kerberos に関する技術的補足](http://go.microsoft.com/fwlink/?LinkId=101449)  
  
-   [Microsoft Kerberos](http://go.microsoft.com/fwlink/?LinkID=100758)  
  
## <a name="usage"></a>使用方法  
 次の表では、セキュリティで保護された認証をクライアント アプリケーションで使用するための、最も一般的なシナリオについて説明します。  
  
|シナリオ|説明|  
|--------------|-----------------|  
|レガシ アプリケーションで SPN が指定されない。|この互換性のシナリオでは、以前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で作成されたアプリケーションの動作が変更されないことが保証されます。 SPN が指定されていない場合、アプリケーションは生成された SPN を使用し、どの認証方法が使用されるかは認識しません。|  
|現在のバージョンを使用してクライアント アプリケーション[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client では、ドメイン ユーザーまたはコンピューター アカウント、インスタンス固有の SPN、またはユーザー定義の文字列、接続文字列に、SPN を指定します。|プロバイダー文字列、初期化文字列、または接続文字列で `ServerSPN` キーワードを使用することで、次の操作が可能になります。<br /><br /> -によって使用されるアカウントを指定する、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンスが接続します。 これにより、Kerberos 認証へのアクセスが簡単になります。 Kerberos キー配布センター (KDC) が存在し、かつ正しいアカウントが指定された場合は、NTLM よりも Kerberos 認証が使用される可能性が高くなります。 KDC は通常、ドメイン コントローラーと同じコンピューターに存在します。<br />-検索のサービス アカウントに SPN を指定します、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンス。 各[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンスをこの目的で使用できる 2 つの既定の Spn が生成されます。 ただし、これらのキーが Active Directory に存在することは保証されないため、この状況では Kerberos 認証は保証されません。<br />-指定のサービス アカウントの検索に使用される SPN、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンス。 これは、サービス アカウントにマップされる任意のユーザー定義文字列でかまいません。 この場合は、キーを手動で KDC に登録する必要があり、キーがユーザー定義 SPN の規則を満たしていることも必要です。<br /><br /> `FailoverPartnerSPN`キーワードを使用して、フェールオーバー パートナー サーバーの SPN を指定できます。 アカウントおよび Active Directory キーの値の範囲は、プリンシパル サーバーに指定できる値と同じです。|  
|ODBC アプリケーションで、SPN がプリンシパル サーバーまたはフェールオーバー パートナー サーバーの接続属性として指定される。|接続属性 `SQL_COPT_SS_SERVER_SPN` を使用して、プリンシパル サーバーへの接続用の SPN を指定できます。<br /><br /> 接続属性 `SQL_COPT_SS_FAILOVER_PARTNER_SPN` を使用して、フェールオーバー パートナー サーバーの SPN を指定できます。|  
|OLE DB アプリケーションで、SPN がプリンシパル サーバーまたはフェールオーバー パートナー サーバーのデータ ソース初期化プロパティとして指定される。|接続プロパティ`SSPROP_INIT_SERVER_SPN`で、`DBPROPSET_SQLSERVERDBINIT`接続の SPN を指定するプロパティ セットを使用できます。<br /><br /> `SSPROP_INIT_FAILOVER_PARTNER_SPN` 内の接続プロパティ `DBPROPSET_SQLSERVERDBINIT` を使用して、フェールオーバー パートナー サーバーの SPN を指定できます。|  
|ユーザーが、サーバーまたはフェールオーバー パートナー サーバーの SPN を ODBC データ ソース名 (DSN) で指定する。|SPN は、DSN を設定するダイアログ ボックスを使用して ODBC DSN に指定できます。|  
|ユーザーが、サーバーまたはフェールオーバー パートナー サーバーの SPN を、OLE DB の **[データ リンク]** または **[ログイン]** ダイアログ ボックスで指定する。|SPN は、 **[データ リンク]** または **[ログイン]** ダイアログ ボックスで指定できます。 **[ログイン]** ダイアログ ボックスは、ODBC または OLE DB で使用できます。|  
|ODBC アプリケーションで、接続の確立に使用された認証方法が特定される。|接続が正常に開いている場合、アプリケーションでは接続属性 `SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD` をクエリして、使用された認証方法を特定できます。 値が含まれますに限定されません`NTLM`と`Kerberos`です。|  
|OLE DB アプリケーションで、接続の確立に使用された認証方法が特定される。|接続プロパティのクエリをアプリケーションに接続が正常に開いている場合`SSPROP_AUTHENTICATION_METHOD`で、`DBPROPSET_SQLSERVERDATASOURCEINFO`使用された認証方法を決定するプロパティを設定します。 値が含まれますに限定されません`NTLM`と`Kerberos`です。|  
  
## <a name="failover"></a>[フェールオーバー]  
 SPN はフェールオーバー キャッシュに保存されないため、接続間で受け渡すことができません。 接続文字列または接続属性に SPN が指定されると、プリンシパルおよびパートナーへの接続が試行されるたびに SPN が使用されます。  
  
## <a name="connection-pooling"></a>接続のプール  
 SPN をすべての文字列ではなく一部の接続文字列で指定すると、プールが断片化する原因となることがあるので、アプリケーションでは注意が必要です。  
  
 アプリケーションでは、接続文字列キーワードを指定する代わりに、プログラムによって SPN を接続属性として指定できます。 こうすると、接続プールの断片化を管理するうえで役立ちます。  
  
 接続文字列内の SPN は対応する接続属性を設定することでオーバーライドできますが、接続のプールで使用される接続文字列は、プールの目的で接続文字列値を使用するので、アプリケーションでは注意が必要です。  
  
## <a name="down-level-server-behavior"></a>下位サーバーの動作  
 新しい接続動作はクライアントで実装されるため、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のバージョンに固有ではありません。  
  
## <a name="linked-servers-and-delegation"></a>リンク サーバーと委任  
 リンク サーバーを作成すると、`@provstr`のパラメーター [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)サーバーとフェールオーバー パートナーの Spn を指定するために使用できます。 そのメリットは、クライアントの接続文字列で SPN を指定する場合と同じです。つまり、Kerberos 認証を使用する接続を、より簡単かつ確実に確立できます。  
  
 リンク サーバーでの委任には、Kerberos 認証が必要です。  
  
## <a name="management-aspects-of-spns-specified-by-applications"></a>アプリケーションによって指定される SPN の管理上の考慮事項  
 SPN をアプリケーションで接続文字列を通じて指定するか、プログラムで接続プロパティを通じて指定するか (プロバイダーが生成した既定の SPN を使用しない) を選択する際には、次の事項を検討してください。  
  
-   セキュリティ : 指定した SPN が保護されている情報を開示する可能性。  
  
-   信頼性: 既定の Spn の使用を有効にするサービス アカウントを[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンスの実行は、KDC 上の Active Directory を更新するための十分な特権が必要です。  
  
-   利便性と場所の透過性 : アプリケーションのデータベースを別の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスに移した場合の、アプリケーションの SPN に対する影響。 データベース ミラーリングを使用する場合は、プリンシパル サーバーとそのフェールオーバー パートナーの両方について、この事項を検討する必要があります。 また、サーバーの変更に伴って SPN を変更する場合のアプリケーションに対する影響や、 すべての変更に関する管理の有無についても検討してください。  
  
## <a name="specifying-the-spn"></a>SPN の指定  
 SPN は、ダイアログ ボックスおよびコードで指定できます。 ここでは、SPN を指定する方法について説明します。  
  
 SPN の最大長は 260 文字です。  
  
 接続文字列または接続属性で SPN に使用される構文は次のとおりです。  
  
|構文|説明|  
|------------|-----------------|  
|MSSQLSvc/*fqdn*|TCP 以外のプロトコルが使用される場合に、既定のインスタンスに対してプロバイダーが生成する既定の SPN。<br /><br /> *fqdn* は、完全修飾ドメイン名です。|  
|MSSQLSvc/*fqdn*:*port*|TCP が使用される場合にプロバイダーが生成する既定の SPN。<br /><br /> *port* は、TCP ポート番号です。|  
|MSSQLSvc/*fqdn*:*InstanceName*|TCP 以外のプロトコルが使用される場合に、名前付きインスタンスに対してプロバイダーが生成する既定の SPN。<br /><br /> *InstanceName*は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンス名。|  
|HOST/*fqdn*<br /><br /> HOST/*MachineName*|Windows で自動的に登録されるビルトイン コンピューター アカウントにマップされる SPN。|  
|*Username*@*Domain*|ドメイン アカウントの直接指定。<br /><br /> *Username* は、Windows ユーザー アカウントの名前です。<br /><br /> *Domain* は、Windows ドメイン名または完全修飾ドメイン名です。|  
|*MachineName*$@*Domain*|コンピューター アカウントの直接指定。<br /><br /> (接続しているサーバーが Kerberos 認証を取得するには、ローカル システムや NETWORK SERVICE アカウントで実行されている場合`ServerSPN`にすることができます、 *MachineName*$@*ドメイン*形式)|  
|*KDCKey*/*MachineName*|ユーザー指定の SPN。<br /><br /> *KDCKey* は、KDC キーの規則に従っている英数字の文字列です。|  
  
## <a name="odbc-and-ole-db-syntax-supporting-spns"></a>SPN をサポートする ODBC および OLE DB の構文  
 各構文の情報については、次のトピックを参照してください。  
  
-   [サービス プリンシパル名&#40;Spn&#41;クライアント接続で&#40;ODBC&#41;](../odbc/service-principal-names-spns-in-client-connections-odbc.md)  
  
-   [サービス プリンシパル名&#40;Spn&#41;クライアント接続で&#40;OLE DB&#41;](../ole-db/service-principal-names-spns-in-client-connections-ole-db.md)  
  
 この機能を説明するサンプル アプリケーションについては、「 [SQL Server データ プログラミング サンプル](http://msftdpprodsamples.codeplex.com/)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client の機能](sql-server-native-client-features.md)  
  
  
