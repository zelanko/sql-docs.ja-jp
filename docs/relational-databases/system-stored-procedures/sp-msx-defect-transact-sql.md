---
title: "sp_msx_defect (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_msx_defect
- sp_msx_defect_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_msx_defect
ms.assetid: 0dfd963a-3bc5-4b58-94f7-aec976da2883
caps.latest.revision: "24"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7a9d60318c9e737dd01d80d6ab00b089d98a1fb0
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="spmsxdefect-transact-sql"></a>sp_msx_defect (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マルチサーバー操作から現在のサーバーを削除します。  
  
> [!CAUTION]  
>  **sp_msx_defect**はレジストリを編集します。 レジストリは手動で編集しないでください。不適切または不正確な変更を加えると、システム構成に重大な問題が生じる場合があります。 熟練したユーザーのみがレジストリ エディターを使用してレジストリを編集することをお勧めします。 詳細については、Microsoft Windows のマニュアルを参照してください。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_msx_defect [@forced_defection =] forced_defection  
```  
  
## <a name="arguments"></a>引数  
 [  **@forced_defection =**] *forced_defection*  
 強制的に、マスター SQLServerAgent が、致命的に破損した完全に失われた場合に発生する参加解除するかどうかを示す**msdb**データベース、または いいえ**msdb**データベースのバックアップ。 *forced_defection*は**ビット**、既定値は**0**、強制的な参加解除が発生しないことを示します。 値**1**強制的に参加解除します。  
  
 実行することによって、参加解除の強制後**sp_msx_defect**のメンバー、 **sysadmin**マスター sqlserveragent の固定サーバー ロールは、参加解除を完了するには、次のコマンドを実行する必要があります。  
  
```  
EXECUTE msdb.dbo.sp_delete_targetserver @server_name = 'tsx-server', @post_defection =  0;  
```  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 ときに**sp_msx_defect**正常に完了すると、メッセージが返されます。  
  
## <a name="permissions"></a>Permissions  
 このストアド プロシージャを実行するには、 **sysadmin** 固定サーバー ロールのメンバーであることが必要です。  
  
## <a name="see-also"></a>参照  
 [sp_msx_enlist &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
