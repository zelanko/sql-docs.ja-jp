---
title: データベース ミラーリングの使用 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- SQL Server Native Client, database mirroring
- data access [SQL Server Native Client], database mirroring
- database mirroring [SQL Server], connecting clients to
- SQLNCLI, database mirroring
- SQL Server Native Client ODBC driver, database mirroring
- SQL Server Native Client OLE DB provider, database mirroring
ms.assetid: 71b15712-7972-4465-9274-e0ddc271eedc
caps.latest.revision: 55
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 371fb59b67547a1459739c6a71963dae34dab294
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173922"
---
# <a name="using-database-mirroring"></a>データベース ミラーリングの使用
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)] 代わりに [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] を使用します。  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] で導入されたデータベース ミラーリングは、データベースの可用性とデータの冗長性を高めるためのソリューションです。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client は、開発者がコードを記述またはデータベース用に構成されていると、その他のアクションを実行する必要はありませんので、データベース ミラーリングを暗黙的にサポートを提供します。  
  
 データベースごとに実装されている、ミラー化すると、データベースのコピーを保持する、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]実稼働データベースをスタンバイ サーバーでします。 このサーバーは、データベース ミラーリング セッションの構成および状態に応じて、ホット スタンバイ サーバーかウォーム スタンバイ サーバーのいずれかになります。 ホット スタンバイ サーバーはコミット済みトランザクションが失われない高速フェールオーバーをサポートし、ウォーム スタンバイ サーバーはサービスの強制 (データ損失の可能性あり) をサポートします。  
  
 実稼働データベースが呼び出されます、*プリンシパル データベース*、スタンバイ コピーを呼び出すと、*ミラー データベース*です。 プリンシパル データベースとミラー データベースは、別個のインスタンス上に存在する必要があります[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)](サーバー インスタンス) し、別々 のコンピューターに可能であればが存在する必要があります。  
  
 運用サーバー インスタンスと呼ばれる、*プリンシパル サーバー*と呼ばれるスタンバイ サーバーのインスタンスと通信する、*ミラー サーバー*です。 プリンシパルとミラー サーバーがミラー化データベース内のパートナーとして動作*セッション*です。 プリンシパル サーバーが失敗した場合、ミラー サーバーできますのデータベースにプリンシパル データベースと呼ばれるプロセスを介して*フェールオーバー*です。 たとえば、Partner_A と Partner_B がパートナー サーバーで、初期時点ではプリンシパル データベースがプリンシパル サーバーである Partner_A にあり、ミラー データベースがミラー サーバーである Partner_B にあるとします。 Partner_A がオフラインになった場合、Partner_B がフェールオーバーして現在のプリンシパル データベースになることができます。 Partner_A がミラー化セッションに再び参加すると、このサーバーがミラー サーバーになり、このサーバーのデータベースがミラー データベースになります。  
  
 代替データベース ミラーリング構成は、さまざまなレベルのパフォーマンスとデータの安全性を提供し、さまざまな形態のフェールオーバーをサポートします。 詳細については、「[データベース ミラーリング &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-sql-server.md)」を参照してください。  
  
 ミラー データベース名を指定するときには別名を使用できます。  
  
> [!NOTE]  
>  最初の接続試行とミラー データベースへの再接続試行のについては、次を参照してください。[データベース ミラーリング セッションへのクライアントの接続&#40;SQL Server&#41;](../../../database-engine/database-mirroring/connect-clients-to-a-database-mirroring-session-sql-server.md)です。  
  
## <a name="programming-considerations"></a>プログラミングの考慮事項  
 プリンシパル データベース サーバーに障害が発生した場合、クライアント アプリケーションの API 呼び出しの応答がエラーになり、データベースへの接続が失われたことが伝えられます。 このとき、データベースへのコミットされていない変更は反映されず、現在のトランザクションはロールバックされます。 その場合、アプリケーションは接続を閉じ (またはデータ ソース オブジェクトを解放し)、再度接続を開く必要があります。 再接続の結果、プリンパル サーバーの機能を引き継いだミラー データベースに自動的にリダイレクトされます。  
  
 接続を確立するときに、プリンシパル サーバーからクライアントに対し、フェールオーバーが行われるときに使用されるフェールオーバー パートナーの ID が送信されます。 プリンシパル サーバーで障害が発生した後で接続を確立すると、クライアント側でフェールオーバー パートナーの ID を把握できません。 このシナリオでクライアントが適切な処理を行うため、初期化プロパティおよび関連する接続文字列キーワードを使用して、クライアントが独自にフェールオーバー パートナーの ID を指定することができます。 クライアント属性が使用されるのは、このシナリオのみです。プリンシパル サーバーが利用できる場合、クライアント属性は使用されません。 クライアントが指定したフェールオーバー パートナー サーバーが、フェールオーバー パートナーとして機能しているサーバーを参照していない場合は、サーバーへの接続が拒否されます。 アプリケーションが構成の変更に対応できるようにするため、接続を確立した後で属性を調査することにより、実際のフェールオーバー パートナーの ID を特定できます。 パートナー情報をキャッシュして接続文字列を更新することを検討するか、最初の接続に失敗した場合の再接続の方法を検討することをお勧めします。  
  
> [!NOTE]  
>  この機能を DSN、接続文字列、または接続プロパティや接続属性で使用する場合は、接続で使用するデータベースを明示的に指定する必要があります。 指定しないと、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client はパートナー データベースへのフェールオーバーを実行しません。  
>   
>  ミラー化はデータベースの機能です。 複数のデータベースを併用するアプリケーションでは、この機能を利用できない場合があります。  
>   
>  また、サーバー名は大文字小文字が区別されませんが、データベース名は区別されます。 したがって、大文字小文字の使い方を DSN と接続文字列で統一してください。  
  
## <a name="sql-server-native-client-ole-db-provider"></a>SQL Server Native Client OLE DB プロバイダー  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、データベース ミラーリング接続と接続文字列の属性をサポートしています。 DBPROPSET_SQLSERVERDBINIT プロパティ セットには、SSPROP_INIT_FAILOVERPARTNER プロパティが追加されています。`FailoverPartner` キーワードは、DBPROP_INIT_PROVIDERSTRING の新しい接続文字列属性です。 詳細については、次を参照してください。[使用した Connection String Keywords with SQL Server Native Client を使用して](../applications/using-connection-string-keywords-with-sql-server-native-client.md)です。  
  
 プロバイダーが読み込まれるまでである限り、フェールオーバー キャッシュが保持される**CoUninitialize**が呼び出されたか、アプリケーションによって管理されるいくつかのオブジェクトを参照している限り、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーなど、データ ソース オブジェクト。  
  
 詳細については[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、データベース ミラーリングのサポートを参照してください[初期化プロパティと承認プロパティ](../../native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)です。  
  
## <a name="sql-server-native-client-odbc-driver"></a>SQL Server Native Client ODBC ドライバー  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、データベース ミラーリング接続と接続文字列の属性をサポートしています。 使用する SQL_COPT_SS_FAILOVER_PARTNER 属性が追加されました具体的には、 [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md)と[SQLGetConnectAttr](../../native-client-odbc-api/sqlgetconnectattr.md)関数および`Failover_Partner`としてキーワードが追加されて、新しい接続文字列属性です。  
  
 アプリケーションに環境ハンドルが少なくとも 1 つ割り当てられている限り、フェールオーバー キャッシュが保持されます。 反対に、最後の環境ハンドルの割り当てが解除されると、キャッシュが消失します。  
  
> [!NOTE]  
>  ODBC ドライバー マネージャーが拡張され、フェールオーバー サーバーの名前を指定できるようになりました。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client の機能](sql-server-native-client-features.md)   
 [データベース ミラーリング セッションへのクライアントの接続 &#40;SQL Server&#41;](../../../database-engine/database-mirroring/connect-clients-to-a-database-mirroring-session-sql-server.md)   
 [データベース ミラーリング &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  