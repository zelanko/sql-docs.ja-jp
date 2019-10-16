---
title: sp_copymergesnapshot (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_copymergesnapshot
- sp_copymergesnapshot_TSQL
helpviewer_keywords:
- sp_copymergesnapshot
ms.assetid: eaecd6e0-8486-4e5d-ace7-8ae75768c0a8
author: stevestein
ms.author: sstein
ms.openlocfilehash: d51f29399487ee156210e96fe598c38288755913
ms.sourcegitcommit: 4c75b49599018124f05f91c1df3271d473827e4d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72381709"
---
# <a name="sp_copymergesnapshot-transact-sql"></a>sp_copymergesnapshot (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  指定したパブリケーションのスナップショットフォルダーを **\@destinationfolder**に一覧表示されているフォルダーにコピーします。 このストアドプロシージャは、パブリッシャー側でパブリケーションデータベースに対して実行されます。  
  
 ![トピックリンクアイコン](../../database-engine/configure-windows/media/topic-link.gif "トピックリンクアイコン") [Transact-sql 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_copymergesnapshot [ @publication = ] 'publication', [ @destination_folder = ] 'destination_folder'  
```  
  
## <a name="arguments"></a>[引数]  
`[ @publication = ] 'publication'` には、スナップショットの内容をコピーするパブリケーションの名前を指定します。 *publication*は**sysname**,、既定値はありません。  
  
`[ @destination_folder = ] 'destination_folder'` は、パブリケーションスナップショットの内容をコピーするフォルダーの名前です。 *destination_folder*は**nvarchar (255)** ,、既定値はありません。 *Destination_folder*は、別のサーバー、ネットワークドライブ、またはリムーバブルメディア (cd-rom やリムーバブルディスクなど) 上の別の場所にすることができます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>備考  
 **sp_copymergesnapshot**は、マージレプリケーションで使用します。 @No__t-0 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョン7.0 以前を実行しているサブスクライバーは、代替スナップショットの場所を使用できません。  
  
## <a name="permissions"></a>Permissions  
 **Sp_copymergesnapshot**を実行できるのは、固定サーバーロール**sysadmin**または固定データベースロール**db_owner**のメンバーだけです。  
  
## <a name="see-also"></a>「  
 [スナップショット フォルダーの代替位置](../../relational-databases/replication/snapshot-options.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
