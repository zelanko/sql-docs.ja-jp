---
title: sp_vupgrade_replication (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_vupgrade_replication_TSQL
- sp_vupgrade_replication
helpviewer_keywords:
- sp_vupgrade_replication
ms.assetid: d2c0ed66-07d1-4adc-82e5-a654376879bc
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ab783933dd060c23019db5a7c16e9734e59bb140
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52802284"
---
# <a name="spvupgradereplication-transact-sql"></a>sp_vupgrade_replication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  レプリケーション サーバーのアップグレード時に、セットアップによって起動されます。 現在の製品レベルでレプリケーションをサポートするため、必要に応じてスキーマとシステム データをアップグレードします。 また、システム データベースとユーザー データベースに、新しいレプリケーション システム オブジェクトを作成します。 このストアド プロシージャは、レプリケーションのアップグレードが行われるマシンで実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_vupgrade_replication [ [@login=] 'login' ]  
    [ , [ @password= ] 'password' ]  
    [ , [ @ver_old= ] 'old_version' ]  
    [ , [ @force_remove= ] 'force_removal' ]  
    [ , [ @security_mode= ] security_mode ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@login=**] **'***ログイン***'**  
 ディストリビューション データベースに新しいシステム オブジェクトを作成するときに使用するシステム管理者のログインです。 *login* のデータ型は **sysname** で、既定値は NULL です。 このパラメーターは必要ない場合は*security_mode*に設定されている**1**、つまり Windows 認証。  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンへのアップグレードの場合、このパラメーターは無視されます。  
  
 [  **@password=**] **'***パスワード***'**  
 ディストリビューション データベースに新しいシステム オブジェクトを作成するときに使用するシステム管理者のパスワードです。 *パスワード*は**sysname**、既定値は **'** (空の文字列)。 このパラメーターは必要ない場合は*security_mode*に設定されている**1**、つまり Windows 認証。  
  
> [!NOTE]  
>  SQL にアップグレードする場合、このパラメーターは無視されます[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]以降のバージョン。  
  
 [  **@ver_old=**] **'***old_version***'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 このストアド プロシージャは今後の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のリリースで削除される予定であり、非推奨とされます。  
  
 [  **@force_remove=**] **'***force_removal***'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@security_mode=**] **'***security_mode***'**  
 ディストリビューション データベースに新しいシステム オブジェクトを作成するときに使用するログイン セキュリティ モードです。 *security_mode*は**ビット**の既定値を持つ**0**します。 場合**0**、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証が使用されます。 場合**1**、Windows 認証が使用されます。  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンへのアップグレードの場合、このパラメーターは無視されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_vupgrade_replication**あらゆる種類のレプリケーションをアップグレードするときに使用されます。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_vupgrade_replication**します。  
  
## <a name="see-also"></a>参照  
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [レプリケートされたデータの検証](../../relational-databases/replication/validate-replicated-data.md)  
  
  
