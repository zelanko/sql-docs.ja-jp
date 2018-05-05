---
title: sp_publication_validation (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
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
- sp_publication_validation
- sp_publication_validation_TSQL
helpviewer_keywords:
- sp_publication_validation
ms.assetid: 06be2363-00c0-4936-97c1-7347f294a936
caps.latest.revision: 34
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: f893c6a42d16c9d36d2a28a2c77c80bc62fa56bb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sppublicationvalidation-transact-sql"></a>sp_publication_validation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したパブリケーションの各アーティクルに対する検証の要求を開始します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_publication_validation [ @publication = ] 'publication'  
    [ , [ @rowcount_only = ] type_of_check_requested ]  
    [ , [ @full_or_fast = ] full_or_fast ]  
    [ , [ @shutdown_agent = ] shutdown_agent ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>引数  
 [**@publication=**] **' * * * パブリケーション '*  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [**@rowcount_only=**] *rowcount_only*  
 テーブルの行数のみを返すかどうかを指定します。 *rowcount_only*は**smallint**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|実行、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 互換のチェックサム。<br /><br /> 注: アーティクルが行方向にフィルター選択される場合は、チェックサム操作ではなく rowcount 操作が実行します。|  
|**1** (既定値)|行数のチェックのみを実行します。|  
|**2**|行数とバイナリのチェックサムを実行します。<br /><br /> : 注[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バージョン 7.0 サブスクライバーの場合、行数検証のみを実行します。|  
  
 [**@full_or_fast=**] *full_or_fast*  
 行数の計算で使用する方法を指定します。 *full_or_fast*は**tinyint**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|COUNT(*) を使用してフル カウントします。|  
|**1**|高速カウントから**sysindexes.rows**です。 行のカウント[sys.sysindexes](../../relational-databases/system-compatibility-views/sys-sysindexes-transact-sql.md)実際のテーブル内の行のカウントより高速です。 ただし、ため[sys.sysindexes](../../relational-databases/system-compatibility-views/sys-sysindexes-transact-sql.md)遅れてが更新されると、行カウントことができます。|  
|**2** (既定値)|最初に高速カウントを試み、条件高速カウントを行います。 高速カウントに違いが見られる場合、フル カウントに戻されます。 場合*expected_rowcount*ストアド プロシージャの中を NULL 値を取得する、フル カウントが常に使用します。|  
  
 [  **@shutdown_agent=**] *shutdown_agent*  
 検証の完了後すぐにディストリビューション エージェントをシャットダウンするかどうかを指定します。 *shutdown_agent*は**ビット**、既定値は**0**します。 場合**0**、レプリケーション エージェントがシャット ダウンできません。 場合**1**、最後のアーティクルが検証された後にレプリケーション エージェントがシャット ダウンします。  
  
 [ **@publisher** =] **'***パブリッシャー***'**  
 指定以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*検証を要求するときに使用しないで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_publication_validation**トランザクション レプリケーションで使用します。  
  
 **sp_publication_validation**パブリケーションに関連付けられているアーティクルがアクティブ化された後、いつでも呼び出すことができます。 このプロシージャは、指定日時に手動で実行するか、またはデータを検証する定期的スケジュールに組み込んだジョブの一部として実行することができます。  
  
 場合は、アプリケーションがある即時更新サブスクライバー、 **sp_publication_validation**疑似エラーを検出することがあります。 **sp_publication_validation**行数またはチェックサムがパブリッシャーとサブスクライバー側でしをまずを計算します。 行数またはチェックサムがパブリッシャーで完了していて、サブスクライバーでは完了していない場合、即時更新トリガーはサブスクライバーからパブリッシャーに更新を通知できるため、値が変更される可能性があります。 パブリケーションの検証中にサブスクライバーとパブリッシャーの値が変更されないようにするには、検証中のパブリッシャーでの Microsoft 分散トランザクション コーディネーター (MS DTC) サービスを停止します。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_publication_validation**です。  
  
## <a name="see-also"></a>参照  
 [サブスクライバーでのデータの検証](../../relational-databases/replication/validate-data-at-the-subscriber.md)   
 [sp_article_validation &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md)   
 [sp_table_validation &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-validation-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
