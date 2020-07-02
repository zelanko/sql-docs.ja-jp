---
title: sp_markpendingschemachange (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_markpendingschemachange
- sp_markpendingschemachange_TSQL
helpviewer_keywords:
- sp_markpendingschemachange
ms.assetid: 01100309-7bef-4154-85bf-f18489577e37
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 500547ba6fa2fb53675dfd6eb8e5a32ffb293e49
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85790370"
---
# <a name="sp_markpendingschemachange-transact-sql"></a>sp_markpendingschemachange (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  選択した保留中のスキーマ変更がレプリケートされないように、管理者がそのスキーマ変更をスキップできるようにします。これは、マージ パブリケーションをサポートするための操作です。 このストアドプロシージャは、パブリッシャー側でパブリケーションデータベースに対して実行されます。  
  
> [!CAUTION]  
>  このストアドプロシージャによって、スキーマの変更がレプリケートされない可能性があります。 再初期化などの他の方法が既に試行されているか、パフォーマンスの面でコストが高すぎる場合にのみ、問題を解決するために使用する必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_markpendingschemachange [@publication = ] 'publication'  
    [ , [ @schemaversion = ] schemaversion ]  
    [ , [ @status = ] 'status' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'`パブリケーションの名前を指定します。 *publication*は**sysname**,、既定値はありません。  
  
`[ @schemaversion = ] schemaversion`保留中のスキーマ変更を識別します。 *schemaversion*は**int**,、既定値は**0**です。 [Sp_enumeratependingschemachanges &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-enumeratependingschemachanges-transact-sql.md)を使用して、パブリケーションの保留中のスキーマ変更を一覧表示します。  
  
`[ @status = ] 'status'`保留中のスキーマ変更をスキップするかどうかを指定します。 *状態*は**nvarchar (10)** で、既定値は**アクティブ**です。 *Status*の値が**スキップ**された場合、選択したスキーマの変更はレプリケートされません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>Remarks  
 **sp_markpendingschemachange**は、マージレプリケーションで使用します。  
  
 **sp_markpendingschemachange**は、マージレプリケーションのサポートを目的としたストアドプロシージャであり、再初期化などの他の是正措置が状況を修正できなかった場合、またはパフォーマンスの面でコストが高すぎる場合にのみ使用してください。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_markpendingschemachange**を実行できるのは、固定サーバーロール**sysadmin**または固定データベースロール**db_owner**のメンバーだけです。  
  
## <a name="see-also"></a>関連項目  
 [sysmergeschemachange &#40;Transact-sql&#41;](../../relational-databases/system-tables/sysmergeschemachange-transact-sql.md)  
  
  
