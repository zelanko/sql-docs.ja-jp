---
title: sp_copysubscription (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_copysubscription
- sp_copysubscription_TSQL
helpviewer_keywords:
- sp_copysubscription
ms.assetid: 3c56cd62-2966-4e87-a986-44cb3fd0b760
caps.latest.revision: 33
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a8a6a53bc7f9b793dfef4b685c4d55033657a152
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spcopysubscription-transact-sql"></a>sp_copysubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  これはアタッチ可能なサブスクリプション機能ですが、使用は推奨されず、将来のリリースで削除されます。 この機能は、新しい開発作業では使用できません。 パラメーター化されたフィルターを使用してパーティション分割されたマージ パブリケーションでは、パーティション スナップショットの新しい機能を使用することをお勧めします。この機能を使用すると、多数のサブスクリプションの初期化を簡単に実行できます。 詳細については、「 [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)」を参照してください。 パーティション分割されていないパブリケーションでは、バックアップを使用してサブスクリプションを初期化できます。 詳細については、「 [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)を使用して、サブスクリプションを手動で初期化する方法について説明します。  
  
 プル サブスクリプションはあるがプッシュ サブスクリプションはないサブスクリプション データベースをコピーします。 単一ファイルのデータベースのみをコピーできます。 このストアド プロシージャは、サブスクライバー側でサブスクリプション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_copysubscription [ @filename = ] 'file_name'  
    [ , [ @temp_dir = ] 'temp_dir' ]  
    [ , [ @overwrite_existing_file = ] overwrite_existing_file]  
```  
  
## <a name="arguments"></a>引数  
 [ **@filename =**] **'***file_name***'**  
 データ ファイル (.mdf) のコピーを保存する場所を表す、ファイル名を含む完全なパスの文字列を指定します。 *ファイル名*は**nvarchar (260)**、既定値はありません。  
  
 [  **@temp_dir=**] **'***temp_dir***'**  
 一時ファイルを格納するディレクトリの名前を指定します。 *temp_dir*は**nvarchar (260)**、既定値は NULL です。 NULL の場合、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]既定データ ディレクトリが使用されます。 このディレクトリは、すべてのサブスクライバー データベース ファイルを合わせたファイル サイズを格納できるだけの領域を備えている必要があります。  
  
 [  **@overwrite_existing_file=**] **'***overwrite_existing_file***'**  
 指定された同じ名前の既存のファイルを上書きするかどうかを指定するオプションのブール フラグは、  **@filename**です。 *overwrite_existing_file*は**ビット**、既定値は**0**します。 場合**1**、によって指定されたファイルが上書きされます **@filename**存在する場合、します。 場合**0**ファイルが存在し、ファイルが上書きされない場合、ストアド プロシージャは失敗します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_copysubscription**はサブスクライバーでスナップショットを適用する代わりに、サブスクリプション データベースをファイルにコピーするすべての種類のレプリケーションで使用します。 データベースは、プル サブスクリプションのみをサポートするように構成する必要があります。 適切な権限を持つユーザーは、サブスクリプション データベースのコピーを作成し、サブスクリプション ファイル (.msf) を別のサブスクライバーに電子メールで送信、コピー、または転送できます。受信側のサブスクライバーでは、ファイルをサブスクリプションとしてアタッチできます。  
  
 コピーされるサブスクリプション データベースのサイズは 2 ギガバイト (GB) 未満でなければなりません。  
  
 **sp_copysubscription**はクライアント サブスクリプションを持つデータベースに対してのみサポートされ、データベースはサーバー サブスクリプションを持つときに実行されることはできません。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_copysubscription**です。  
  
## <a name="see-also"></a>参照  
 [代替スナップショット フォルダーの場所](../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
