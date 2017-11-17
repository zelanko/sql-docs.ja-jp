---
title: "ALTER DATABASE データベース ミラーリング (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/17/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- witness [SQL Server], establishing
- manual failover [SQL Server]
- ALTER DATABASE statement, database mirroring
- database mirroring [SQL Server], Transact-SQL
ms.assetid: 27a032ef-1cf6-4959-8e67-03d28c4b3465
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 96ac469df9660e29c0394226cf7199e451df9d8c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alter-database-transact-sql-database-mirroring"></a>ALTER DATABASE (TRANSACT-SQL) データベース ミラーリング 
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 代わりに [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] を使用します。  
  
 データベースのデータベース ミラーリングを制御します。 データベース ミラーリング オプションで指定した値は、データベースのコピーと、データベース ミラーリング セッション全体の両方に適用されます。 1 つだけ\<database_mirroring_option > は ALTER DATABASE ステートメントごとに許可します。  
  
> [!NOTE]  
>  構成は、パフォーマンスに影響を及ぼすために、オフピーク時間中にデータベース ミラーリングを構成することをお勧めします。  
  
 ALTER DATABASE オプションについては、次を参照してください。 [ALTER DATABASE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-transact-sql.md). ALTER DATABASE SET オプションでは、次を参照してください。 [ALTER DATABASE SET Options & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER DATABASE database_name   
SET { <partner_option> | <witness_option> }  
  <partner_option> ::=  
    PARTNER { = 'partner_server'   
            | FAILOVER   
            | FORCE_SERVICE_ALLOW_DATA_LOSS  
            | OFF  
            | RESUME   
            | SAFETY { FULL | OFF }  
            | SUSPEND   
            | TIMEOUT integer  
            }  
  <witness_option> ::=  
    WITNESS { = 'witness_server'   
            | OFF   
            }  
  
```  
  
## <a name="arguments"></a>引数  
  
> [!IMPORTANT]  
>  SET PARTNER または SET WITNESS コマンドは入力時には正常に完了できますが、後で失敗します。  
  
> [!NOTE]  
>  ALTER DATABASE データベース ミラーリング オプションは、包含データベースでは使用できません。  
  
 *database_name*  
 変更するデータベースの名前を指定します。  
  
 パートナー \<partner_option >  
 データベース ミラーリング セッションのフェールオーバー パートナー、およびそれらの動作を定義する、データベース プロパティを制御します。 SET PARTNER オプションには、パートナーのうちのいずれか一方で設定すればよいものと、プリンシパル サーバーとミラー サーバーのいずれか一方に限定されているものがあります。 詳細については、後述の各 PARTNER オプションを参照してください。 SET PARTNER 句は、それを指定したパートナーには関係なく、データベースの両方のコピーに影響します。  
  
 SET PARTNER ステートメントを実行するには、両方のパートナーのエンドポイントの STATE が、STARTED に設定されている必要があります。 また、それぞれのパートナー サーバー インスタンスのデータベース ミラーリング エンドポイントの ROLE は、PARTNER または ALL のいずれかに設定されている必要があります。 エンドポイントを指定する方法については、次を参照してください[、データベース ミラーリング エンドポイントで Windows 認証 &#40; を作成します。。TRANSACT-SQL と #41 です。](../../database-engine/database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md). サーバー インスタンスのデータベース ミラーリング エンドポイントのロールおよび状態を確認するには、そのインスタンス上で、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用します。  
  
```  
SELECT role_desc, state_desc FROM sys.database_mirroring_endpoints  
```  
  
 **\<partner_option >:: =**  
  
> [!NOTE]  
>  1 つだけ\<partner_option > SET PARTNER 句は許可します。  
  
 **'** *partner_server* **'**  
 インスタンスのサーバー ネットワーク アドレスを指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に新しいデータベース ミラーリング セッションでのフェールオーバー パートナーとして機能します。 各セッションには 2 つのパートナーが必要です。一方はプリンシパル サーバーとして起動し、他方はミラー サーバーとして起動します。 これらのパートナーは、別々のコンピューター上に配置することをお勧めします。  
  
 このオプションは、各パートナーでのセッションごとに 1 回指定します。 2 つの ALTER DATABASE データベース ミラーリング セッションを開始する必要があります*データベース*SET PARTNER **='***partner_server***'**ステートメント. これらのステートメントの順序は非常に重要です。 最初に、ミラー サーバーに接続し、プリンシパル サーバー インスタンスを指定*partner_server* (SET PARTNER **='***principal_server***'**). 次は、プリンシパル サーバーに接続し、としてミラー サーバー インスタンスの指定*partner_server* (SET PARTNER **='***mirror_server***'**);これには、これら 2 つのパートナー間のセッションのミラーリング データベースが起動されます。 詳細については、このトピックの「 [データベース ミラーリングの設定 &#40;SQL Server&#41;](../../database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md)」を参照してください。  
  
 値*partner_server*サーバー ネットワーク アドレスです。 構文は次のとおりです。  
  
 TCP**://***\<system-address>***:***\<port>*  
  
 パラメーターの説明  
  
-   *\<システム アドレス >*などのシステム名、完全修飾ドメイン名、または、対象のコンピューター システムを明確に識別する IP アドレスの文字列です。  
  
-   *\<ポート >*パートナー サーバー インスタンスのミラーリング エンドポイントに関連付けられているポート番号です。  
  
 詳細については、「 [サーバー ネットワーク アドレスの指定 &#40;データベース ミラーリング&#41;](../../database-engine/database-mirroring/specify-a-server-network-address-database-mirroring.md)を使用します。  
  
 次の例では、SET PARTNER **='***partner_server***'**句。  
  
```  
'TCP://MYSERVER.mydomain.Adventure-Works.com:7777'  
```  
  
> [!IMPORTANT]  
>  かどうか、セッションは、セットアップの代わりに ALTER DATABASE ステートメントを使用して[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、セッションが既定の (SAFETY が FULL に設定) で完全なトランザクションの安全性に設定し、自動フェールオーバーを伴わない高い安全性モードで実行します。 自動フェールオーバーを使用するにはミラーリング監視サーバーを構成し、高パフォーマンス モードで実行するにはトランザクションの安全性を無効 (SAFETY OFF) にします。  
  
 FAILOVER  
 プリンシパル サーバーをミラー サーバーに手動でフェールオーバーします。 FAILOVER は、プリンシパル サーバー上でのみ指定できます。 このオプションは、SAFETY が FULL に設定されている (既定) 場合にのみ有効です。  
  
 フェールオーバー オプションには、**マスター**データベース コンテキストとして。  
  
 FORCE_SERVICE_ALLOW_DATA_LOSS   
 データベースが非同期状態の場合、または自動フェールオーバーが行われずデータベースが同期状態の場合、プリンシパル サーバーで障害が発生すると、データベース サービスを強制的にミラー データベースにします。  
  
 サービスの強制は、プリンシパル サーバーが停止した場合にのみ行うことを強くお勧めします。 それ以外の場合にサービスを強制すると、一部のクライアントが、新しいプリンシパル データベースではなく、元のプリンシパル データベースにアクセスし続ける可能性があります。  
  
 FORCE_SERVICE_ALLOW_DATA_LOSS は、ミラー サーバー上でのみ使用可能で、かつ次の条件をすべて満たしている必要があります。  
  
-   プリンシパル サーバーが停止している。  
  
-   WITNESS が OFF に設定またはミラーリング監視サーバーがミラー サーバーに接続します。  
  
 サービスの強制は、データベースにサービスを直ちに復元するために一部のデータが失われてもかまわないという場合にのみ行ってください。  
  
 サービスを強制すると、セッションが中断され、すべてのデータが一時的に元のプリンシパル データベースに保持されます。 元のプリンシパルが稼働し、新しいプリンシパル サーバーと通信できるようになると、データベース管理者はサービスを再開できます。 セッションを再開すると、すべての未送信ログ レコードと、それに対応する更新は失われます。  
  
 OFF  
 データベース ミラーリング セッションを削除し、データベースからミラーリングを削除します。 OFF は、どちらのパートナー上でも指定できます。 詳細については、ミラーリングの削除の影響について参照してください[データベース ミラーリングの削除 (&) #40 です。SQL Server &#41;](../../database-engine/database-mirroring/removing-database-mirroring-sql-server.md).  
  
 RESUME  
 中断状態のデータベース ミラーリング セッションを再開します。 RESUME は、プリンシパル サーバー上でのみ指定できます。  
  
 SAFETY { FULL | OFF }  
 トランザクションの安全性のレベルを設定します。 SAFETY は、プリンシパル サーバー上でのみ指定できます。  
  
 既定値は FULL です。 データベース ミラーリング セッションを同期的に実行、safety が full (で*高い安全性モード*)。 データベース ミラーリング セッションが非同期的に実行の安全性が OFF に設定されている場合 (で*高パフォーマンス モード*)。  
  
 高い安全性モードの動作は、次のように部分的にミラーリング監視に依存します。  
  
-   SAFETY が FULL に設定され、ミラーリング監視がセッションに対して設定されている場合、セッションは自動フェールオーバーを伴う高い安全性モードで実行されます。 データベースが同期され、ミラー サーバー インスタンスとミラーリング監視が引き続き相互接続している場合 (つまりクォーラムを保持している場合)、プリンシパル サーバーが失われると、セッションでは自動的にフェールオーバーが発生します。 詳細については、「[クォーラム: データベースの可用性にミラーリング監視サーバーが与える影響 &#40;Database Mirroring&#41;](../../database-engine/database-mirroring/quorum-how-a-witness-affects-database-availability-database-mirroring.md)」を参照してください。  
  
     ミラーリング監視がセッションに対して設定されていても、ミラーリング監視サーバーが切断されていると、ミラー サーバーが利用できなくなるためプリンシパル サーバーがダウンします。  
  
-   SAFETY が FULL に設定され、ミラーリング監視が OFF に設定されている場合、セッションは自動フェールオーバーを伴わない高い安全性モードで実行されます。 ミラー サーバー インスタンスがダウンしても、プリンシパル サーバー インスタンスは影響を受けません。 プリンシパル サーバー インスタンスがダウンした場合、ミラー サーバー インスタンスにサービスの提供を強制的に移行できます (データが損失する可能性があります)。  
  
 SAFETY が OFF に設定されている場合、セッションは高パフォーマンス モードで実行されます。この場合、自動フェールオーバーも手動フェールオーバーもサポートされません。 ただし、ミラー サーバーで発生した問題が、プリンシパル サーバーに影響を及ぼすことはありません。WITNESS が OFF に設定されているか、ミラーリング監視サーバーがミラーに現在接続されているときに、プリンシパル サーバー インスタンスがダウンした場合、必要に応じてミラー サーバー インスタンスにサービスの提供を強制的に移行できます (データが損失する可能性があります)。 サービスの強制の詳細については、前の「FORCE_SERVICE_ALLOW_DATA_LOSS」を参照してください。  
  
> [!IMPORTANT]  
>  高パフォーマンス モードは、ミラーリング監視の使用を想定していません。 ただし、SAFETY を OFF に設定した場合は常に、WITNESS も OFF に設定することを強くお勧めします。  
  
 SUSPEND  
 データベース ミラーリング セッションを一時停止します。  
  
 SUSPEND は、どちらのパートナー上でも指定できます。  
  
 タイムアウト*整数*  
 タイムアウト時間を秒単位で指定します。 タイムアウト時間は、ミラーリング セッションの別のインスタンスからの PING メッセージを受信するために、サーバー インスタンスが待機する最大時間です。この時間を過ぎると、待機していたインスタンスは接続解除されたものと見なされます。  
  
 TIMEOUT オプションは、プリンシパル サーバー上でのみ指定できます。 このオプションを指定しない場合、この時間は既定で 10 秒に設定されます。 5 以上の値を指定すると、タイムアウト時間は指定した秒数に設定されます。 タイムアウト値に 0 ～ 4 秒を指定すると、タイムアウト時間は自動的に 5 秒に設定されます。  
  
> [!IMPORTANT]  
>  タイムアウト期間を 10 秒以上にしておくことをお勧めします。 値を 10 秒未満に設定すると、負荷の高いシステムでは PING を受信できず、誤認エラーが示される可能性があります。  
  
 詳細については、「 [データベース ミラーリング中に発生する可能性のあるエラー](../../database-engine/database-mirroring/possible-failures-during-database-mirroring.md)」を参照してください。  
  
 ミラーリング監視サーバー \<witness_option >  
 データベースのミラーリング監視を定義するデータベース プロパティを制御します。 SET WITNESS 句は、データベースの両方のコピーに影響しますが、SET WITNESS はプリンシパル サーバー上でのみ指定できます。 クォーラムが、SAFETY の設定に関係なく、データベースの処理に必要な場合は、セッションのミラーリング監視サーバーを設定すると、詳細については、次を参照してください。[クォーラム: ミラーリング監視サーバー データベース可用性に与える影響 &#40; データベース ミラーリング &#41;](../../database-engine/database-mirroring/quorum-how-a-witness-affects-database-availability-database-mirroring.md)です。  
  
 ミラーリング監視とフェールオーバー パートナーは、別々のコンピューターに配置することをお勧めします。 詳細について、ミラーリング監視サーバーは、次を参照してください。[データベース ミラーリング監視サーバー](../../database-engine/database-mirroring/database-mirroring-witness.md)です。  
  
 SET WITNESS ステートメントを実行するには、プリンシパル サーバー インスタンスおよびミラーリング監視サーバー インスタンスのエンドポイントの STATE が STARTED に設定されている必要があります。 また、ミラーリング監視サーバー インスタンスのデータベース ミラーリング エンドポイントの ROLE は、WITNESS または ALL のいずれかに設定されている必要があります。 エンドポイントの指定方法の詳細については、次を参照してください。[データベース ミラーリング エンドポイント & #40 です。SQL Server &#41;](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md).  
  
 サーバー インスタンスのデータベース ミラーリング エンドポイントのロールおよび状態を確認するには、そのインスタンス上で、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用します。  
  
```  
SELECT role_desc, state_desc FROM sys.database_mirroring_endpoints  
```  
  
> [!NOTE]  
>  データベースのプロパティは、ミラーリング監視では設定できません。  
  
 **\<witness_option >:: =**  
  
> [!NOTE]  
>  1 つだけ\<witness_option > SET WITNESS 句は許可します。  
  
 **'** *witness_server* **'**  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスが、データベース ミラーリング セッションのミラーリング管理サーバーとして動作することを指定します。 SET WITNESS ステートメントは、プリンシパル サーバー上でのみ指定できます。  
  
 SET witness **='***witness_server***'**ステートメントの構文では、 *witness_server*はの構文と同じ*partner_server*です。  
  
 OFF  
 データベース ミラーリング セッションから、ミラーリング監視を削除します。 ミラーリング監視を OFF に設定すると、自動フェールオーバーが無効化されます。 データベースが FULL SAFETY に設定され、ミラーリング監視が OFF に設定されている場合、ミラー サーバーに障害が発生すると、プリンシパル サーバーはデータベースを使用不可にします。  
  
## <a name="remarks"></a>解説  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-database-mirroring-session-with-a-witness"></a>A. ミラーリング監視を使用したデータベース ミラーリング セッションを作成する  
 ミラーリング監視を使用したデータベース ミラーリングをセットアップするには、セキュリティを構成し、ミラー データベースを準備し、ALTER DATABASE を使用してパートナーを設定する必要があります。 完全なセットアップ プロセスの例は、次を参照してください。[データベース ミラーリングの設定 (&) #40 です。SQL Server &#41;](../../database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md).  
  
### <a name="b-manually-failing-over-a-database-mirroring-session"></a>B. データベース ミラーリング セッションを手動でフェールオーバーする  
 手動フェールオーバーは、どちらのデータベース ミラーリング パートナーからでも開始できます。 フェールオーバーする前に、現在プリンシパル サーバーであると思われるサーバーが、実際にプリンシパル サーバーであるかどうかを確認する必要があります。 たとえば、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースの場合、現在プリンシパル サーバーであると思われるサーバー インスタンスで、次のクエリを実行します。  
  
```  
SELECT db.name, m.mirroring_role_desc   
FROM sys.database_mirroring m   
JOIN sys.databases db  
ON db.database_id = m.database_id  
WHERE db.name = N'AdventureWorks2012';   
GO  
```  
  
 そのサーバー インスタンスが実際にプリンシパルである場合、`mirroring_role_desc` の値は `Principal` になります。 このサーバー インスタンスがミラー サーバーの場合、`SELECT`ステートメントを返します`Mirror`です。  
  
 次の例では、そのサーバーが現在のプリンシパルであることを前提としています。  
  
1.  データベース ミラーリング パートナーに手動でフェールオーバーするには、次のステートメントを実行します。  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET PARTNER FAILOVER;  
    GO  
    ```  
  
2.  新しいミラーでのフェールオーバーの結果を確認するには、次のクエリを実行します。  
  
    ```  
    SELECT db.name, m.mirroring_role_desc   
    FROM sys.database_mirroring m   
    JOIN sys.databases db  
    ON db.database_id = m.database_id  
    WHERE db.name = N'AdventureWorks2012';   
    GO  
    ```  
  
     `mirroring_role_desc` の現在の値は、`Mirror` です。  
  
## <a name="see-also"></a>参照  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [sys.database_mirroring_witnesses & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)  
  
  

