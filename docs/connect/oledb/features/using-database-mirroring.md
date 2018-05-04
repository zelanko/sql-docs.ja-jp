---
title: データベース ミラーリングの使用 |Microsoft ドキュメント
description: データベース ミラーリング OLE DB Driver for SQL Server を使用します。
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- OLE DB Driver for SQL Server, database mirroring
- data access [OLE DB Driver for SQL Server], database mirroring
- database mirroring [SQL Server], connecting clients to
- MSOLEDBSQL, database mirroring
- OLE DB Driver for SQL Server, database mirroring
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 844af0a66c8c9493b07785583297efb207c5d8ca
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="using-database-mirroring"></a>データベース ミラーリングの使用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]使用して[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]代わりにします。  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] で導入されたデータベース ミラーリングは、データベースの可用性とデータの冗長性を高めるためのソリューションです。 OLE DB Driver for SQL Server は、開発者がコードを記述またはデータベース用に構成されていると、その他のアクションを実行する必要はありませんので、データベース ミラーリングを暗黙的にサポートを提供します。  
  
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
>  この機能を DSN、接続文字列、または接続プロパティや接続属性で使用する場合は、接続で使用するデータベースを明示的に指定する必要があります。 OLE DB Driver for SQL Server はしませんパートナー データベースへのフェールオーバーにこれを行わない場合。  
>   
>  ミラー化はデータベースの機能です。 複数のデータベースを併用するアプリケーションでは、この機能を利用できない場合があります。  
>   
>  また、サーバー名は大文字小文字が区別されませんが、データベース名は区別されます。 したがって、大文字小文字の使い方を DSN と接続文字列で統一してください。  
  
## <a name="ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server  
 SQL Server の OLE DB Driver は、データベース ミラーリングの接続と接続文字列の属性をサポートします。 SSPROP_INIT_FAILOVERPARTNER プロパティが DBPROPSET_SQLSERVERDBINIT プロパティ セットに追加されて、 **FailoverPartner**キーワードは、DBPROP_INIT_PROVIDERSTRING の新しい接続文字列属性です。 詳細については、次を参照してください。 [OLE DB Driver for SQL Server での接続文字列キーワードの使用](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)です。  
  
 プロバイダーが読み込まれるまでである限り、フェールオーバー キャッシュが保持される**CoUninitialize**が呼び出されたか、アプリケーションがあるデータ ソース オブジェクトなど、SQL Server 用の OLE DB Driver で管理、一部のオブジェクトへの参照とならない限り.  
  
 SQL Server データベース ミラーリングのサポートの詳細を OLE DB Driver は、次を参照してください。[初期化プロパティと承認プロパティ](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md)です。  
 
  
## <a name="see-also"></a>参照  
 [SQL Server 機能の OLE DB ドライバー](../../oledb/features/oledb-driver-for-sql-server-features.md)   
 [データベース ミラーリング セッションへのクライアントの接続 &#40;SQL Server&#41;](../../../database-engine/database-mirroring/connect-clients-to-a-database-mirroring-session-sql-server.md)   
 [データベース ミラーリング &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
