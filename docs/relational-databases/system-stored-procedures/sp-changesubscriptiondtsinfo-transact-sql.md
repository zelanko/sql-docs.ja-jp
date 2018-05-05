---
title: sp_changesubscriptiondtsinfo (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
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
- sp_changesubscriptiondtsinfo
- sp_changesubscriptiondtsinfo_TSQL
helpviewer_keywords:
- sp_changesubscriptiondtsinfo
ms.assetid: 64fc085f-f81b-493b-b59a-ee6192d9736d
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 55c43914d883ce5f704ad6c7648d473bd38611fb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spchangesubscriptiondtsinfo-transact-sql"></a>sp_changesubscriptiondtsinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サブスクリプションのデータ変換サービス (DTS) パッケージのプロパティを変更します。 このストアド プロシージャは、サブスクライバー側でサブスクリプション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_changesubscriptiondtsinfo [ [ @job_id = ] job_id ]  
    [ , [ @dts_package_name= ] 'dts_package_name' ]  
    [ , [ @dts_package_password= ] 'dts_package_password' ]  
    [ , [ @dts_package_location= ] 'dts_package_location' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@job_id=**] *job_id*  
 プッシュ サブスクリプションのディストリビューション エージェントのジョブ ID を指定します。 *job_id*は**varbinary (16)**、既定値はありません。 ディストリビューション ジョブ ID を見つけるには実行**sp_helpsubscription**または**sp_helppullsubscription**です。  
  
 [ **@dts_package_name**=] **'***dts_package_name***'**  
 DTS パッケージの名前を指定します。 *dts_package_name*は、 **sysname**、既定値は NULL です。 たとえば、パッケージを指定する名前**DTSPub_Package**を指定する場合`@dts_package_name = N'DTSPub_Package'`です。  
  
 [ **@dts_package_password**=] **'***dts_package_password***'**  
 パッケージのパスワードを指定します。 *dts_package_password*は**sysname**既定値は NULL の場合、変更されていないパスワード プロパティのままにすることを指定します。  
  
> [!NOTE]  
>  DTS パッケージにはパスワードが必要です。  
  
 [ **@dts_package_location**=] **'***dts_package_location***'**  
 パッケージの場所を指定します。 *dts_package_location*は、 **nvarchar (12)**、既定値は NULL、変更しないままにする、パッケージの場所を指定します。 パッケージの場所を変更できます**ディストリビューター**または**サブスクライバー**です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_changesubscriptiondtsinfo**スナップショット レプリケーションおよびトランザクション レプリケーションでプッシュ サブスクリプションのみに使用します。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロール、 **db_owner**固定データベース ロール、またはサブスクリプションの作成者が実行できる**sp_changesubscriptiondtsinfo**です。  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
