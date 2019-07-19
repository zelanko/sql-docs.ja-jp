---
title: sp_copysubscription (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_copysubscription
- sp_copysubscription_TSQL
helpviewer_keywords:
- sp_copysubscription
ms.assetid: 3c56cd62-2966-4e87-a986-44cb3fd0b760
author: stevestein
ms.author: sstein
ms.openlocfilehash: 71027fb060a5085289aed4c8a637bc76a71bbd2a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68108681"
---
# <a name="spcopysubscription-transact-sql"></a>sp_copysubscription (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  アタッチ可能なサブスクリプション機能は非推奨し、将来のリリースで削除される予定です。 新しい開発作業でこの機能を使用しない必要があります。 パラメーター化されたフィルターを使用してパーティション分割されたマージ パブリケーションでは、パーティション スナップショットの新しい機能を使用することをお勧めします。この機能を使用すると、多数のサブスクリプションの初期化を簡単に実行できます。 詳しくは、「 [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)」をご覧ください。 パーティション分割されていないパブリケーションの場合は、バックアップを使用してサブスクリプションを初期化できます。 詳細については、「[スナップショットを使用しないトランザクション サブスクリプションの初期化](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)」を参照してください。  
  
 プル サブスクリプションはあるがプッシュ サブスクリプションはないサブスクリプション データベースをコピーします。 単一ファイルのデータベースのみをコピーできます。 このストアド プロシージャは、サブスクライバーのサブスクリプション データベースで実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_copysubscription [ @filename = ] 'file_name'  
    [ , [ @temp_dir = ] 'temp_dir' ]  
    [ , [ @overwrite_existing_file = ] overwrite_existing_file]  
```  
  
## <a name="arguments"></a>引数  
`[ @filename = ] 'file_name'` データ ファイル (.mdf) のコピーを保存するファイル名を含む、完全なパスを指定する文字列です。 *ファイル名*は**nvarchar (260)** 、既定値はありません。  
  
`[ @temp_dir = ] 'temp_dir'` 一時ファイルを格納するディレクトリの名前です。 *temp_dir*は**nvarchar (260)** 、既定値は NULL です。 NULL の場合、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]既定のデータ ディレクトリが使用されます。 このディレクトリは、すべてのサブスクライバー データベース ファイルを合わせたファイル サイズを格納できるだけの領域を備えている必要があります。  
  
`[ @overwrite_existing_file = ] 'overwrite_existing_file'` 指定された同じ名前の既存のファイルを上書きするかどうかを指定する省略可能なブール型フラグは、  **@filename** します。 *overwrite_existing_file*は**ビット**、既定値は**0**します。 場合**1**、によって指定されたファイルが上書きされます **@filename** 存在します場合。 場合**0**、ストアド プロシージャ、ファイルが存在して、ファイルが上書きされない場合は失敗します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_copysubscription**サブスクライバーでスナップショットを適用する代わりに、サブスクリプション データベースをファイルにコピーするすべての種類のレプリケーションで使用します。 データベースは、プル サブスクリプションのみをサポートするように構成する必要があります。 適切なアクセス許可を持つユーザーがサブスクリプション データベースのコピーを作成して、電子メールで送信コピー、または、どこにアタッチできます、サブスクリプションとして別のサブスクライバーのサブスクリプション ファイル (.msf) をトランスポートします。  
  
 コピー対象のサブスクリプション データベースのサイズは、2 ギガバイト (GB) 未満である必要があります。  
  
 **sp_copysubscription**はクライアント サブスクリプションを持つデータベースのみサポートされており、データベースはサーバー サブスクリプションを持つ場合に実行されることはできません。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_copysubscription**します。  
  
## <a name="see-also"></a>関連項目  
 [スナップショット フォルダーの代替位置](../../relational-databases/replication/snapshot-options.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
