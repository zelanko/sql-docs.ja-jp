---
title: "DROP AVAILABILITY GROUP (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
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
f1_keywords:
- DROP_AVAILABILITY_GROUP_TSQL
- DROP AVAILABILITY GROUP
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], removing
- Availability Groups [SQL Server], Transact-SQL statements
- DROP AVAILABILITY GROUP statement
- Availability Groups [SQL Server], dropping
ms.assetid: c1600289-c990-454a-b279-dba0ebd5d63e
caps.latest.revision: 44
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c1cd1e16d7d25810d571f940aaf1dece825406c3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drop-availability-group-transact-sql"></a>DROP AVAILABILITY GROUP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  指定された可用性グループとそのすべてのレプリカを削除します。 可用性グループを削除する際、可用性レプリカの 1 つをホストするサーバー インスタンスがオフラインだった場合は、再度オンラインになった時点でローカルの可用性レプリカが削除されます。 可用性グループを削除すると、関連付けられている可用性グループ リスナーも削除されます (存在する場合)。  
  
> [!IMPORTANT]  
>  可能であれば、プライマリ レプリカをホストするサーバー インスタンスに接続しているときにのみ可用性グループを削除してください。 可用性グループをプライマリ レプリカから削除すると、元のプライマリ データベースで変更が許可されます (高可用性の保護なし)。 プライマリ レプリカでセカンダリ レプリカから可用性グループの削除が離れる、 **RESTORING**状態、および変更がデータベースで許可されていません。  
  
 可用性グループを削除する別の方法については、次を参照してください[可用性グループ &#40; を削除します。。SQL Server &#41;](../../database-engine/availability-groups/windows/remove-an-availability-group-sql-server.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP AVAILABILITY GROUP group_name   
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *group_name*  
 削除する可用性グループの名前を指定します。  
  
## <a name="limitations-and-recommendations"></a>制限事項と推奨事項  
  
-   実行する**DROP AVAILABILITY GROUP**サーバー インスタンスで、Always On 可用性グループ機能が有効である必要があります。 詳細については、「[AlwaysOn 可用性グループの有効化と無効化 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)」を参照してください。  
  
-   **DROP AVAILABILITY GROUP**トランザクション内でバッチの一部として実行することはできません。 また、式および変数はサポートされません。  
  
-   可用性グループの削除は、その可用性グループに対する適切なセキュリティ資格情報が存在する任意の Windows Server フェールオーバー クラスタリング (WSFC) ノードから行うことができます。 そのため、可用性レプリカがまったく残っていなくても可用性グループを削除することができます。  
  
    > [!IMPORTANT]  
    >  Windows Server フェールオーバー クラスタリング (WSFC) クラスターにクォーラムがない場合は、可用性グループを削除しないでください。 クラスターのクォーラムがないときに可用性グループを削除すると、クラスターに格納されているメタデータ可用性グループは削除されません。 クラスターのクォーラムが再取得された後、WSFC クラスターから削除するために、可用性グループをもう一度削除する必要があります。  
  
-   セカンダリ レプリカで**DROP AVAILABILITY GROUP**緊急の目的だけのみ使用する必要があります。 理由は、可用性グループを削除すると可用性グループがオフラインになるためです。 プライマリ レプリカが判断できない場合は、セカンダリ レプリカから可用性グループを削除するかどうか、**オフライン**状態がクォーラム損失、強制フェールオーバーのために発生した、または**DROP AVAILABILITY GROUP**コマンド。 プライマリ レプリカに移行し、 **RESTORING**スプリット ブレイン状況の発生を防ぐために状態です。 詳細については、「 [動作方法: DROP AVAILABILITY GROUP の動作](http://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) 」(CSS SQL Server エンジニアのブログ) を参照してください。  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>Permissions  
 必要があります**ALTER AVAILABILITY GROUP**可用性グループの権限**CONTROL AVAILABILITY GROUP**権限、 **ALTER ANY AVAILABILITY GROUP**権限、または**CONTROL SERVER**権限です。 必要があるローカル サーバー インスタンスによってホストされていない可用性グループを削除する**CONTROL SERVER**権限または**コントロール**その可用性グループに対する権限。  
  
## <a name="examples"></a>使用例  
 次の例では削除、`AccountsAG`可用性グループです。  
  
```  
DROP AVAILABILITY GROUP AccountsAG;  
```  
  
##  <a name="RelatedContent"></a> 関連コンテンツ  
  
-   [動作方法: DROP AVAILABILITY GROUP の動作](http://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) (CSS SQL Server エンジニアのブログ)  
  
## <a name="see-also"></a>参照  
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md)   
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [可用性グループの削除 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/remove-an-availability-group-sql-server.md)  
  
  

