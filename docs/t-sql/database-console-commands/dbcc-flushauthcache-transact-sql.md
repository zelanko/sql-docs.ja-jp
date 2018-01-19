---
title: "DBCC FLUSHAUTHCACHE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC FLUSHAUTHCACHE
- FLUSHAUTHCACHE
- DBCC_FLUSHAUTHCACHE_TSQL
- FLUSHAUTHCACHE_TSQL
helpviewer_keywords: DBCC FLUSHAUTHCACHE
ms.assetid: 681ef31d-ceb9-4da5-86bf-bf1240df950f
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: da396237660d76c837a3dcadd84253d44ce28479
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="dbcc-flushauthcache-transact-sql"></a>DBCC FLUSHAUTHCACHE (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

ログインと現在のユーザー データベースでのファイアウォール規則に関する情報を含む、データベース認証キャッシュを空に[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。 Master データベースにログインし、ファイアウォール規則に関する情報の物理記憶域が含まれているために、このステートメントは、論理マスター データベースには適用されません。 ステートメントを実行するユーザー、現在接続している他のユーザーは、接続されたままです。 (DBCC FLUSHAUTHCACHE は現在サポートされていません[!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)])。
 
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
DBCC FLUSHAUTHCACHE [ ; ]  
```  
  
## <a name="arguments"></a>引数  
[なし] :
  
## <a name="remarks"></a>解説  
認証キャッシュは、ログインとは master に格納され、ユーザー データベースでメモリに配置するサーバーのファイアウォール ルールのコピーを作成します。  包含データベース ユーザーに関する情報が既に格納されるため、ユーザー データベースで、包含データベース ユーザーが、認証キャッシュの一部。
継続的にアクティブな接続[!INCLUDE[ssSDS](../../includes/sssds-md.md)]再認証が必要 (によって実行される、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]) 少なくとも 10 時間ごとです。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]試行の再認証が最初に送信されたパスワードとユーザーがいないを使用して入力が必要です。 パフォーマンス上の理由で、パスワードがリセットされると[!INCLUDE[ssSDS](../../includes/sssds-md.md)]、接続プールのため、接続がリセットされた場合でも、接続の再認証されません。 これは、内部設置型の動作と異なる[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 接続が最初に承認されているために、パスワードは変更されている場合、は、接続を終了する必要があり、新しいパスワードを使用して新しい接続が作成します。 KILL DATABASE CONNECTION 権限を持つユーザーがへの接続を明示的に終了[!INCLUDE[ssSDS](../../includes/sssds-md.md)]を使用して、 [KILL &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/kill-transact-sql.md)コマンド。
  
## <a name="permissions"></a>権限  
必要があります、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]管理者アカウントです。
  
## <a name="example"></a>例  
次のステートメントでは、現在のデータベースの認証キャッシュをクリアします。
  
```sql
DBCC FLUSHAUTHCACHE;  
```  
  
## <a name="see-also"></a>参照  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
  
