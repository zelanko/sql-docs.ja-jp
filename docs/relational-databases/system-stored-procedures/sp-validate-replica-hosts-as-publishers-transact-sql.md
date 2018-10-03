---
title: sp_validate_replica_hosts_as_publishers (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_validate_replica_hosts_as_publishers_TSQL
- sp_validate_replica_hosts_as_publishers
helpviewer_keywords:
- sp_validate_replica_hosts_as_publishers
ms.assetid: 45001fc9-2dbd-463c-af1d-aa8982d8c813
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9143c5c681ed9e992a06ccad6be4511c23be37b5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47639697"
---
# <a name="spvalidatereplicahostsaspublishers-transact-sql"></a>sp_validate_replica_hosts_as_publishers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  **sp_validate_replica_hosts_as_publishers**の拡張機能は、 **sp_validate_redirected_publisher**すべてのセカンダリ レプリカを現在のプライマリ レプリカだけではなく検証できるようにします。 **sp_validate_replicat_hosts_as_publisher** Alwayson レプリケーション トポロジ全体を検証します。 **sp_validate_replica_hosts_as_publishers**ダブルホップ セキュリティ エラー (21892) を回避するためにリモート デスクトップ セッションを使用して、ディストリビューターに対して直接実行する必要があります。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_validate_replica_hosts_as_publishers   
    [ @original_publisher = ] 'original_publisher',  
    [ @publisher_db = ] 'database_name',   
    [ @redirected_publisher = ] 'new_publisher' output  
```  
  
## <a name="arguments"></a>引数  
 [ **@original_publisher** =] **'***original_publisher***'**  
 インスタンスの名前[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースを最初に発行します。 *original_publisher*は**sysname**、既定値はありません。  
  
 [ **@publisher_db** =] **'***publisher_db***'**  
 パブリッシュされるデータベースの名前。 *publisher_db*は**sysname**、既定値はありません。  
  
 [ **@redirected_publisher** =] **'***redirected_publisher***'**  
 リダイレクトの対象と**sp_redirect_publisher**元パブリッシャーとパブリッシュされたデータベースのペアに対して呼び出されました。 *redirected_publisher*は**sysname**、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 [なし] :  
  
## <a name="remarks"></a>コメント  
 パブリッシャーとパブリッシングのデータベースのエントリが存在しない場合**sp_validate_redirected_publisher**出力パラメーターに null を返します *@redirected_publisher*します。 それ以外の場合は、成功した場合も失敗した場合も関連付けられているリダイレクトされたパブリッシャーが返されます。  
  
 検証が成功すると、 **sp_validate_redirected_publisher**成功を示す値を返します。  
  
 検証が失敗した場合は、該当するエラーが発生します。  **sp_validate_redirected_publisher**によりすべての問題とだけでなく、最初に発生させる最善の努力が発生しました。  
  
> [!NOTE]  
>  セカンダリ レプリカのホストで読み取りアクセスが許可されていない場合や、読み取りを目的としたアクセスを指定する必要がある場合、**sp_validate_replica_hosts_as_publishers** による検証は失敗し、次のエラー メッセージが表示されます。  
>   
>  メッセージ 21899、レベル 11、状態 1、プロシージャ **sp_hadr_verify_subscribers_at_publisher**、行 109  
>   
>  元のパブリッシャー 'MyOriginalPublisher' のサブスクライバーの sysserver エントリがあるかどうかを判断するために、リダイレクトされたパブリッシャー 'MyReplicaHostName' で実行したクエリが、エラー '976'、エラー メッセージ 'エラー 976、レベル 14、状態 1、メッセージ: 対象になるデータベース 'MyPublishedDB' は可用性グループに参加しているため、現在クエリでアクセスできません。 データ移動が中断されているか、可用性レプリカの読み取りアクセスが有効になっていません。 このデータベースや可用性グループの他のデータベースへの読み取り専用アクセスを許可するには、グループの 1 つ以上のセカンダリ可用性レプリカへの読み取りアクセスを有効にします。  詳細については、 **オンライン ブックの** ALTER AVAILABILITY GROUP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ステートメントのトピックをご覧ください。  
>   
>  レプリカ ホスト 'MyReplicaHostName' について、1 つまたは複数のパブリッシャー検証エラーが発生しました。  
  
## <a name="permissions"></a>アクセス許可  
 呼び出し元する必要がありますいずれかのメンバーである、 **sysadmin**固定サーバー ロール、 **db_owner**固定データベース ロールには、ディストリビューション データベースまたは定義済みパブリケーションのパブリケーション アクセス リストのメンバーパブリッシャー データベースと関連付けられています。  
  
## <a name="see-also"></a>参照  
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_get_redirected_publisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-get-redirected-publisher-transact-sql.md)   
 [sp_redirect_publisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-redirect-publisher-transact-sql.md)   
 [sp_validate_redirected_publisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-redirected-publisher-transact-sql.md)  
  
  
